<template>
    <div class="product container">
        <div class="product-item">
            <div class="about-product">
                <div class="product-title">
                    <h1 class="product-name">{{ product.title }} <em class="product-name-em">{{ product.title2 }}</em>
                    </h1>
                    <h2 class="product-name2"> {{ product.title3 }} </h2>
                </div>
                <div class="product-tabs-menu">
                    <nav>
                        <div class="nav nav-tabs" id="nav-tab" role="tablist">
                            <a class="nav-link active" id="nav-description-tab" data-bs-toggle="tab"
                                data-bs-target="#nav-description" type="button" role="tab"
                                aria-controls="nav-description" aria-selected="true">ОПИС</a>
                            <a class="nav-link" id="nav-benefit-tab" data-bs-toggle="tab" data-bs-target="#nav-benefit"
                                type="button" role="tab" aria-controls="nav-benefit" aria-selected="false">КОРИСТЬ</a>
                            <a class="nav-link" id="nav-ingredients-tab" data-bs-toggle="tab"
                                data-bs-target="#nav-ingredients" type="button" role="tab"
                                aria-controls="nav-ingredients" aria-selected="false">ІНГРЕДІЄНТИ</a>
                            <a class="nav-link" id="nav-application-tab" data-bs-toggle="tab"
                                data-bs-target="#nav-application" type="button" role="tab"
                                aria-controls="nav-application" aria-selected="false">СПОСІБ ЗАСТОСУВАННЯ</a>
                        </div>
                    </nav>
                    <div class="tab-content" id="nav-tabContent">
                        <div class="tab-pane fade show active" id="nav-description" role="tabpanel"
                            aria-labelledby="nav-description-tab" tabindex="0">
                            <p> {{ product.description }}</p>
                        </div>
                        <div class="tab-pane fade" id="nav-benefit" role="tabpanel" aria-labelledby="nav-benefit-tab"
                            tabindex="0">
                            <ul>
                                <li v-for="benefit of product.benefits" v-bind:key=benefit> {{ benefit }} </li>
                            </ul>
                        </div>
                        <div class="tab-pane fade" id="nav-ingredients" role="tabpanel"
                            aria-labelledby="nav-ingredients-tab" tabindex="0">
                            <table>
                                <tbody>
                                    <tr>
                                        <th>{{ product.ingridients.ingridientsTitle1 }}</th>
                                        <td>{{ product.ingridients.ingridientsDescription1 }}</td>
                                    </tr>
                                    <tr>
                                        <th>{{ product.ingridients.ingridientsTitle2 }}</th>
                                        <td>{{ product.ingridients.ingridientsDescription2 }}</td>
                                    </tr>
                                    <tr>
                                        <th>{{ product.ingridients.ingridientsTitle3 }}</th>
                                        <td>{{ product.ingridients.ingridientsDescription3 }}</td>
                                    </tr>
                                    <tr>
                                        <th>{{ product.ingridients.ingridientsTitle4 }}</th>
                                        <td>{{ product.ingridients.ingridientsDescription4 }}</td>
                                    </tr>
                                </tbody>
                            </table>
                        </div>
                        <div class="tab-pane fade" id="nav-application" role="tabpanel"
                            aria-labelledby="nav-application-tab" tabindex="0">
                            <p>{{ product.application.p1part1 }}<strong>{{ product.application.strong }}</strong>,
                                {{ product.application.p1part2 }}</p>
                            <p><strong>{{ product.application.course }}</strong> {{ product.application.p2part1 }}</p>
                        </div>
                    </div>
                </div>
                <div class="product-information">
                    <div class="product-information-discriptions-price">
                        <div class="product-information-package">
                            <img src="../static/package-icon.png" alt="package-icon">
                            <div class="product-package">
                                <strong>В упаковці:</strong>
                                <span>{{ product.pack.quanity }}</span>
                                <span class="reception-time">{{ product.pack.timeUse }}</span>
                            </div>
                        </div>
                        <div class="product-information-price">
                            <div class="old-price">
                                <strong>{{ quanity * 963 }} ₴</strong>
                            </div>
                            <div class="price">
                                <strong>{{ quanity * 489 }} ₴</strong>
                            </div>
                        </div>
                    </div>
                    <div class="product-actions">
                        <div class="product-actions-quantity">
                            <div class="product-actions-quantity-minus" @click="quanityDec">-</div>
                            <input type="number" class="product-actions-quantity-actual" v-bind:value=quanity
                                @change="changeQuanity">
                            <div class="product-actions-quantity-plus" @click="quanityInc">+</div>
                        </div>
                        <button class="show-basket" @click='addToBasket'>До кошика</button>
                    </div>
                </div>
            </div>
            <Carousel />
        </div>
        <Delivery-info />
    </div>
</template>

<script setup>
import { ref } from "vue";
import { product } from "../data/Product";
let quanity = ref(1);
const oldBasketList = defineProps(['basketList']);
const newBasketList = oldBasketList.basketList;
let basketList = [product];

