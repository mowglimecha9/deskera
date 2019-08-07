<template>
    <div>
        
        <div class="form-container">
            <div class="form-title">
                Deskera Registration
            </div>
            <div class="form-body">
                
                <form method="get" @submit.prevent="onSubmit">
                    
                    <div class="input-field col s12">
                        <input  id="full" v-model="name" type="text" required class="validate">
                        <label for="full">Full Name</label>
                        <span class="helper-text" data-error="Full Name is required"></span>
                    </div>
                    <div class="input-field col s12">
                        <input  id="email" v-model="email" type="email" required class="validate">
                        <label for="email">Email Address</label>
                        <span class="helper-text" data-error="Email Address is required"></span>

                    </div>
                    <div class="input-field col s12">
                        <input @change="checkEmpty"  id="phone" v-model="tel" type="tel" required class="validate" >
                        <label for="phone">Phone</label>
                            <span class="helper-text" data-error="Phone Number is required"></span>
                    </div>
                    <div class="input-field col s12">
                        <input  id="org" v-model="org" type="text"  >
                        <label for="org">Organisation</label>
                    </div>
                    <div class="input-field col s12" v-show="showDemo">
                        <select id="phone-demo" v-model="phoneCode" @change="changeCode">
                            <option value="" disabled >For demo you can choose the Country</option>
                            <option data-icon="http://icons.iconarchive.com/icons/wikipedia/flags/512/IT-Italy-Flag-icon.png" value="it">Italy</option>
                            <option selected data-icon="https://cdn.countryflags.com/thumbs/singapore/flag-400.png" value="sg">Singapore</option>
                            <option data-icon="https://cdn.countryflags.com/thumbs/united-states-of-america/flag-square-250.png" value="us">USA</option>
                        </select>
                    </div>
                    <div class="input-field col s12" style="text-align:center">
                        <input  class="btn" type="submit"  value="Submit" ref="dsSubmit">
                    </div>
                    <span class="demo-text" v-show="!showDemo" @click="showSelect">Click here to change country (phone demo)</span>
                    <span class="demo-text" v-show="showDemo" @click="showSelect">Hide change country (phone demo)</span>
                    
                </form>
            </div>
        </div>
    </div>
</template>
<script>
export default {
     data() {
        return {
          
           name:"",
           email:"",
           tel:"",
           org:"",
           prefix:"",
           phoneCode:"sg",
           showDemo:false,
           country_code:{
               sg:"65",
               it:"39",
               us:"1"
           },
           regex: {
               sg:/^[6|8|9]\d{7}|\+65[6|8|9]\d{7}|\+65\s[6|8|9]\d{7}$/,
               it:/^(([+]|00)39)?((3[1-6][0-9]))(\d{7})$/,
               us:/^(1\s?)?((\([0-9]{3}\))|[0-9]{3})[\s\-]?[\0-9]{3}[\s\-]?[0-9]{4}$/
           }
        }
    },
    methods: {
        onSubmit:function(e){
            e.preventDefault();
            var validNumber = this.testNumbers();
            if (validNumber) {
                this.$refs.dsSubmit.disabled = true;
                this.$refs.dsSubmit.value= "Submitted";
                console.log("Name: "+ this.name);
                console.log("Email: "+ this.email);
                console.log("Tel: "+ this.tel);
                console.log("Organisation: "+ this.org);
            } else {
                alert("Phone Number entered is invalid")
            }
        },
        showSelect:function(){
            this.showDemo = !this.showDemo;
        },
        testNumbers:function() {
            let code = this.phoneCode;
            var regex = new RegExp(this.regex[code]);
            return regex.test(this.tel);
        },
        checkEmpty:function() {
            // Check if empty then revert to country code if its true
            if(this.tel.length == 0) {
                this.tel = this.country_code[this.phoneCode]
            }
        },
        changeCode:function() {
        this.tel = this.country_code[this.phoneCode]
        this.testNumbers();
            
        },
        initSelect:function() {   
            var elems = document.querySelectorAll('select');
            var instances = M.FormSelect.init(elems, {});
        },
    },mounted : function() {
        this.initSelect();
        this.tel = this.country_code[this.phoneCode]
    }
}
</script>
<style scoped>

.form-title {
    font-family: 'Roboto', sans-serif;
    width: 100%;
    padding:15px 10px;
    text-align: left;
    font-size: 20px;
    color:#fff;
    text-align: center;
    background-color: #e7494d;
    
}
.btn{
     background-color: #e7494d;
}
.form-body {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    padding:15px 25px;
    background-color: #fff;
    border:1px solid rgba(0, 0, 0, 0.125);
}
.demo-text {
    font-size: 12px;
    color: #3db0b0;
    display: block;
    text-align: center;
    cursor: pointer;
    text-decoration: underline
}
</style>


