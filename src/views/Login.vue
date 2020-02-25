<template>
    <div id="login">
        <h1>Form Login</h1>
        <form class="">
        <div class="form-group">
            <label for="exampleInputEmail1">Username</label>
            <input type="text" class="form-control" name="username" v-model="input.username" placeholder="Username"/>
        </div>
        <div class="form-group">
            <label for="exampleInputPassword1">Password</label>
             <input type="password" class="form-control" name="password" v-model="input.password" placeholder="Password" />
        </div>
        <button type="button" class="btn-login" v-on:click="login()">Login</button>
        </form>
    </div>
</template>

<script>
    export default {
        name: 'Login',
        data() {
            return {
                input: {
                    username: "",
                    password: ""
                }
            }
        },
        methods: {
            login() {
                if(this.input.username != "" && this.input.password != "") {
                    if(this.input.username == this.$parent.mockAccount.username && this.input.password == this.$parent.mockAccount.password) {
                        this.$emit("authenticated", true);
                        this.$router.replace({ name: "Secure" });
                    } else {
                        console.log("Username atau Password Salah");
                    }
                } else {
                    console.log("A username and password must be present");
                }
            }
        }
    }
</script>

<style scoped>
    #login {
        font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        color :black;
        width: 400px;
        background-color: lightsalmon;
        border-radius: 30px;
        margin: auto;
        margin-top: 200px;
        padding: 20px;
        box-shadow: 2px 2px 2px 2px grey;
    }
    .form-group label {
        float: left;
    }
    .btn-login {
        background: white;
        border: 0;
        padding: 10px;
        width: 80px;
        border-radius: 10px;
    }
    .btn-login:hover {
        background : wheat;
        transition: 0.3s;
    }
</style>