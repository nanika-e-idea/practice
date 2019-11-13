<template>
    <section class="container">
        <h1>{{title}}</h1>
        <p>{{message}}</p>
        <div>
            <input type="text" v-model="msg" />
            <button @click="doClick" >Click</button>
        </div>
        <table>
            <tr>
                <th>User ID</th>
                <td>{{json_data.userId}}</td>
            </tr>
            <tr>
                <th>ID</th>
                <td>{{json_data.id}}</td>
            </tr>
            <tr>
                <th>Title</th>
                <td>{{json_data.title}}</td>
            </tr>
            <tr>
                <th>Body</th>
                <td>{{json_data.body}}</td>
            </tr>
        </table>
    </section>
</template>

<script>
const axios = require('axios');

let url = "https://jsonplaceholder.typicode.com/posts/";
 
export default {
    data: function(){
        return {
            title: 'Axios',
            msg: '',
            message: 'axios sample',
            json_data: {},
        };
    },
    methods: {
        doClick: function(event) {
            axios.get(url + this.msg).then((res) => {
                this.message = 'get ID=' + this.msg;
                this.json_data = res.data;
            });
        },
    },
}
</script>