<template>
  <div>
    <form @click.prevent>
      <label>Role</label>
      <input type="text" required v-model="userRole" class="role" />
      <label>Name</label>
      <input type="text" required v-model="userName" class="name" />
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

        <span><button @click="updateBtn(chore)">Update</button></span>
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
      textBox: 0,
      showDIV: false,
      choreList: [],
    };
  },
  methods: {
    createUSER() {
      this.showDIV = true;
      const ROLE = document.querySelector(".role");
      ROLE.value = "";

      const NAME = document.querySelector(".name");
      NAME.value = "";
    },

    updateBtn(chore) {
      this.textBox = 1;
      console.log("HERE");
      console.log(this.textBox);
      if (this.textBox == 1) {
        this.textBox = 0;
        const userText = document.createElement("input");
        const submitText = document.createElement("button");
        submitText.textContent = "Click me to update the chore";
        const updateChore = document.querySelector(`.${chore}`);
        updateChore.appendChild(userText);
        updateChore.append(submitText);
        console.log(updateChore);
        const text = updateChore.querySelector("p");
        console.log(text.textContent);
        submitText.addEventListener("click", (e) => {
          console.log("IN HERE");
          console.log(userText.value);
          text.textContent = userText.value;
          userText.remove();
          submitText.remove();
        });
      }

      // text.textContent =
      //  updateChore.textContent= userText
    },
    deletebtn(chore) {
      console.log(chore);

      const removeChore = document.querySelector(`.${chore}`);

      removeChore.remove();
    },
  },
};
</script>

<style></style>
