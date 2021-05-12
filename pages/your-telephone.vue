<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <nuxt-link to="load-photo" class="btn btn-back">
                    <img src="images/back.png" alt="back" />
                </nuxt-link>
            </div>
            <div class="col-12">
                <div class="step">03</div>
            </div>
            <div class="col-9">
                <div class="line-step red"></div>
            </div>
            <div class="col-3">
                <div class="line-step gray"></div>
            </div>
        </div>
        <div class="row">
            <div class="col-12">
                <h1>Номер телефона</h1>
                <p>Введи номер телефона для авторизации</p>
            </div>
        </div>
        <div class="row">
            <div class="col-12">
                <div class="input">
                    <input
                        class="tel"
                        type="text"
                        placeholder="+7 966 999 88 77"
                    />
                </div>
            </div>
        </div>
        <div class="row">
            <div class="col-12 d-flex justify-content-center">
                <nuxt-link to="load-photo" class="btn btn-send">
                    Авторизация
                </nuxt-link>
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
    input.tel {
        text-align: center;
        width: 100%;
        background: #f8f3f3;
        border: 1.5px solid rgba(184, 167, 171, 0.51);
        box-shadow: 2px 9px 30px rgba(201, 170, 170, 0.795345);
        border-radius: 20px;
        font-family: Lato;
        font-weight: bold;
        font-size: 16px;
        line-height: 24px;
        color: #334669;
        padding: 16px;
        max-width: 350px;
    }
    input::placeholder {
        opacity: 0.6;
    }
    input:focus {
        outline: none;
    }
    input[type="text"]:last-child {
        margin-right: 0;
    }
    .btn-send {
        width: 90%;
        max-width: 350px;
        margin-top: 97px;
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