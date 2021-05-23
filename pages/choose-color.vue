<template>
    <div class="container choose-color">
        <div class="row photo">
            <div class="col-12">
                <a href="#" @click="step = 1" class="btn btn-back">
                    <img src="images/back.png" alt="back" />
                </a>
            </div>
        </div>
        <div class="row">
            <div class="col-4">
                <img src="images/filtr.png" alt="" /> Фильтр
            </div>
            <div class="col-4">{{ activeGroup }}</div>
            <div class="col-4 d-flex justify-content-end">Скрыть</div>
        </div>
        <div class="row">
            <div class="col-12">
                <div class="template"><img src="images/none.png" alt="" /></div>
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        data() {
            return {};
        },
    };
</script>
<style>
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
        width: 90% !important;
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