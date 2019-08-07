<template>
    <div class="hero-container  " style="position:relative;display:flex;align-items:center" >
       <div class="hero-bg parallax" :style="{backgroundPositionY:bgPosY + 'px'}"/>
       <div class="container ds-cont row">
            <div class="col m3"/>
            <div class="col m6 ">
                <FormComponent/>
            </div>
            <div class="col m3"/>
       </div>
    </div>    
</template>
<script>
import FormComponent from './Form.vue'
export default {
    data() {
        return {
           bgPosY:0,
           name:"",
           email:"",
           tel:"",
           org:"",
        }
    },
    components:{
        FormComponent
    },
    props: {
        scrollPos:Number
    },
    watch:{
        scrollPos:function(e) {
            let gravity = 10;
            let m = e/gravity;
            this.bgPosY = m

        }
    },
    mounted:function(){
    }
}
</script>

<style scoped>
.hero-container {
    min-height: 100vh;
    height: 100%;
    width:100%;
}
.hero-bg {
    position: absolute;
    top:0;
    left: 0;
    z-index: 0;
    height: 100%;
    width: 100%;
    background-repeat: no-repeat;
    background-image: url('../assets/bg.jpg');
    background-size: cover;
    transition: all 0.2s linear;
}
/* Portrait and Landscape */


.hero-bg:after {
    position: absolute;
    top:0;
    left: 0;
    height: 100%;
    width: 100%;
    content: "";
    background-color:rgba(113, 8, 6, 0.4)
    
}.ds-cont {
    position: relative;
    z-index: 1;
}
</style>
