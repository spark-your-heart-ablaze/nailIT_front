<template>
    <div class="nail-it">
        <div class="container salone-code" v-if="step == 1">
            <div class="row">
                <div class="col-12">
                    <nuxt-link to="/" class="btn btn-back">
                        <img src="images/back.png" alt="back" />
                    </nuxt-link>
                </div>
                <div class="col-12">
                    <div class="step">01</div>
                </div>
                <div class="col-3">
                    <div class="line-step red"></div>
                </div>
                <div class="col-9">
                    <div class="line-step gray"></div>
                </div>
            </div>
            <div class="row">
                <div class="col-12">
                    <h1>Введите код салона</h1>
                    <p>
                        Посмотрите на столе у мастера или спросите у
                        администратора
                    </p>
                </div>
            </div>
            <div class="row">
                <div class="col-12 p-0">
                    <div class="input-v">
                        <the-mask
                            :mask="[' # # # #']"
                            class="code-v"
                            v-model="num"
                            @input="check"
                        />
                    </div>
                </div>
            </div>
            <div class="row">
                <div class="col-12 d-flex justify-content-center">
                    <a href="#" class="btn btn-send" @click="sendCode">
                        Отправить
                    </a>
                </div>
            </div>
        </div>
        <div class="container load-photo" v-if="step == 2">
            <div class="row photo">
                <div class="col-12">
                    <a href="#" @click="step = 1" class="btn btn-back">
                        <img src="images/back.png" alt="back" />
                    </a>
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
                        Пришли фотографию своей руки, чтобы начать примерку, как
                        на фотографии выше
                    </p>
                </div>
            </div>
            <div class="row">
                <div class="col-12 d-flex justify-content-center">
                    <a href="#" class="btn btn-send" @click="step = 3">
                        Камера
                    </a>
                    <input type="file" accept="image/*" capture="camera" />
                </div>
            </div>
        </div>
        <div class="container your telephone" v-if="step == 3">
            <div class="row">
                <div class="col-12">
                    <a href="#" @click="step = 2" class="btn btn-back">
                        <img src="images/back.png" alt="back" />
                    </a>
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
                <div class="col-12 d-flex justify-content-center">
                    <div class="input">
                        <the-mask
                            :mask="['+7 ### ### ## ##']"
                            class="tel"
                            placeholder="+7 966 999 88 77"
                            v-model="phone"
                        />
                    </div>
                </div>
            </div>
            <div class="row">
                <div class="col-12 d-flex justify-content-center">
                    <a href="#" class="btn btn-send" @click="sendPhone">
                        Авторизация
                    </a>
                </div>
            </div>
        </div>
        <div class="container choose-color" v-if="step == 4">
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
                <div class="col-12 d-flex">
                    <div class="template">
                        <img src="images/none.png" alt="" />
                    </div>
                    <!-- <div
                        class="template"
                        v-for="(item, index) in stemping"
                        :key="index"
                    >
                        <img :src="item.photo" alt="" />
                    </div> -->
                    {{ stemping[0] }}
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    import { TheMask } from "vue-the-mask";
    export default {
        components: { TheMask },
        data() {
            return {
                num: "",
                step: 1,
                stemping: [],
                phone: "",
                activeGroup: null,
            };
        },
        methods: {
            sendPhone() {
                let tel = "+7" + this.phone;
                this.$axios
                    .$post(
                        `http://178.154.209.29:4343/add_to_csv?csv_parameter=${tel}`
                    )
                    .then((response) => {
                        this.step = 4;
                    })
                    .catch((err) => {
                        alert("error");
                    });
            },
            accept() {},
            async sendCode() {
                if (this.num.length == 4) {
                    this.step = 2;
                    console.log(this.num);
                    this.stemping = await this.$axios.$get(
                        `http://178.154.209.29:4343/download?salon_code=${this.num}`
                    );
                } else {
                    alert("Введите код");
                    this.num = "";
                }
            },
            check(event) {
                let input = document.querySelector(".code-v");
                if (input) {
                    if (event.length == 4) {
                        input.blur();
                    }
                }
            },
            send() {},
        },
    };
</script>
<style>
    @import url("https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,100;0,300;0,400;0,700;0,900;1,100;1,300;1,400;1,700;1,900&display=swap");
    @import url("https://fonts.googleapis.com/css2?family=DM+Sans:ital,wght@0,400;0,500;0,700;1,400;1,500;1,700&display=swap");

    .input-v {
        display: flex;
        justify-content: center;
        margin-top: 40px;
        height: 70px;
    }
    input.code-v {
        width: 380px;
        height: 70px;
        font-family: "DM Sans";
        font-size: 24px;
        line-height: 32px;
        border: none;
        background-color: transparent;
        background-image: url("../static/images/Code-number.png");
        background-position: center;
        background-repeat: no-repeat;
        text-align: left;
        letter-spacing: 28px;
        padding: 30px;
        cursor: none;
        color: transparent;
        text-shadow: 0 0 0 #2e476e;
    }
    input:focus {
        outline: none;
    }
    input.code:last-child {
        margin-right: 0;
    }
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
</style>