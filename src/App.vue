<template>
    <login></login>
    <div class="toasts">
        <TheToast v-for="(toast,i) in toasts" :key="toast" :toastType="toast.type" :message="toast.message"></TheToast>
    </div>
</template>

<script>
import Login from './components/Login.vue';
import TheToast from './components/TheToast.vue';
export default {

    data: () =>({
        toasts: [
        // {
        //     type:"Success",
        //     message:"Done Successfully"
        // },
        // {
        //     type:"Error",
        //     message:"Something Went Wrong"
        // },
    ]
    }),
    components: {
        Login,
        TheToast
    },
    mounted() {
        this.$eventBus.on('toast', (data) => {
            this.toasts.push(data);
            this.removeOnToast();
        });
    },
    methods: {
        removeOnToast(){
            setTimeout(() => {
                this.toasts.shift();
            }, 2000);
        }
    }
}
</script>

<style lang="">
    
</style>

