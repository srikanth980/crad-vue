<template>
  <div class="container m-5">
    {{ students }}
    <form>
      NAME : <input type="text" v-model="userDetails.name" placeholder="enter name" /> <br />
      COLLEGE :
      <input type="text" v-model="userDetails.college" placeholder="enter  collge" /><br />
      ADDDRESS : <input type="text" v-model="userDetails.address" placeholder="enter address" />
      <button class="btn  btn-primary" @click="PostApi()"> submit</button>
    </form>
  </div>
  <div class="container bg-secondary mt-5">
    <h2>hello worldanpp</h2>
    <table>
      <tr>
        <th>ID</th>
        <th>NAME</th>
        <th>COLLEGE</th>
        <th>ADDRES3S</th>
        <th>VIEW</th>
        <th>UPDATE</th>
        <th>DELETE</th>
      </tr>
      <tr v-for="student in students" v-bind:key="student.id">
        <td>{{ student.id }}</td>
        <td>{{ student.name }}</td>
        <td>{{ student.college }}</td>
        <td>{{ student.address }}</td>

        <td><button class="btn btn-primary bg-warning" @click="PutApi(student.id)">view</button></td>
        <td>
          <button class="btn btn-sucess bg-success" @click="updateApi(student.id)">update</button>
        </td>
        <td>
          <button class="btn btn-primary bg-danger" @click="DeleteApi(student.id)">Delete</button>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
import axios from 'axios'
const baseUrl = 'http://localhost:3000/students/'
export default {
  data() {
    return {
      userDetails: {
        name: '',
        college: '',
        address: ''
      },
      students: []
    }
  },
  mounted() {
    this.GetApi()
  },
  methods: {
    // get call
    async GetApi() {
      axios
        .get(baseUrl)
        .then((resp) => {
          this.students = resp.data
        })
        .catch((err) => {
          console.log(err)
        })
    },
/// post api (create)
    async PostApi() {
      let payload = {
        name: this.userDetails.name,
        collge: this.userDetails.college,
        address: this.userDetails.address
      }
      axios
        .post(baseUrl, payload)
        .then((resp) => {
          resp.data
          this.GetApi()
        })
        .catch((err) => {
          console.log(err)
        })
    },

    // DELETE CALL
    async  DeleteApi(id){
     axios.delete(baseUrl+id).then((resp) => {
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

    this.userDetails.name = resp.data.name;
this.userDetails.college=resp.data.college;
this.userDetails.address=resp.data.address;


})
.catch((error) => {
    console.log(error)
})
},
// update call
   async updateApi(id){
      let payload = {
        name: this.userDetails.name,
        collge: this.userDetails.name,
        address: this.userDetails.address
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

<style>
table,
th,
td {
  border: 1px solid black;
  border-collapse: collapse;
}
table {
  border-collapse: collapse;
  width: 100%;
  border: 1px solid #ddd;
}
</style>