const quanityDec = () => {
    if (quanity.value !== 1) {
        quanity.value = quanity.value - 1;
        if (basketList.length > 1) {
            basketList.shift();
        }
    }
}

const quanityInc = () => {
    quanity.value = quanity.value + 1;
    basketList.push(product);
}

const changeQuanity = (event) => {
    if (event.target.value == "" || event.target.value == 0) {
        event.target.value = quanity.value = 1
        basketList = [product];
    } else {
        quanity.value = parseInt(event.target.value);
        basketList = [];
        for (let i = 0; i < quanity.value; i++) {
            basketList.push(product);
        }
    }
}

const addToBasket = () => {
    for (let i = 0; i < basketList.length; i++) {
        newBasketList.push(basketList[i]);
    }
    basketList = [product];
    quanity.value = 1;
}
</script>

<style>
.product-tab {
    display: none;
    font-weight: 400;
    font-size: 18px;
    line-height: 28px;
}

.active {
    display: block;
}

.product {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-top: 110px !important;
    font-family: 'Onest', Arial, Helvetica, sans-serif;
}

.product-item {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: flex-start;

}

.about-product {
    display: flex;
    flex-direction: column;
    width: 635px;
    padding-top: 10px;
}

.product-title {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;

}

.product-name {
    font-weight: 700;
    font-size: 40px;
    line-height: 51px;
    max-width: 306px;
    text-align: center;
}

.product-name-em {
    font-family: "Calliga";
    font-weight: 500;
}

.product-name2 {
    font-weight: 500;
    font-size: 22px;
    line-height: 22px;
    width: 306px;
    background: #FFFFFF;
    border-radius: 50px;
    padding: 10px 12px;
    margin-left: 25px;
    text-align: center;
}

.product-tabs-menu {
    margin-top: 22px !important;
}

.nav.nav-tabs {
    font-weight: 700;
    font-size: 17px;
    line-height: 22px;
    color: #00284F;
    text-transform: uppercase;
    margin-right: 40px;
}

.nav.nav-tabs:last-child {
    margin-right: 0px;
}

.product-tab {
    font-weight: 400;
    font-size: 18px;
    line-height: 28px;
    margin-top: 20px !important;
}

.product-information-package {
    display: flex;
    flex-direction: row;
    align-items: center;
}

.product-information-package img {
    height: 40px;
}

.product-package {
    display: flex;
    flex-direction: column;
    margin-left: 30px;

}

.product-information-discriptions-price {
    display: flex;
    flex-direction: row;
    margin-top: 55px !important;
    justify-content: space-between;
}

.reception-time {
    color: rgba(0, 40, 79, 0.3);
    ;
}

.product-information-price {
    display: flex;
    flex-direction: row;
    align-items: center;
}

.old-price {
    position: relative;
    font-weight: 900;
    font-size: 28px;
    line-height: 36px;
    text-align: center;
    color: rgba(0, 40, 79, 0.3);
    margin-right: 25px;
}

.old-price::before {
    border-bottom: 2px solid #00284F;
    position: absolute;
    content: "";
    width: 100%;
    height: 50%;
    transform: rotate(7deg);
}

.price {
    font-weight: 700;
    font-size: 40px;
    line-height: 51px;
    color: #00284F;
}

.product-actions {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    margin-top: 75px !important;
    padding-left: 15px;
}

.product-actions input {
    margin: 0 20px;
    font-weight: 400;
    font-size: 28px;
    line-height: 35px;
    text-align: center;
    color: #00284F;
    width: 45px;
    border: none;
    border-radius: 7px;
    height: 45px;
}

/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
}

.product-actions-quantity {
    display: flex;
    flex-direction: row;
    align-items: center;
}

.product-actions-quantity-minus,
.product-actions-quantity-plus {
    color: rgba(0, 40, 79, 0.4);
    font-size: 25px;

}

.show-basket {
    width: 416px;
    text-align: center;
    background: #69C522;
    border-radius: 40px;
    padding: 15px;
    color: #FFF;
    font-weight: 500;
    font-size: 18px;
    line-height: 27px;
}

.nav-link {
    color: #00284F;
    opacity: 40%;
    cursor: pointer;
    border: none !important;

}

.nav-link:hover {
    text-decoration: none;
    color: #00284F;
}

.nav-link.active {
    border-bottom: 2px solid #00284F !important;
    background: none !important;
    opacity: 100%;
}

#nav-tab {
    display: inline-flex !important;
    border-bottom: 1px solid #00284F !important;
}

.tab-pane {
    margin-top: 15px !important;
    font-family: 'Onest', Arial, Helvetica, sans-serif !important;
    font-weight: 400;
    font-size: 18px;
    line-height: 28px;
    width: 100%;
}

.tab-pane li {
    display: list-item !important;
    list-style: inside;
}

.tab-pane table {
    width: 100%;
}

.tab-pane tr {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    border-bottom: 1px solid #00284F;
}

.tab-pane td {
    width: 50%;
}

.nav.nav-tabs {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    width: 100%;
}

.product-actions-quantity-minus,
.product-actions-quantity-plus {
    cursor: pointer;
}
</style>