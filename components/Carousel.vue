<template>
    <div class="galery-product-slider">
        <div id="carouselExampleControls" class="carousel slide">
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
            <div class="carousel-control btn-less-1920">
                <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleControls"
                    data-bs-slide="prev">
                    <img src="../static/arrow-left-icon.png" alt="arrow-left-icon">
                </button>
                <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleControls"
                    data-bs-slide="next">
                    <img src="../static/arrow-right-icon.png" alt="arrow-right-icon">
                </button>
            </div>
            <div class="carousel-control btn-more-1920">
                <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleControls"
                    data-bs-slide="prev">
                    <img src="../static/desktop-arrow-left-icon.png" alt="desktop-arrow-left-icon">
                </button>
                <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleControls"
                    data-bs-slide="next">
                    <img src="../static/desktop-arrow-right-icon.png" alt="desktop-arrow-right-icon">
                </button>
            </div>
        </div>
    </div>
</template>

<style>
.btn-less-1920 {
    display: none;
}

.galery-product-slider {
    width: 550px !important;
}

.carousel-inner {
    position: relative;
    width: 100%;
    height: 450px !important;
    max-width: 550px !important;
    overflow: hidden;
}

.carousel-control-prev,
.carousel-control-next {
    max-width: 22px !important;
    opacity: 0.5 !important;

}

.carousel-control-prev {
    right: 0 !important;
}

.carousel-control-prev {
    left: 450px;
}

@media (min-width: 1350px) {
    .carousel-control {
        position: relative !important;
    }
}


@media (max-width: 1320px) {
    .btn-less-1920 {
        display: block;
    }

    .btn-more-1920 {
        display: none;
    }

    .galery-product-slider {
        width: 768px !important;
        height: 310px;
        display: flex;
        justify-content: center;

    }

    .carousel-inner {
        position: relative;
        width: 100%;
        height: auto;
        max-width: 400px !important;
        overflow: hidden;
    }

    .carousel-control-prev,
    .carousel-control-next {
        max-width: 22px !important;
        opacity: 0.5 !important;
        margin-left: -170px;
        margin-right: -170px;

    }



    .carousel-control-prev {
        right: 123px !important;
    }

    .carousel-control-prev {
        left: 0;
    }
}

@media (max-width: 768px) {
    .btn-less-1920 {
        display: block;
    }

    .btn-more-1920 {
        display: none;
    }

    .galery-product-slider {
        max-width: 384px !important;
        display: flex;
        justify-content: center;
        align-items: center;

    }

    .carousel-inner {
        position: relative;
        width: 100%;
        height: auto !important;
        max-width: 285px !important;
        overflow: hidden;
    }

    .carousel-control-prev,
    .carousel-control-next {
        max-width: 17px !important;
        opacity: 0.5 !important;
        margin-left: -45px;
        margin-right: -45px;
        height: 30px;
        margin-top: 30%;

    }

    .carousel-control-prev {
        left: 0;
    }
}
</style>