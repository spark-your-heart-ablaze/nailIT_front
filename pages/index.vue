<template>
    <div class="container">
        <div class="row">
            <div class="col-12 d-flex justify-content-center">
                <div class="logo">
                    <img src="images/logo.png" alt="" />
                </div>
            </div>
            <div class="col-12 d-flex justify-content-center">
                <div class="logo-name">Nailed IT</div>
            </div>
            <div class="col-12">
                <div class="subtitle d-flex justify-content-center">
                    За 30 секунд примерь дизайн своей мечты
                </div>
            </div>
            <div class="col-12 d-flex justify-content-center">
                <nuxt-link to="user-info" class="btn btn-start">
                    Начать <img src="images/arrow.png" alt="" />
                </nuxt-link>
            </div>
        </div>
    </div>
</template>

<script>
    export default {};
</script>

<style >
    @import url("https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,100;0,300;0,400;0,700;0,900;1,100;1,300;1,400;1,700;1,900&display=swap");
    .logo {
        margin-top: 50px;
    }
    .logo-name {
        font-family: Lato;
        font-weight: bold;
        font-size: 48px;
        line-height: 32px;
        color: #334669;
        margin-top: 70px;
    }
    .subtitle {
        font-family: Lato;
        font-size: 24px;
        line-height: 24px;
        color: #334669;
        opacity: 0.6;
        margin-top: 50px;
        text-align: center;
    }
    .btn-start {
        display: flex;
        justify-content: space-between;
        align-items: center;
        width: 70%;
        max-width: 350px;
        margin-top: 48px;
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
        border-radius: 100px;
        padding: 19px 35px;
    }
    .btn:hover {
        color: #fff;
    }
</style>
