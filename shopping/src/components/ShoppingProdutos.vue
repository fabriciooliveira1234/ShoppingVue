<template>
    <div>
        <h1>{{ msg }}</h1>
        <p>Quantidade: {{ productsCount }}</p>

        <table>
            <thead>
                <tr>
                    <th>#</th>
                    <th>Produto</th>
                    <th>Quant.</th>
                    <th>Total</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="product in products" :key="product.id">
                    <td>{{product.id}}</td>
                    <td>{{product.nome}}</td>
                    <td class="center">
                        <button @click="product.quant--">-</button>
                        <input class="cell-center" min="0" type="number"
                        v-model="product.quant"/>
                        <button @click="product.quant++">+</button>
                    </td>
                    <td>{{ total(product) }}</td>
                </tr>

            </tbody>
        </table>
        <p>total: {{ productsTotal}}</p>
    </div>
</template>

<script>
   export default {
        name: 'ShoppingProdutos',
        props: {
            msg: String
        },
        data(){
            return{
                products: [
                    { id: 1, nome: 'Sapato', quant: 10, price: 185.90 },
                    { id: 2, nome: 'Camisa', quant: 10, price: 98.90 },
                    { id: 3, nome: 'Boné', quant: 10, price: 49.90 },
                    { id: 4, nome: 'Shorts', quant: 10, price: 129.90 },
                    { id: 5, nome: 'Oculos', quant: 10, price: 99.90 }
                ]
            }
        },
        methods: {
            total(product){
                return(product.price * product.quant).toFixed(2)
            }
        },
        computed:{
            productsCount(){
                return this.products
                .map(product => product.quant)
                .reduce((pv, cv) => pv += cv)
            },
            productsTotal() {
                return this.products
                .map(product => product.quant * product.price)
                .reduce((pv, cv) => pv += cv ).toFixed(2)
            }
        }
    }
</script>

<style scoped>
    .center{
        text-align: center;
    }

    .cell-center{
        max-width: 30px;
        display: inline-block;
    }

    h3{
        margin: 40px 0 0;
    }

    th, td{
        border-top: 1px solid lightgray;
        padding: 5px 10px;
    }

    a{
        color: palevioletred;
    }
    
</style>