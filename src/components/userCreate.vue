<template>
  <div>
    <form @click.prevent>
      <label>Role</label>
      <input type="text" required v-model="userRole" />
      <label>Name</label>
      <input type="text" required v-model="userName" />
      <label>Chores</label>
      <input type="text" required v-model="choreList" />

      <input type="submit" value="Submit" @click="createUSER" />
    </form>

    <div v-if="showDIV">
      <h1>Name:{{ userName }}</h1>

      <h2>Role: {{ userRole }}</h2>

      <h3>Chores:</h3>

      <div v-for="chore in choreList" :key="chore" :class="chore">
        <p>{{ chore }}</p>

        <span><button @click="updateBtn">Update</button></span>
        <span><button @click="deletebtn(chore)">Delete</button></span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userName: "",
      userRole: "",

      showDIV: false,
      choreList: [],
    };
  },
  methods: {
    createUSER() {
      this.showDIV = true;
    },
    updateBtn() {},
    deletebtn(chore) {
      console.log(chore);

      const removeChore = document.querySelector(`.${chore}`);

      removeChore.remove();
    },
  },
};
</script>

<style></style>
