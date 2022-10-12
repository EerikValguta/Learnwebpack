<template>
    <div class="columns">
        <div class="column is-one-third has-text-centered">
            <b>{{clicks}} clicks</b>  
            <br>
            <b>{{cps}} clicks per second</b>  
            <img @click="clickClick()" :class="{'click': clickClass}" src="https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/be02a4e3-e357-4bde-b048-3a8a59e11d49/d2mcev3-5ac40603-bd13-49ed-b235-859ee4fd46cb.png?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7InBhdGgiOiJcL2ZcL2JlMDJhNGUzLWUzNTctNGJkZS1iMDQ4LTNhOGE1OWUxMWQ0OVwvZDJtY2V2My01YWM0MDYwMy1iZDEzLTQ5ZWQtYjIzNS04NTllZTRmZDQ2Y2IucG5nIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmZpbGUuZG93bmxvYWQiXX0.LJLK_Ka0GIqVx1C0RwYv7vvE4Vgc3BuYUdttCUAJ3RM">   
        </div>
        <div class="column">
            <button @click="upgrade(0.1, 10)" class="button is-white" :disabled="clicks<10">Buy 0.1 cps for 10 clicks</button>     
            <br>
            <br>
            <button @click="upgrade(1, 100)" class="button is-white" :disabled="clicks<100">Buy 1 cps for 100 clicks</button> 
            <br>
            <br>
            <button @click="upgrade(10, 1000)" class="button is-white" :disabled="clicks<1000">Buy 10 cps for 1000 clicks</button>
            <br>  
            <br>    
            <button @click="upgrade(100, 10000)" class="button is-white" :disabled="clicks<10000">Buy 100 cps for 10000 clicks</button> 
            <br>
            <br>
            <button @click="upgrade(1000, 100000)" class="button is-white" :disabled="clicks<100000">Buy 1000 cps for 100000 clicks</button> 

        </div>
    </div>
  
</template>

<script>
export default {
    created(){
        setInterval(()=>{
            this.clicks += this.cps;
            this.clicks = parseFloat(this.clicks.toFixed(1));


        }, 1000);
    },
    data(){
        return {
            clickClass: false,
            clicks: 0,
            cps: 0

        }
    },
    methods: {
        clickClick(){
            this.clicks++;
            this.clickClass = true;
            setTimeout(()=> {
                this.clickClass = false;
            }, 100);
        },
        upgrade(cps, cost){
            if(this.clicks >= cost){
                this.clicks -= cost;
                this.cps += cps;
            }
        }
    }

}


</script>

<style scoped>
    img.click {
        transform: scale(0.9);
    }
</style>