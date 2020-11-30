<template>
    <div>
        <mt-header title="新增缴费账户">
            <router-link to="/" slot="left">
                <mt-button icon="back"></mt-button>
            </router-link>
            <!--            <mt-button icon="more" slot="right"></mt-button>-->
        </mt-header>

        <mt-field label="缴费单位" placeholder="请选择缴费单位" v-model="organization" @click.stop.native="clickBillingInput"
                  @input.stop.native="inputSomething"></mt-field>
        <mt-field label="户号" placeholder="请输入户号" v-model="account"></mt-field>

        <div style="display: flex;
                    justify-content: center;
                    align-items: center;
                    margin: 3px;
                    height: 30px;">
            <input type="radio" id="one" value="1" v-model="picked" @click="changeRadio">
            <p>已阅读并同意《缴费协议》</p>
        </div>

        <div class="bottom">
            <mt-button type="primary">下一步</mt-button>
        </div>

        <mt-popup
            v-model="popupVisible"
            position="right" :modal="true" :closeOnClickModal="true">
            <mt-index-list style="width: 60vw; height: 100vh">
                <mt-index-section index="S">
                    <mt-cell title="石家庄缴费公司" @click.native="chooseOrganization"></mt-cell>
                    <mt-cell title="苏州缴费公司" @click.native="chooseOrganization"></mt-cell>
                    <mt-cell title="喵喵喵" @click.native="chooseOrganization"></mt-cell>
                </mt-index-section>
                <mt-index-section index="Z">
                    <mt-cell title="汪汪汪" @click.native="chooseOrganization"></mt-cell>
                    <mt-cell title="哈士奇" @click.native="chooseOrganization"></mt-cell>
                </mt-index-section>
            </mt-index-list>
        </mt-popup>
    </div>
</template>

<script>
    export default {
        name: "BillingAccount",
        data() {
            return {
                organization: "",
                account: "",

                popupVisible: false,

                picked: "1"
            }
        },
        methods: {
            clickBillingInput(e) {
                e.preventDefault();
                console.log("clickBillingInput");
                this.popupVisible = !(this.popupVisible);
            },
            inputSomething(val) {
                this.organization = "";
                return false
            },

            // 选择缴费单位
            chooseOrganization(e) {
                this.organization = e.target.innerText;
                this.popupVisible = false;
            },

            changeRadio() {
                console.log("hh");
                this.picked = this.picked === "1" ? "0" : "1";
            }
        },
    }
</script>

<style scoped>
    .header {
    }

    .bottom {
        width: 100%;
        padding: 5px;
        box-sizing: border-box;
    }

    .bottom button {
        width: 100%;
    }
</style>
