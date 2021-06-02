<template>
    <div class="nail-it">
        <div class="loading" v-if="load">
            <img src="/images/loading.png" alt="" class="load-img" />
        </div>
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
                    <input
                        type="file"
                        accept="image/x-png,image/gif,image/jpeg"
                        capture="camera"
                        class="btn btn-send"
                        ref="file"
                        id="photo"
                        @change="onFileChange"
                    />
                    <canvas id="canvas" style="display: none" />
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
            <div class="row">
                <div class="col-12 pl-0 pr-0">
                    <div
                        class="btn-group d-flex justify-content-between align-items-center"
                    >
                        <div>
                            <a href="#" @click="step = 1" class="btn btn-back">
                                <img src="images/back.png" alt="back" />
                            </a>
                        </div>
                        <div>
                            <a
                                href=""
                                download
                                class="btn btn-back"
                                id="link-download"
                            >
                                <img src="images/save.svg" alt="save"
                            /></a>
                        </div>
                    </div>
                </div>
            </div>
            <div class="row">
                <div class="imgbox">
                    <img class="center-fit" id="myImage" src="" alt="" />
                </div>
            </div>
            <div class="setting col-12" :class="{ 'hide-sett': closeSetting }">
                <div class="row">
                    <div class="col-4" style="text-align: left">
                        <img src="images/filtr.png" alt="" /> Фильтр
                    </div>
                    <div
                        class="col-4"
                        v-if="activeWin == 2"
                        style="text-align: center"
                    >
                        <span> Цвет</span>
                    </div>
                    <div
                        class="col-4"
                        v-if="activeWin == 1"
                        style="text-align: center"
                    >
                        <span>Стемпинг</span>
                    </div>
                    <div
                        class="col-4 d-flex justify-content-end"
                        style="text-align: "
                        @click="closeSetting = !closeSetting"
                        v-if="!closeSetting"
                    >
                        Скрыть
                    </div>
                    <div
                        class="col-4 d-flex justify-content-end"
                        style="text-align: "
                        @click="closeSetting = !closeSetting"
                        v-if="closeSetting"
                    >
                        Раскрыть
                    </div>
                </div>
                <div class="row">
                    <div class="col-12 d-flex templates" v-if="activeWin == 1">
                        <div class="template" @click="clearPhoto">
                            <img src="images/none.png" alt="" />
                        </div>
                        <div
                            class="template"
                            v-for="(item, index) in stemp"
                            :key="index"
                            :id="item['Номер пластины']"
                            @click="getStemp(item['Номер пластины'])"
                        >
                            <img :src="item['photo']" alt="" />
                        </div>
                    </div>
                    <div class="col-12 d-flex templates" v-if="activeWin == 2">
                        <div class="template" @click="clearPhoto">
                            <img src="images/none.png" alt="" />
                        </div>
                        <div
                            class="template"
                            v-for="(item, index) in color"
                            :key="index"
                            :id="item['color code']"
                            @click="getColor(item['🔒 Row ID'])"
                        >
                            <img :src="item['photo']" alt="" />
                        </div>
                    </div>
                </div>
            </div>
            <div class="row">
                <div class="col-12">
                    <div class="control">
                        <div @click="activeWin = 2">
                            <img src="images/rgb.png" alt="" />
                            <p>Цвет</p>
                        </div>
                        <div>
                            <img src="images/cam.png" alt="" />
                            <p>Камера</p>
                        </div>
                        <div @click="activeWin = 1">
                            <img src="images/stemp.png" alt="" />
                            <p>Стемпинг</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    import { TheMask } from "vue-the-mask";
    import axios from "axios";
    export default {
        components: { TheMask },
        data() {
            return {
                num: "",
                step: 1,
                array: [],
                ara: [{ ar: 1 }, { ar: 1 }],
                phone: "",
                activeGroup: null,
                photo: null,
                url: "",
                file: "",
                activeWin: 2,
                idStemp: null,
                idColor: null,
                photo_name: null,
                color_condition: 0,
                stamping_condition: 0,
                closeSetting: false,
                photoNone: "",
                load: false,
            };
        },
        computed: {
            stemp() {
                return this.array.filter((e) => {
                    return e["Номер пластины"] != "none";
                });
            },
            color() {
                return this.array.filter((e) => {
                    return e["color code"] != "none";
                });
            },
        },
        methods: {
            clearPhoto() {
                console.log(this.photoNone);
                document.getElementById("myImage").src = this.photoNone;
            },
            getStemp(id) {
                console.log(id);
                this.$axios
                    .$get(
                        `/equip_stamp?photo_name=${this.photo_name}&stamping_condition=${this.stamping_condition}&color_condition=${this.color_condition}&stamping=${id}'`
                    )
                    .then((response) => {
                        this.stamping_condition = 1;
                        this.url = response;
                        document.getElementById("myImage").src = this.url;
                        document.getElementById("link-download").href = this.url;
                    });
            },
            getColor(id) {
                console.log(id);
                this.$axios
                    .$get(
                        `/equip?photo_name=${this.photo_name}&stamping_condition=${this.stamping_condition}&color_condition=${this.color_condition}&color=${id}`
                    )
                    .then((response) => {
                        this.color_condition = 1;
                        this.url = response;
                        document.getElementById("myImage").src = this.url;
                        document.getElementById("link-download").href = this.url;
                    });
            },
            sendPhone() {
                let tel = "+7" + this.phone;
                console.log("telephone");
                this.load = true;
                if (tel.length == 12) {
                    this.$axios
                        .$post(`/add_to_csv?csv_parameter=${tel}`)
                        .then((response) => {
                            this.step = 4;
                            var vm = this;
                            this.load = false;
                            setTimeout(function () {
                                document.getElementById("myImage").src = vm.url;
                                document.getElementById("link-download").href =
                                    vm.url;
                            }, 1000);
                        })
                        .catch((err) => {
                            alert(err);
                        });
                } else {
                    alert("Введите корректный номер телефона");
                }
            },
            sendCode() {
                if (this.num.length == 4) {
                    this.step = 2;
                    // this.stemping = await
                    this.$axios
                        .$get(`/download?salon_code=${this.num}`)
                        .then((response) => {
                            this.array = Object.values(response);
                        });
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
            onFileChange(e) {
                this.photo_name = Math.random().toString(36).substr(2, 9);
                this.file = this.$refs.file.files[0];
                let formData = new FormData();
                formData.append("Photo", this.file);
                console.log(formData);
                this.step = 3;
                this.$axios //отправка изображения на сервер
                    .$post(`/prediction?name=${this.photo_name}`, formData)
                    .then((response) => {
                        this.url = response;
                        this.photoNone = response;
                    })
                    .catch((err) => {
                        alert("error");
                        this.step = 3;
                    });
            },
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
        letter-spacing: 30px;
        padding: 30px;
        cursor: none;
        color: transparent;
        text-shadow: 0 0 0 #2e476e;
    }
    @media (max-width: 370px) {
        input.code-v {
            padding: 15px;
        }
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
    .templates {
        justify-content: space-between;
        flex-wrap: wrap;
        padding-bottom: 460px;
        position: fixed;
        height: 100%;
        overflow: auto;
    }
    .template img {
        width: 60px;
        height: 60px;
    }
    .template {
        width: 60px;
        height: 60px;
        margin-bottom: 9px;
        touch-action: none;
    }
    #file-upload-button {
        background: transparent;
    }
    input[type="file"] {
        background: transparent;
    }
    .control {
        position: fixed;
        bottom: 0px;
        background: #f8f3f3;
        width: 100vw;
        height: 104px;
        display: flex;
        justify-content: space-around;
        align-items: center;
        left: 0;
    }
    .control div {
        text-align: center;
    }
    #photo {
        position: absolute;
        opacity: 0;
    }
    .setting {
        font-family: Lato;
        font-style: normal;
        font-weight: bold;
        font-size: 16px;
        line-height: 24px;
        /* identical to box height, or 171% */

        color: #334669;

        mix-blend-mode: normal;
        position: fixed;
        left: 0;
        top: calc(100vh - 329px);
        height: 100%;
        overflow: auto;
        background: #f8f3f3;
        border-radius: 30px;
        transition: all 0.5s ease-in-out;
    }
    .hide-sett {
        top: calc(100vh - 190px) !important;
    }
    .setting span {
        font-family: Lato;
        font-style: normal;
        font-weight: bold;
        font-size: 14px;
        line-height: 24px;
        /* identical to box height, or 240% */

        text-align: center;

        color: #1e2a41;

        mix-blend-mode: normal;
    }
    .btn-group {
        background: #f8f3f3;
        width: 100%;
        height: 70px;
    }
    .btn-group .btn-back {
        margin: 15px;
    }
    .imgbox {
        height: 80%;
    }
    .center-fit {
        display: block;
        width: 100%;
        max-height: 80vh;
        /* transform: rotate(90deg); */
    }
    .choose-color {
        height: 100%;
        max-height: 100%;
        max-width: 100%;
    }
    .loading {
        position: absolute;
        width: 100%;
        height: 100%;
        z-index: 1000;
        background: rgba(145, 144, 144, 0.5);
        display: flex;
        align-items: center;
        justify-content: center;
    }
    .load-img {
        width: 70px;
        height: 70px;
        opacity: 1;
        animation: 3s linear 0s normal none infinite running rot;
        -webkit-animation: 3s linear 0s normal none infinite running rot;
    }
    @keyframes rot {
        0% {
            transform: rotate(0deg);
        }
        100% {
            transform: rotate(360deg);
        }
    }
    @-webkit-keyframes rot {
        0% {
            transform: rotate(0deg);
        }
        100% {
            transform: rotate(360deg);
        }
    }
</style>
