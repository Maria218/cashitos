<template>
    <div class="container my-12 mx-auto">
        <div class="flex flex-wrap">
            <div v-for="index in cardInfo.sort(() => Math.random() - 0.7).slice(0,4)" v-bind:key="index" class="cards p-5 sm:w-1/2 md:w-1/2 lg:w-1/2">
                <div @click="effects(index.days, index.money)" class="max-w-sm w-full lg:flex rounded-lg border-r border-b border-l border-t border-gray-700 lg:border-l lg:border-t lg:border-r lg:border-b lg:border-gray-700 bg-white">
                    <div class="px-6 py-4">
                        <div class="font-bold text-xl mb-2">
                            <h1 class="text-center">{{index.description}}</h1>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import { mapMutations } from "vuex";
    import anime from 'animejs/lib/anime.es.js';

    var object = [
            {
                description: "Cut all the trees",
                days: -275,
                money: 100
            },
            {
                description: "Drill more oil",
                days: -70,
                money: 100
            },
            {
                description: "Build a forest reserve",
                days: 50,
                money: 50
            },
            {
                description: "Start a war",
                days: -70,
                money: 70
            },
            {
                description: "Open a sweatshop",
                days: -10,
                money: 70
            },
            {
                description: "Build a wall",
                days: 0,
                money: 50
            },
            {
                description: "Start a cattle ranch",
                days: -10,
                money: 40
            },
            {
                description: "Start a wildfire",
                days: -50,
                money: -100
            },
            {
                description: "Clear a forest",
                days: -20,
                money: 20
            },
            {
                description: "Dump waste into the ocean",
                days: -70,
                money: 45
            },
            {
                description: "Build a dam",
                days: -10,
                money: 20
            },
            {
                description: "Dump nuclear waste",
                days: -70,
                money: 60
            },
            {
                description: "Poach endangered wildlife",
                days: -50,
                money: 10
            },
            {
                description: "Add more cars",
                days: -30,
                money: 20
            },
            {
                description: "Open a coal mine",
                days: -20,
                money: 10
            },
            {
                description: "Reduce employee wages",
                days: -5,
                money: 60
            },
            {
                description: "Fire half of workforce",
                days: -5,
                money: 0
            },
            {
                description: "Legalize child labour",
                days: -5,
                money: 60
            },
            {
                description: "Create a new disease",
                days: -100,
                money: 50
            },
            {
                description: "Close schools",
                days: -2,
                money: -10
            },
            {
                description: "Build schools",
                days: -3,
                money: -5
            },
            {
                description: "Recycle",
                days: 20,
                money: 10
            },
            {
                description: "Advocate for world peace",
                days: 20,
                money: 10
            },
            {
                description: "Build an animal sanctuary",
                days: 30,
                money: -15
            },
            {
                description: "Do nothing",
                days: -70,
                money: 0
            },
            {
                description: "Ban plastic straws",
                days: 10,
                money: 0
            },
            {
                description: "Make electric vehicles",
                days: 20,
                money: 30
            },
            {
                description: "Push plant based alternatives for food",
                days: 10,
                money: 10
            },
            {
                description: "Invest in green energy",
                days: 60,
                money: 60
            },
            {
                description: "Improve working conditions",
                days: 5,
                money: -5
            },
            {
                description: "Open all borders",
                days: 10,
                money: 30
            },
            {
                description: "Do green farming",
                days: 20,
                money: 20
            },
            {
                description: "Clean the ocean floor",
                days: 20,
                money: 0
            },
            {
                description: "End child labour",
                days: 10,
                money: -30
            },
            {
                description: "Improve healthcare",
                days: 30,
                money: -10
            },
            {
                description: "End free speech",
                days: -40,
                money: 0
            },
            {
                description: "Promote free speech",
                days: 30,
                money: 0
            },
            {
                description: "Push alternative energy",
                days: 40,
                money: -20
            },
            {
                description: "Provide sustainable housing",
                days: 20,
                money: -10
            },
            {
                description: "Build more chemical factories",
                days: -30,
                money: 20
            },
        ]

    export default {
        name: "Cards",
        data: () => ({
            cardInfo: object,
            // daysLeft: 365,
            money: 0,
            control:0,
            gameOver: false,
        }),
        methods: {
            ...mapMutations(["makeChoice", "calcDays","calcCash"]),
            effects(days, money) {
                this.makeChoice();
                this.calcDays(days);
                this.calcCash(money);
                // var randomProperty = function(obj) {
                //     var keys = Object.keys(obj)
                //     return obj[keys[ keys.length * Math.random() << 0]];
                // };
                object = this.cardInfo.splice(0,4);
                // object.sort(() => Math.random() - 0.5);
            },
            animateCards(){
                anime({
                    targets: '.cards',
                    scale:{
                        value: [1,0.9],
                        duration: 1200,
                        easing: 'linear'
                    },
                    loop: true
                });
            }
        },

        mounted() {
            this.animateCards();
            this.endGame();
        },
        updated(){
            this.animateCards();
        }
    }
</script>

<style scoped>
    h2 {
        color: black,
    }
    .cards {
        display: flex;
        justify-content: center;
    }
    .description {
        text-align: center;
    }
</style>