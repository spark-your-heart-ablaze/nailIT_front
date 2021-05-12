<template>
    <div class="container">
        <div class="row photo">
            <div class="col-12">
                <nuxt-link to="salone-code" class="btn btn-back">
                    <img src="images/back.png" alt="back" />
                </nuxt-link>
            </div>
        </div>
        <div class="row row-step">
            <div class="col-12">
                <div class="step">02</div>
            </div>
            <div class="col-6">
                <div class="line-step red"></div>
            </div>
            <div class="col-6">
                <div class="line-step gray"></div>
            </div>
        </div>
        <div class="row">
            <div class="col-12">
                <h1>Загрузка фотографии</h1>
                <p>
                    Пришли фотографию своей руки, чтобы начать примерку, как на
                    фотографии выше
                </p>
            </div>
        </div>
        <div class="row">
            <div class="col-12 d-flex justify-content-center">
                <nuxt-link to="your-telephone" class="btn btn-send">
                    Камера
                </nuxt-link>
                <input
                    type="file"
                    class="btn btn-send"
                    accept="image/*;capture=camera"
                />
            </div>
        </div>
    </div>
</template>
<style>
    @import url("https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,100;0,300;0,400;0,700;0,900;1,100;1,300;1,400;1,700;1,900&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=DM+Sans:ital,wght@0,400;0,500;0,700;1,400;1,500;1,700&display=swap");
    .btn-back {
        display: flex;
        align-items: center;
        justify-content: center;
        margin-top: 50px;
        width: 35px;
        height: 35px;
        border-radius: 50px;
        background: #f8f3f3;
        box-shadow: -7px -7px 12px rgba(255, 255, 255, 0.0155704),
            -13px -7px 15px rgba(246, 251, 255, 0.741505),
            -8px 5px 12px rgba(244, 248, 251, 0.345662),
            2px 9px 30px rgba(201, 170, 170, 0.795345);
    }
    .photo {
        background-image: url("/images/hand.jpg");
        background-size: cover;
        height: 460px;
    }
    .row-step {
        background: #f8f3f3;
        border-radius: 24px 24px 0px 0px;
    }
    .step {
        font-family: Lato;
        font-style: normal;
        font-weight: 500;
        font-size: 16px;
        line-height: 26px;

        color: #653333;

        mix-blend-mode: normal;
        opacity: 0.3;
        margin-top: 15px;
    }
    .line-step {
        margin-top: 10px;
        width: 100%;
        height: 3px;
    }
    .red {
        background: linear-gradient(
            295.74deg,
            rgba(205, 138, 154, 0.8) -52.26%,
            rgba(254, 170, 160, 0.8) 118.91%
        );
        box-shadow: 12px 6px 40px rgba(255, 105, 169, 0.182009);
    }
    .gray {
        background: rgba(110, 129, 160, 0.235905);
        border-radius: 100px;
    }
    h1 {
        font-family: Lato;
        font-weight: bold;
        font-size: 28px;
        line-height: 32px;
        text-align: center;
        color: #334669;
        margin-top: 26px;
    }
    p {
        font-family: Lato;
        font-size: 16px;
        line-height: 24px;
        text-align: center;
        color: #334669;
        opacity: 0.6;
        margin-top: 15px;
    }
    .btn-send {
        width: 0%;
        max-width: 350px;
        margin-top: 50px;
        margin-bottom: 50px;
        font-family: Lato;
        font-size: 21px;
        line-height: 25px;
        color: #ffffff;
        filter: drop-shadow(0px 4px 4px rgba(0, 0, 0, 0.25));
        background: linear-gradient(
                238.59deg,
                #5fd3ff -18.96%,
                rgba(99, 214, 255, 0) 54.42%
            ),
            linear-gradient(96.53deg, #ffae88 -3.19%, #8f93ea 105.27%);
        border-radius: 20px;
        padding: 19px 35px;
    }
    .btn:hover {
        color: #fff;
    }
</style>