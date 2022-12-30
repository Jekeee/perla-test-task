<template>
    <div class="delivery-information">
        <div class="delivery-information-item">
            <img src="../static/free-delivery-logo.png" alt="free-delivery-logo">
            <p>Безкоштовна доставка від 1800 грн</p>
        </div>
        <div class="delivery-information-item">
            <img src="../static/delivery-time-logo.png" alt="delivery-time-logo">
            <p>Відправки в день оформлення замовлення до 16:00</p>
        </div>
        <div class="delivery-information-item">
            <img src="../static/delivery-return-logo.png" alt="delivery-return-logo">
            <p>Гарантія повернення грошових коштів</p>
        </div>
    </div>
</template>

<style>
.delivery-information {
    margin-top: 100px !important;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    width: 100%;
    align-items: center;
    padding: 20px 56px;
    background: linear-gradient(270deg, rgba(255, 255, 255, 0.81) 0%, rgba(255, 255, 255, 0.54) 100%);
    border-radius: 15px;
}

.delivery-information-item {
    display: flex;
    flex-direction: row;
    align-items: center;
    width: 280px;

}

.delivery-information img {
    max-width: 56px;
    margin-right: 26px;
}

@media (max-width: 1920px) {
        .delivery-information {
        font-weight: 400;
        font-size: 18px;
        line-height: 24px;
        margin-top: 55px !important;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        width: 100%;
        align-items: flex-center;
        padding: 20px 56px;
        background: linear-gradient(270deg, rgba(255, 255, 255, 0.81) 0%, rgba(255, 255, 255, 0.54) 100%);
        border-radius: 15px;
    }

    .delivery-information-item {
        display: flex;
        flex-direction:column;
        align-items: center;
        text-align: center;
        width: 156px;
        height: 208px;
        padding:  20px 60px;

    }

    .delivery-information img {
        margin-bottom: 27px;
        max-width: 56px;
        margin-right: 26px;
    }
 }

 @media (max-width: 768px) {
        .delivery-information {
        font-weight: 400;
        font-size: 16px;
        line-height: 21px;
        margin-top: 55px !important;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        width: 100%;
        align-items: flex-start;
        padding: 0;
        background: linear-gradient(270deg, rgba(255, 255, 255, 0.81) 0%, rgba(255, 255, 255, 0.54) 100%);
        border-radius: 15px;
    }

    .delivery-information-item {
        display: flex;
        flex-direction:row;
        align-items: center;
        text-align: center;
        width: 346px;
        height: auto;
        padding:  39px 33px !important;

    }

    .delivery-information img {
        margin-bottom: 27px;
        max-width: 54px;
        margin-right: 33px;
    }
 }
 

</style>