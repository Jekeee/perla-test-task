<template>
    <div class="galery-product-slider">
        <div id="carouselExampleControls" class="carousel slide carousel-slider">
            <div class="carousel-inner">
                <div class="carousel-item active">
                    <img src="../static/product-img-1.png" class="d-block w-100" alt="product-img-1">
                </div>
                <div class="carousel-item">
                    <img src="../static/product-img-2.png" class="d-block w-100" alt="product-img-2">
                </div>
                <div class="carousel-item">
                    <img src="../static/product-img-3.png" class="d-block w-100" alt="product-img-3">
                </div>
                <div class="carousel-item">
                    <img src="../static/product-img-4.png" class="d-block w-100" alt="product-img-4">
                </div>
                <div class="carousel-item">
                    <img src="../static/product-img-5.png" class="d-block w-100" alt="product-img-5">
                </div>
            </div>
        </div>
        <div class="carousel-btn">
            <button type="button" data-bs-target="#carouselExampleControls" data-bs-slide="prev" id="prev">
                <img src="../static/arrow-left-icon.png" alt="arrow-left-icon">
            </button>
            <button type="button" data-bs-target="#carouselExampleControls" data-bs-slide="next" id="next">
                <img src="../static/arrow-right-icon.png" alt="arrow-right-icon">
            </button>
        </div>
    </div>
</template>

<style>
.galery-product-slider {
    display: flex;
    flex-direction: column;
    max-width: 550px;
    height: 475px;
    justify-content: space-between;
}


.slider-buttons {
    display: flex;
    flex-direction: row;
}

.slider-item img {
    max-width: 100%;
}

.carousel-slider {
    display: flex;
    flex-direction: column;
}

.carousel-btn {
    display: flex;
    flex-direction: row;
    justify-content: flex-end;

}

.carousel-btn button {
    margin-left: 42px;
}

.carousel-btn img {
    max-width: 22px;
}
</style>