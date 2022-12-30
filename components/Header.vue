<template>
    <div>
        <Free-delivery-block />
    <div class="header container">
        <div class="header-content container">
            <div class="header-content-left">
                <button><img src="../static/burger-desk-icon.png" alt="burger-desk-icon"></button>
                <a href="/"><img src="../static/search-icon.png" alt="search-icon"></a>
            </div>
            <div class="header-content-logo">
                <a href="/"><img src="../static/perla-helsa-logo.png" alt="perla-helsa-logo"></a>
            </div>
            <div class="header-content-right">
                <a href="/"><img src="../static/phone-icon.png" alt="phone-icon"></a>
                <div class="basket">
                    <a href="/"><img src="../static/basket-icon.png" alt="basket-icon">
                        <span class="cart-contity" v-if="basketList.length">{{ basketList.length }}</span></a>
                </div>
            </div>
        </div>
        <div class="header-menu container">
            <ul>
                <li><a href="/">Омега-3</a></li>
                <li><a href="/">Вітаміни</a></li>
                <li><a href="/">Добавки</a></li>
                <li><a href="/">Доставка</a></li>
                <li><a href="/">Про нас</a></li>
            </ul>
        </div>
    </div>
    </div>
    
</template>

<script setup>
defineProps(['basketList'])
</script>


<style>


.header-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 35px !important;
}

.header-content-left {
    display: flex;
    justify-content: center;
    align-items: flex-start;
}

.header-content-right {
    display: flex;
    justify-content: center;
    align-items: flex-start;
}

.header-content button {
    margin-right: 45px;
}

.header-content a {
    cursor: pointer;
    margin-right: 45px;
}

.header-content a:last-child {
    margin-right: 0;
}

.header-content img {
    max-width: 24px;
}

.header-content-logo img {
    max-width: 196px;
}

.header-menu {
    display: flex;
    justify-content: center;
    font-family: 'Onest', Arial, Helvetica, sans-serif;
    font-weight: 400;
    font-size: 23px;
    line-height: 29px;
    margin-top: 45px !important;
}

.header-menu ul {
    display: flex;
    justify-content: space-around;
    margin: 0;
    padding: 0;
}

.header-menu li {
    margin-right: 40px;
}

.header-menu li:last-child {
    margin-right: 0px;
}

.header-menu ul li a {
    text-decoration: none;
    color: #1D1D1B;
}

.basket {
    position: relative;
}

.cart-contity {
    display: flex;
    align-items: center;
    justify-content: center;
    position: absolute;
    background: #F5F352;
    color: #1D1D1B;
    width: 26px;
    height: 26px;
    font-weight: 500;
    font-size: 14px;
    line-height: 14px;
    top: -15px;
    right: -17px;
    padding: 0;
    border-radius: 50%;

}

@media (max-width: 1920px) {

    .header-content {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-top: 30px !important;
    }

    .header-content-left {
        display: flex;
        justify-content: center;
        align-items: flex-start;
    }

    .header-content-right {
        display: flex;
        justify-content: center;
        align-items: flex-start;
    }

    .header-content button {
        margin-right: 33px;
    }

    .header-content a {
        cursor: pointer;
        margin-right: 33px;
    }

    .header-content a:last-child {
        margin-right: 0;
    }

    .header-content img {
        max-width: 23px;
    }

    .header-content-logo img {
        max-width: 150px;
    }

    .header-menu {
        display: flex;
        justify-content: space-between;
        margin-right: 0;
        margin-left: 0;
        font-family: 'Onest', Arial, Helvetica, sans-serif;
        font-weight: 400;
        font-size: 23px;
        line-height: 29px;
        margin-top: 45px !important;
        color: #000;
    }

    .header-menu ul {
        display: flex;
        justify-content: space-between;
        margin: 0;
        padding: 0;
        width: 768px !important ;
    }

    .header-menu li {
        margin-right: 55px;
    }

    .header-menu li:last-child {
        margin-right: 0px;
    }

    .header-menu ul li a {
        text-decoration: none;
        color: #000;
    }

    .basket {
        position: relative;
    }

    .cart-contity {
        display: flex;
        align-items: center;
        justify-content: center;
        position: absolute;
        background: #F5F352;
        color: #1D1D1B;
        width: 26px;
        height: 26px;
        font-weight: 500;
        font-size: 14px;
        line-height: 14px;
        top: -15px;
        right: -17px;
        padding: 0;
        border-radius: 50%;

    }
}
</style>