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
                                <tbody v-for="ingridient of product.ingridients" v-bind:key=ingridient>
                                    <tr>
                                        <th>{{ ingridient.title }}</th>
                                        <td>{{ ingridient.discription }}</td>
                                    </tr>
                                </tbody>
                            </table>
                        </div>
                        <div class="tab-pane fade" id="nav-application" role="tabpanel"
                            aria-labelledby="nav-application-tab" tabindex="0" >
                            <p v-html="product.applications.discription"></p>
                            <p><strong>Курс прийому:</strong> {{ product.applications.course }}</p>
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
                        <button class="show-basket all" @click='addToBasket'>До кошика</button>
                        <button class="show-basket mobile" @click='addToBasket'>До кошика - 489 ₴</button>
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
.show-basket.mobile{
    display: none;
}
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
    justify-content: space-between;
    align-items: flex-start;
    width: 1306px !important;

}

.about-product {
    display: flex;
    flex-direction: column;
    width: 635px !important;
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

@media (max-width: 1320px){
.product {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-top: 64px !important;
    font-family: 'Onest', Arial, Helvetica, sans-serif;
}

.product-item {
    display: flex;
    flex-direction: column-reverse;
    justify-content: center;
    align-items: center;
    width: 768px !important;

}

.about-product {
    display: flex;
    flex-direction: column;
    width: 100%;
    padding-top: 0;
    margin-top: 40px;
    width: 768px !important;
}

.product-title {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-start;
    width: 768px !important;

}

.product-name {
    font-weight: 500;
    font-size: 40px;
    line-height: 48px;
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
    background: #FFFFFF;
    border-radius: 50px;
    padding: 5px 24px;
    margin-left: 24px;
    text-align: center;
}

.product-tabs-menu {
    margin-top: 30px !important;
}

.product-tab {
    font-weight: 400;
    font-size: 18px;
    line-height: 26px;
    margin-top: 12px !important;
}

.nav.nav-tabs {
    font-weight: 700;
    font-size: 17px;
    line-height: 22px;
    color: #00284F;
    text-transform: uppercase;
    margin: 0;
    width: 768px !important;
}

.nav.nav-tabs:last-child {
    margin-right: 0px;
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
    margin-top: 44px !important;
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
    margin-right: 18px;
    letter-spacing: -0.03em;
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
    line-height: 48px;
    color: #00284F;
}

.product-actions {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    margin-top: 35px !important;
    padding-left: 15px;
}

.product-actions input {
    margin: 0 25px;
    font-weight: 400;
    font-size: 28px;
    line-height: 36px;
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
    font-size: 22px;

}

.show-basket {
    width: 395px;
    text-align: center;
    background: #69C522;
    border-radius: 40px;
    padding: 17px 0;
    color: #FFF;
    font-weight: 500;
    font-size: 18px;
    line-height: 23px;
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
    line-height: 26px;
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
}

@media (max-width: 768px){
.show-basket.mobile{
    display: block;
}

.show-basket.all{
    display: none;
}
.product {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-top: 35px !important;
    font-family: 'Onest', Arial, Helvetica, sans-serif;
}

.product-item {
    display: flex;
    flex-direction: column-reverse;
    justify-content: center;
    align-items: center;
    width: 384px !important;

}

.about-product {
    display: flex;
    flex-direction: column;
    width: 100%;
    padding-top: 0;
    margin-top: 24px;
    width: 384px !important;
}

.product-title {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    width: 384px !important;

}

.product-name {
    font-weight: 700;
    font-size: 25px;
    line-height: 32px;
    text-align: center;
}

.product-name-em {
    font-family: "Calliga";
    font-weight: 500;
}

.product-name2 {
    font-weight: 500;
    font-size: 16px;
    line-height: 20px;
    background: #FFFFFF;
    border-radius: 50px;
    padding: 2px 20px;
    margin-left: 0px;
    text-align: center;
}

.product-tabs-menu {
    margin-top: 30px !important;
    
}

.product-tab {
    font-weight: 700;
    font-size: 11px;
    line-height: 14px;
    margin-top: 26px !important;
}


.nav.nav-tabs {
    font-weight: 700;
    font-size: 11px;
    line-height: 14px;
    color: #00284F;
    text-transform: uppercase;
    margin: 0;
    width: 384px !important;
    display: flex;
    align-items: center;
    flex-wrap: nowrap;
    white-space: nowrap;
}

.nav.nav-tabs:last-child {
    margin-right: 0px;
}

.product-information{
    display: flex;
    flex-direction: column-reverse;
    align-items: center;
    font-weight: 500;
    font-size: 16px;
    line-height: 18px;
}


.product-information-package {
    display: flex;
    flex-direction: row;
    align-items: center;
}

.product-information-package img {
    height: 35px;
}

.product-package {
    display: flex;
    flex-direction: column;
    margin-left: 30px;

}

.product-information-discriptions-price {
    display: flex;
    flex-direction: row;
    margin-top: 24px !important;
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
    display: none;
    position: relative;
    font-weight: 900;
    font-size: 28px;
    line-height: 36px;
    text-align: center;
    color: rgba(0, 40, 79, 0.3);
    margin-right: 18px;
    letter-spacing: -0.03em;
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
    display: none;
    font-weight: 700;
    font-size: 40px;
    line-height: 48px;
    color: #00284F;
}

.product-actions {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    margin-top: 35px !important;
    padding-left: 15px;
}

.product-actions input {
    margin: 0 25px;
    font-weight: 400;
    font-size: 28px;
    line-height: 36px;
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
    display: none;
    flex-direction: row;
    align-items: center;
}

.product-actions-quantity-minus,
.product-actions-quantity-plus {
    color: rgba(0, 40, 79, 0.4);
    font-size: 22px;

}

.show-basket {
    width: 384px;
    text-align: center;
    background: #69C522;
    border-radius: 40px;
    padding: 17px 0;
    color: #FFF;
    font-weight: 500;
    font-size: 18px;
    line-height: 23px;
}

.nav-link {
    color: #00284F;
    opacity: 40%;
    cursor: pointer;
    border: none !important;
    padding: 4px 8px;

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



.tab-pane {
    margin-top: 15px !important;
    font-family: 'Onest', Arial, Helvetica, sans-serif !important;
    font-weight: 400;
    font-size: 16px;
    line-height: 21px;
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
}
</style>