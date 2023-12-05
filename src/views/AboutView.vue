<template>
<div>{{ todos }} llll</div>
<div class="container ">

    <div class="container-fluid mt-5">
        <div class=" col-lg-5 border border-primary  m-5 rounded-5 bg-white">
            <label class="mt-5 ms-3" for="name">name :</label>
            <input type="text" id="name" class="ms-5" v-model="userDetails.nameIs" /> <br />
            <label class="mt-2 ms-3" for="age">age :</label>
            <input type="text" id="age" class="mt-3 ms-5" v-model="userDetails.age" /><br />
            <label for="company">company:</label>
            <input class="mt-2 ms-3" type="text" v-model="userDetails.company" /><br />
            <label class="mt-2 ms-3" for="location">location:</label>
            <input type="text" id="location" class="mt-3 ms-4" v-model="userDetails.location" /> <br />
            <div class="mt-5 mb-5 ms-4">
                <button class="btn  btn-primary" @click="PostApi"> submit</button>
                <button class="btn  btn-danger ms-5"> reset</button>
            </div>
        </div>
    </div>
    <table class=" mt-5">
        <tr>
            <th>ID</th>
            <th>NAME</th>
            <th>AGE</th>
            <th>company</th>
            <th>location</th>
            <th>edit</th>
            <th>Delete</th>
        </tr>
        <tr v-for="todo in todos" v-bind:key="todo.id" class="mt-5">
            <td>{{ todo.id }}</td>
            <td>{{ todo.name }}</td>
            <td>{{ todo.age }}</td>
            <td>{{ todo.company }}</td>
            <td>{{ todo.location }}</td>
            <td><button class="btn btn-primary bg-warning" @click="PutApi(todo.id)">view</button>
                <button class="btn btn-sucess bg-success" @click="updateApi(todo.id)">update</button>
            </td>
            <td><button class="btn btn-primary bg-danger" @click="DeleteApi(todo.id)"> Delete</button></td>
        </tr>
    </table>


</div>
</template>
<script>
import axios from "axios";
const baseUrl = " http://localhost:3000/todo/"
export default {
name: 'App',
data() {
    return {
        userDetails:{
        nameIs: "",
        age: "",
        company: "",
        location: "",
        },
        todos: []
        
    }
},

mounted() {
    this.GetApi();
},

methods: {
    // GET call
    async GetApi() {

        await axios.get(baseUrl).then((resp) => {
            this.todos = resp.data;
            console.log(resp.data);

            
        })
            .catch((error) => {
                console.log(error)
            })
    },

    // post call
    async PostApi() {
        let payload = {
            name: this.userDetails.nameIs,
            age: this.userDetails.age,
            company: this.userDetails.company, 
            location: this.userDetails.location
        }
        await axios.post(baseUrl, payload)
            .then((resp) => {
                console.log(resp.data);
                this.GetApi();
                this.userDetails={};
            })
            .catch((error) => {
                console.log(error)
            })
    },

    // delete call
    async DeleteApi(id) {
        await axios
            .delete(baseUrl+id)
            .then((resp) => {
                console.log(resp)
                this.GetApi();

            })
            .catch((error) => {
                console.log(error)
            })
    },

    // put call (view)
    async PutApi(id) {

await axios.get(baseUrl+id).then((resp) => {
console.log("gggggggggg",resp.data);

    this.userDetails.nameIs = resp.data.name;
this.userDetails.age=resp.data.age;
this.userDetails.company=resp.data.company;
this.userDetails.location=resp.data.location

})
.catch((error) => {
    console.log(error)
})
},
    // put call (update)
    async updateApi(id) {
        console.log(id)
        let payload = {
            name: this.userDetails.nameIs,
            age: this.userDetails.age,
            company: this.userDetails.company, 
            location: this.userDetails.location
        }
        await axios
            .put(baseUrl+id,payload)
            .then((resp) => {
                console.log("kkkkkkkkkk", resp)
                this.GetApi();
                this.userDetails={};

            })
            .catch((error) => {
                console.log(error)
            })
    }
}
}
</script>
<style> table,
th,
td {
 border: 1px solid;
}

table {
 width: 50%;
}

td,
th,
tr {
 text-align: center;
}

.main-layout {

 border: 2px solid black;
 max-width: auto;
}
</style>