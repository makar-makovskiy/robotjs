<template>
    <div>
      <h2>QR-код на портфолия</h2>
      <canvas ref="canvas"></canvas>
      <p>Отсканируй, чтобы открыть</p>
      <button class="visit-btn" @click="visitSite">Перейти на QR-коду</button>
    </div>
</template>

<script>
import QRCode from 'qrcode'
export default{
    data(){
        return{
            url: 'https://makar-makovskiy.github.io/robotjs/#/'// указываем нужную ссылку
        }
    },
    mounted(){
        const canvas = this.$refs.canvas;
        if (canvas) {
            QRCode.toCanvas(canvas, this.url, {width: 180}, (error) =>{
                if (error) console.error(error)
            })
        }
    },
    methods: {
        visitSite(){
            window.open(this.url, '_blank')
        }
    }
}

</script>