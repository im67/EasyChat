<template>
<div class = "main">
    <Row type="flex" justify="center" align="middle" class = "loginrow">
        <Col :xs = "0" :sm = "0" :md = "12" :lg = "12" ref = "logo1">
            <login-banner></login-banner>
        </Col>
        <Col class = "col" :xs = "0" :sm = "0" :md = "1" :lg = "1"><div class = "divideline"></div></Col>
        <Col :xs = "24" :sm = "24" :md = "11" :lg = "11">
            <login-form></login-form>
        </Col>
    </Row>
</div>
</template>

<script>
    import LoginBanner from "./components/logo"
    import LoginForm from "./components/loginform"
    export default {
        name:'login',
        components:{ LoginBanner,LoginForm },
        mounted:function(){
            console.log(this.$refs.logo1.offsetWidth);
        }
    }
</script>

<style lang="scss" scoped>
    .main{
        position:absolute;
        width:100%;
        height:100%;
        background-color: #28343C;
    }

    .loginrow{
        height: 100%;
    }

    .col{
        height:50%;
    }
    
    .divideline{
        height: 100%;
        width:2px;
        background-color:rgb(59, 60, 65);
    }
</style>
