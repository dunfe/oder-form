<template>
    <div class="hello">
        <h1>{{ msg }}</h1>
        <h1 class="pt-3">Service</h1>
        <form id="app" v-cloak>
            <ul>
                <li v-for="service in services" v-bind:key="service.id" v-on:click="toggleActive(service)"
                    v-bind:class="{ 'active' : service.active}" class="w-100">
                    {{ service.name}} <span>{{ service.price | currency}}</span>
                </li>
            </ul>
            <div class="total">
                Total : <span>{{ total() | currency }}</span>
            </div>
        </form>
    </div>
</template>
<script>
    export default {
        name: 'HelloWorld',
        props: {
            msg: String
        },
        data: function () {
            return {
                service: '',
                services: [
                    {
                        id: 1,
                        name: 'Sushi',
                        price: 300,
                        active: false
                    },
                    {
                        id: 2,
                        name: 'Steak',
                        price: 500,
                        active: false
                    },
                    {
                        id: 3,
                        name: 'Coca',
                        price: 10,
                        active: false
                    }
                ]
            }
        },
        methods: {
            toggleActive: function (item) {
                item.active = !item.active
            },
            total: function () {
                let total = 0;
                this.services.forEach(function (item) {
                    if (item.active) {
                        total += item.price
                    }
                });
                return total
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    [v-cloak] {
        display: none;
    }

    h3 {
        margin: 40px 0 0;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }

    form {
        background-color: #61a1bc;
        border-radius: 2px;
        box-shadow: 0 1px 1px #ccc;
        width: 400px;
        padding: 35px 60px;
        margin: 50px auto;
    }

    form h1 {
        color: #fff;
        font-size: 64px;
        font-family: 'Cookie', cursive;
        font-weight: normal;
        line-height: 1;
        text-shadow: 0 3px 0 rgba(0, 0, 0, 0.1);
    }

    form ul {
        list-style: none;
        color: #fff;
        font-size: 20px;
        font-weight: bold;
        text-align: left;
        margin: 20px 0 15px;
    }

    form ul li {
        padding: 20px 30px;
        background-color: #e35885;
        margin-bottom: 8px;
        box-shadow: 0 1px 1px rgba(0, 0, 0, 0.1);
        cursor: pointer;
    }

    form ul li span {
        float: right;
    }

    form ul li.active {
        background-color: #8ec16d;
    }

    div.total {
        border-top: 1px solid rgba(255, 255, 255, 0.5);
        padding: 15px 30px;
        font-size: 20px;
        font-weight: bold;
        text-align: left;
        color: #fff;
    }

    div.total span {
        float: right;
    }
</style>
