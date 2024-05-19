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
        type="email"
        className="inputUser"
        placeholder="User email"
        v-model="userEmail"
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
    <button type="button" @click="sendData()">Відправити</button>
  </form>
  <p>{{ users }}</p>
  <div className="error">{{ error }}</div>
  <div v-for="user in users">
    {{ user.name }}
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: [],
      tytle: "About User",
      userName: "",
      userPass: "",
      userEmail: "",
      error: "",
    };
  },
  methods: {
    insertData(val) {
      this.userName = val;
    },
    sendData() {
      if (this.userName.length < 3) {
        this.error = "Short  or empty name ";
        return;
      } else if (
        this.userEmail.length < 4 ||
        this.userEmail.indexOf("@") == -1
      ) {
        this.error = "Short  email or is apsend @";
        return;
      } else if (this.userPass.length < 2) {
        this.error = "Short  pass";
        return;
      }
      console.log(this.userEmail.indexOf("@"))
      this.error = "";

      this.users.push({
        name: this.userName,
        email: this.userEmail,
        pass: this.userPass,
      });
    },
  },
};
</script>

<style scoped>
.inputUser {
  display: block;
  margin-bottom: 10px;
  background-color: aquamarine;
  width: 500px;
  padding: 5px;
  border: 1px solid silver;
  background: #e3e3e3;
  color: #222;
  border-radius: 3px;
}
.userContainer {
  display: block;
}
button {
  border: 0;
  border-radius: 5px;
  outline: none;
  padding: 10px 15px;
  background: #6cd670;
  cursor: pointer;
  transition: transform 500ms ease;
}
button:hover {
  transform: translateY(-5px);
  background-color: bisque;
}
</style>
