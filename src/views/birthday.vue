<template>
    <img src="../assets/marFoto.jpg" class="foto" />
    <div>
        <span>Tempo para meu aniversário:</span>
        <br />
        <span>{{ texto }}</span>
    </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'birthday',
    data() {
        return {
            texto: 'Tempo',
        };
    },
    created() {
        const dataFinal = new Date("2023-10-07T00:00:01").getTime();
        const interval = setInterval(() => {
            let now = new Date().getTime();
            let diferenca = dataFinal - now;
            let days = Math.floor(diferenca / (1000 * 60 * 60 * 24));
            let hours = Math.floor((diferenca % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            let minutes = Math.floor((diferenca % (1000 * 60 * 60)) / (1000 * 60));
            let seconds = Math.floor((diferenca % (1000 * 60)) / 1000);

            this.texto = days + "d "
                + hours + "h " + minutes + "m " + seconds + "s ";

            if (diferenca < 0) {
                clearInterval(interval);

                this.texto = 'Chegouuuu!!!! aoooooo treeem!!!';
            }
        }, 1000);
    },
})
</script>


<style scoped>
.foto {
    height: 300px;
}
</style>