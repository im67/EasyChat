<template>
    <div>
        <Row type="flex" justify="center" align="middle" class = "formrow">
            <Col :xs = "4" :sm = "4" :md = "1" :lg = "1"></Col>
            <Col :xs = "16" :sm = "16" :md = "15" :lg = "8">
                <Input prefix="ios-contact" class = "inputtext" size="large" v-model = "loginform.username" placeholder="请输入用户名..."/>
                <Input type = "password" prefix="md-lock" class = "inputtext" size="large" v-model = "loginform.password" placeholder="请输入密码..." />
                <Button class = "loginbtn" type="success">连接至聊天室</Button>
            </Col>
            <Col :xs = "4" :sm = "4" :md = "8" :lg = "15"></Col>
        </Row>
    </div>
</template>

<script>
    export default{
        name:'LoginForm',
        data(){
            return {
                loginform:{
                    username:'',
                    password:''
                }
            }
        }
    }
</script>

<style lang = "scss">
    .formrow{
        text-align:center;
    }

    .inputtext{
        margin:0.75rem 0 0.75rem 0;
    }

    .formrow .ivu-input::-webkit-input-placeholder{
        color:rgb(102, 101, 101);
    }


    .formrow .ivu-input-large{
        height:2.25rem;
        font-size: 0.75rem;
        color: rgb(255, 255, 255);
        font-weight: bold;
        border:1px solid rgb(102, 101, 101);
        background-color:rgba(0, 0, 0, 0);
    }

    .formrow .ivu-input-prefix i{
        line-height: 2.25rem;
        font-size:1rem;
    }

    .formrow .ivu-input:focus::-webkit-input-placeholder{
        color:white;
    }

    .formrow .ivu-input-large:focus{
        border:1px solid rgb(255, 255, 255);
    }
    

    .loginbtn{
        height:2.25rem;
        width: 100%;
        margin-top:0.75rem;
    }
</style>

