<template>
    <div class="nav-header">
        <div class="header-content">
            <div class="header-left">
                <img v-if="tabIndex != 2 && tabIndex != 21 &&  tabIndex != 10 &&  tabIndex != 4 &&  tabIndex != 6 &&  tabIndex != 3 &&  tabIndex != 31" class="lobby-icon lobby-pc" @click="changeSlider" :src="require('../../assets/index/lobby.png')" />
                <img class="menu-icon" @click="toPage(1)" :src="require('../../../static/logo.png')" />
            </div>
            <div class="header-middle">
                <div class="menu-item">
                    <img class="menu-icon" @click="toRecharge()" :src="require('../../assets/index/refer.png')" />
                </div>
                <div class="menu-item">
                    <img class="menu-icon" @click="toPage(11)" :src="require('../../assets/index/vip.png')" />
                </div>
                <div class="menu-item">
                    <img class="menu-icon" @click="toPage(4)" :src="require('../../assets/index/me.png')" />
                </div>
                <div class="btn-w" v-if="accountid == 0" @click="toLogin">
                    <div style="flex: 1;">{{ GLOBAL.lanLocal['login'] }}</div>
                </div>
                <div class="btn-s" v-if="accountid == 0" @click="toReg">
                    <div style="flex: 1;">{{ GLOBAL.lanLocal['register_upper'] }}</div>
                </div>
                <div class="box-amount" v-if="accountid != 0" @click="toRecharge">
                    <div style="flex: 1;padding-top:3px;">{{ GLOBAL.currencySymbol }}&nbsp;{{ amount }}</div>
                    <img :src="require('../../assets/index/recharge.png')" />
                </div>
            </div>
            <div class="header-right" :class="accountid===0 ? 'header-right-login' : ''">
                <a :href="'https://line.me/ti/p/LYrxSVfLw2'" target="_blank">
                    <img :src="require('../../assets/index/service.png')" />
                </a>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'navheader',
    data() {
        return {
            lanCode: '',
            isShowLan: false,
        }
    },
    created() {
        this.lanCode = this.GLOBAL.lanCode
    },
    watch: {
        amount: {
            immediate: true,
            handler(newValue, oldValue) {
            }
        },
        accountid: {
            immediate: true,
            handler(newValue, oldValue) {
            }
        },
        tabIndex: {
            immediate: true,
            handler(newValue, oldValue) {
            }
        },
    },
    props: {
        tabIndex: {
            type: Number,
            default: 0
        },
        amount: {
            type: String,
            default: '0.00'
        },
        accountid: {
            type: Number,
            default: 0
        },
        lanData: {
            type: Array,
            default: []
        }
    },
    computed: {

    },
    mounted() { },
    methods: {
        toPage(type) {
            this.tabIndex = type
            this.$emit('change', type)
        },
        close() {
            this.$emit('close')
        },
        setLan(code) {
            this.$emit("setLan", code)
        },
        changeLan() {
            this.isShowLan = !this.isShowLan
        },
        func1() {

        },
        changeSlider() {
            this.$emit('changeSlider')
        },
        func1() {
        },
        toLogin() {
            this.$emit('toLogin')
        },
        toReg() {
            this.$emit('toReg')
        },
        toRecharge() {
            this.$emit('toRecharge')
        },
    }
}
</script>
<style lang="less" scoped>
.nav-header {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 3;
    height: 90px;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    box-sizing: border-box;
    background: #0f111d;
    padding: 0px 30px;

    .header-content {
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin: 0 auto;
        box-sizing: border-box;
        padding: 0 16px;

        .header-left {
            display: flex;
            align-items: center;
        }
    }

    .lobby-icon {
        cursor: pointer;
        width: 70px;
        height: 70px;
        margin-right: 8px;
    }

    .menu-icon {
        cursor: pointer;
        width: 100px;
        height: auto;
        margin-top: 10px;
        margin-right: 8px;
    }

    .header-right {
        display: flex;
        justify-content: center;
        align-items: center;

        >a {
            padding-top: 10px;
            >img {
                width: 50px;
                height: 50px;
            }
        }
    }

    .header-right-login{
        display: flex;
    }

    .main-icon {
        height:46px !important;
        width: 126px;
        display: flex;
    }

    .menu-mobile {
        display: none;
    }

    .mobile-pc {
        display: flex;
    }

    @media only screen and (max-width: 450px) {
        .main-icon {
            display: none;
        }

        .menu-mobile {
            display: flex;
        }

        .lobby-pc {
            display: none;
        }

        .menu-icon {
            width: 60px;
            height: auto;
            margin-top: 0px;
        }


        .header-right {
            >img {
                width: 40px;
                height: 40px;
            }
        }

        .header-right-login{
            display: none;
        }
    }

    .header-middle {
        flex: 1;
        display: flex;
        align-items: center;
        justify-content: center !important;

        .menu-item {
            margin-right: 80px;

            >img {
                width: 60px;
                height: 60px;
            }
        }

        .btn-s {
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 0 12px;
            font-family: Arial;
            margin-left: 15px;
            margin-right: -80px;
            font-weight: 400;
            border: 2px solid #d5b607;
            border-radius: 18px;
            color: white;
            display: flex;
            align-items: center;
            box-sizing: border-box;
            cursor: pointer;
            width: 86px;
            height: 36px;
            font-size: 12px;
            background: rgb(19,18,36);
            background: linear-gradient(180deg, rgba(19,18,36,1) 0%, rgba(176,149,13,1) 100%);
            transition: transform .1s ease-in-out;
            position: relative;
        }

        .btn-w {
            font-family: Arial;
            margin-left: 6px;
            padding: 0 12px;
            font-weight: 400;
            border: 2px solid #049dda;
            border-radius: 18px;
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            box-sizing: border-box;
            cursor: pointer;
            width: 86px;
            height: 36px;
            font-size: 12px;
            background: rgb(19,18,36);
            background: linear-gradient(180deg, rgba(19,18,36,1) 0%, rgba(9,99,139,1) 100%);
            position: relative;
        }

        .box-amount {
            color: white;
            font-weight: 700;
            background: #2f2e2c;
            box-shadow: 0 0 0.2rem rgba(251,216,30,.3), inset 0 -0.04rem 0.06rem 0.02rem #2f2e2c;
            display: flex;
            align-items: center;
            box-sizing: border-box;
            font-size: 12px;
            padding: 0 6px;
            height: 28px;
            line-height: 28px;
            border-radius: 100px;

            >img {
                cursor: pointer;
                height: 32px;
                width: 32px;
                margin-left: 6px;
            }
        }

        .lan-box {
            font-size: 0;
            position: relative;
            padding-right: 10px;
        }

        .wallert {
            background-color: rgb(58, 64, 71);
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 8px;
            box-sizing: border-box;
            width: 100px;
            height: 26px;
            border-radius: 8px;

            div {
                font-size: 12px;
                color: #fff;
            }

            img {
                width: 15px;
                height: 15px;
            }
        }

        .me-icon {
            margin-left: 6px;
        }
    }

    .amount-modal {
        position: absolute;
        top: 58px;
        right: 10px;
        height: 70px;
        width: 90px;
        z-index: 999;
        background-color: rgb(44, 52, 62);
        color: #f6f6f6;

        div {
            height: 35px;
            line-height: 35px;
            margin: 0 10px;
            font-size: 13px;
        }

        div:not(:last-child) {
            border-bottom: 1px solid rgb(34, 40, 48);
        }
    }

    .amount-modal::before {
        content: "";
        display: inline-block;
        position: absolute;
        right: 12px;
        top: -9px;
        border-bottom: 10px solid rgb(44, 52, 62);
        border-right: 10px solid transparent;
        border-left: 10px solid transparent;
    }
}

@media only screen and (max-width: 450px) {
    .nav-header {
        height: 60px !important;
        padding: 0px 5px;
    }

    .menu-item {
        display: none;
    }
}

.lan-masking {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 998;
    height: 100%;
    width: 100%;
}


.lan-modal::before {
    content: "";
    display: inline-block;
    position: absolute;
    right: 12px;
    top: -9px;
    border-bottom: 10px solid rgb(39, 44, 50);
    border-right: 10px solid transparent;
    border-left: 10px solid transparent;
}

.lan-modal {
    position: absolute;
    top: 55px;
    right: 12px;
    background-color: rgb(39, 44, 50);
    border-radius: 6px;

    .lan-item {
        width: 100%;
        height: 50px;
        display: flex;
        align-items: center;
        justify-content: flex-start;
        position: relative;
        padding: 0 20px;
        box-sizing: border-box;
        border-bottom: 1px solid rgb(44, 50, 57);

        .icon {
            height: 30px;
            width: 30px;
            margin-right: 8px;
        }

        div {
            color: rgb(144, 151, 161);
            font-size: 16px;
        }
    }
}
</style>