<template>
    <div class="add container">
        <h1 class="page-header">添加用户</h1>
        <form v-on:submit="addCustomer">
            <div class="well">
                <h4>用户信息</h4>
                <div class="form-group">
                    <label>姓名</label>
                    <input type="text" class="form-control" placeholder="name" v-model="customer.name">
                </div>
                <div class="form-group">
                    <label>电话</label>
                    <input type="number" class="form-control" placeholder="phone" v-model="customer.phone">
                </div>
                <div class="form-group">
                    <label>邮件</label>
                    <input type="text" class="form-control" placeholder="email" v-model="customer.email">
                </div>
                <div class="form-group">
                    <label>网址</label>
                    <input type="text" class="form-control" placeholder="website" v-model="customer.website">
                </div>
                <div class="form-group">
                    <label>学历</label>
                    <input type="text" class="form-control" placeholder="education" v-model="customer.education">
                </div>
                <div class="form-group">
                    <label>职业</label>
                    <input type="text" class="form-control" placeholder="profession" v-model="customer.profession">
                </div>
                <div class="form-group">
                    <label>个人简介</label>
                    <textarea  class="form-control"  v-model="customer.profile" rows="10"></textarea>
                </div>
                <button type="submit" class="btn btn-primary">添加</button>
            </div>
        </form>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                customer:{}
            }
        },
        methods:{
            addCustomer(e){
                // console.log(123);
                if(!this.customer.name||!this.customer.phone||!this.customer.email){
                    alert("请添加对应的信息");
                }else{
                    let newCustomer={
                        name:this.customer.name,
                        phone:this.customer.phone,
                        email:this.customer.email,
                        website:this.customer.website,
                        education:this.customer.education,
                        profession:this.customer.profession,
                        profile:this.customer.profile
                    }
                    this.$http.post("http://localhost:3000/users",newCustomer)
                    .then(res=>{
                        // console.log(res);
                        this.$router.push({path:"/",query:{alert:"用户信息添加成功"}});
                    })

                }
                e.preventDefault();
            }
        }
    }
</script>

<style >

</style>