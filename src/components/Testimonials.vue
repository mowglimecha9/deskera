<template>
    <div class="testimonial-container">
        <div class="container">
         <carousel :loop=true :per-page="1" :autoplay=true :navigationEnabled=true :mouse-drag="false">
            <slide>
            <p>We’ll surely recommend Deskera to everyone who is looking at the most effective ERP software. It has made invoicing faster and easier. From quotations and invoicing to payments – we now handle all transactions with one ERP system. Our sales, finance and fulfillment teams have access to the same accounting data which has greatly eliminated billing errors, improved data accuracy and strengthened the revenue recognition process.</p>
            <span class="name">Jimmy Ng</span>
            <span class="org">Admin &amp; Finance Manager, Clean Solutions Pte Ltd</span>
            </slide>
            <slide>
                <p>We needed a modern and affordable business software that could support our business needs as we continue to grow.</p>
                <p>With Deskera we now have a solution that supports our business operations with end-to-end accounting, HR and Sales. We have been able to reduce the time spend on consolidating of financial reports and get better insights about business performance.</p>
                <span class="name">Yuvonne chew</span>
                <span class="org">Director, Finance &amp; Operations, Esmegen Group</span>
            </slide>
            <slide>
                <p>As our business grew, we required a more streamlined approach to run our business. Managing the employee attendance was a very time-consuming task. With Deskera HRMS, we have been able to automate the process and reduce the time spent on attendance management.</p>
                <span class="name">Rajbir Singh Chopra</span>
                <span class="org">Sales and Marketing Director, Sports Fashion Pte Ltd</span>
            </slide>
        </carousel>
        </div>
    </div>
</template>
<script>
import { Carousel, Slide } from 'vue-carousel';
export default {
    components: {
        Carousel,
        Slide
  }
}
</script>
<style scoped>
    .testimonial-container {
        min-height: 50vh;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        background-color: #222;
    }  .slides {
        display: flex;
        align-items: center;
        justify-content: center;
        height: 100%;
        color:#fff;
        font-size: 18px;
    } 
    .VueCarousel-slide  {
        height: 100%;
        font-size: 18px;
        font-weight: normal;
        padding:15px;
        font-style: italic;
        color:#fff;
        text-align: center;
    }
    .name {
        font-size: 14px;
        font-style: normal;
        display: block;
    }.org {
         font-size: 12px;
        font-style: normal;
        display: block;
    }
</style>
