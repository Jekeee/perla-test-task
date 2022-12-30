<template>
    <div class="free-delivery">
            <p>
                <img src="../static/free-delivery-icon.png" alt="free-delivery-icon">
                Безкоштовна досавка від 1800 грн
                <img src="../static/free-delivery-icon.png" alt="free-delivery-icon">
            </p>
        </div>
</template>

<style>
    .free-delivery {
    display: flex;
    justify-content: center;
    align-items: center;
    background: #99AFFF;
    padding: 10px 0;
    color: #fff;
}

.free-delivery p {
    display: flex;
    align-items: center;
    font-family: 'Onest';
    font-style: normal;
    font-weight: 500;
    font-size: 20px;
    line-height: 24px;
    margin: 0;
}

.free-delivery img {
    max-width: 20px;
    margin-left: 13px;
    margin-right: 13px;

}

@media (max-width: 1920px) {
    
    .free-delivery {
    display: flex;
    justify-content: center;
    align-items: center;
    background: #99AFFF;
    padding: 5px 0;
    color: #fff;
    }

    .free-delivery p {
        display: flex;
        align-items: center;
        font-family: 'Onest';
        font-style: normal;
        font-weight: 500;
        font-size: 14px;
        line-height: 20px;
        margin: 0;
    }

    .free-delivery img {
        max-width: 16px;
        margin-left: 12px;
        margin-right: 12px;

    }
}
</style>