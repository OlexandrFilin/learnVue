<template className="block">
  <div className="userContainer"></div>

  <h1>{{ tytle }}</h1>
  <form>
    <label>
      Name user:
      <input
        id="nameUser"
        type="text"
        className="inputUser"
        placeholder="User name"
        @input="insertData($event.target.value)"
      />
    </label>
    <label>
      Email:
      <input
        type="Email"
        className="inputUser"
        placeholder="User email"
        v-model="ueerEmail"
      />
    </label>
    <label>
      Password:
      <input
        type="password"
        className="inputUser"
        placeholder="User password"
         v-model="userPass"
      />
    </label>
    <button type="button" @click="userName = 'jhon'">Відправити</button>
  </form>
  <!-- <div v-for="">

  </div> -->
</template>

<script>
export default {
  data() {
    return {
      users: [],
      tytle: "About User",
      userName: "",
      userPass: "",
      ueerEmail: "",
    };
  },
  methods: {
    insertData(val) {
       this.userName = val;
    },
    sendData(){
      this.users.push({name:this.userName,
        email: this.userEmail,
        pass: this.userPass
      })
    }
  },
};
</script>

<style scoped>
.inputUser {
  display: block;
  margin-bottom: 10px;
  background-color: aquamarine;
}
.userContainer {
  display: block;
}
button {
  border:0;
  border-radius: 5px;
  outline:none;
  padding: 10px 15px;
}
button:hover {
  transform: translateY(10px);
}
</style>
