<script setup>
import { ref, onMounted } from "vue";
import { nanoid } from "nanoid";
import ImputPass from "./components/ImputPass.vue";
</script>

<template>
  <div class="form-control absolute inset-x-0 bottom-0 m-3">
    <div class="input-group">
      <input
        v-model="imputPass"
        ref="imputPassword"
        type="text"
        placeholder="Enter password..."
        class="input input-bordered w-full"
      />
      <button @click="randomPassword()" class="btn btn-square">
        <span class="material-symbols-rounded bg-transparent"> refresh </span>
      </button>
      <button @click="addPassword()" class="btn btn-square">
        <span class="material-symbols-rounded bg-transparent"> add </span>
      </button>
    </div>
  </div>

  <div
    class="m-3 overflow-y-auto h-screen grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 2xl:grid-cols-6 gap-4"
  >
    <div v-for="(item, index) in itemsPass" :key="item.id">
      <div class="mb-3 p-3 bg-slate-800 bg-opacity-50 rounded-lg">
        <input
          type="text"
          placeholder="Type here"
          class="input w-full my-1"
          :value="item.site"
        />
        <input
          type="text"
          placeholder="Type here"
          class="input w-full my-1"
          :value="item.login"
        />
        <input
          type="text"
          placeholder="Type here"
          class="input w-full my-1"
          :value="item.password"
        />
        <div class="btn-group w-full mt-1">
          <button @click="removePass(index)" class="btn w-1/3">
            <span class="material-symbols-rounded bg-transparent">
              delete
            </span>
          </button>
          <button class="btn w-1/3">
            <span class="material-symbols-rounded bg-transparent"> edit </span>
          </button>
          <button class="btn w-1/3">
            <span class="material-symbols-rounded bg-transparent"> save </span>
          </button>
        </div>
      </div>
    </div>
  </div>

  <!-- :value="randomPass" -->
</template>

<script>
export default {
  setup() {},
  data() {
    return {
      imputPass: "123",
      randomPass: "",
      itemsPass: [
        {
          id: 0,
          site: "vk.com",
          login: "regxxxman",
          password: "hYfmLm4jQqoAcGCXFmg8D",
        },
      ],
    };
  },
  methods: {
    addPassword() {
      // alert(this.itemsPass[0]);
      if (this.itemsPass[0] != null) {
        this.itemsPass.push({
          id: this.itemsPass[this.itemsPass.length - 1].id + 1,
          login: "none",
          password: this.imputPass,
        });
      } else {
        this.itemsPass.push({
          id: 0,
          login: "none",
          password: this.imputPass,
        });
      }
    },
    randomPassword() {
      // let chars =
      //   "0123456789abcdefghijklmnopqrstuvwxyz!@#$%^&*()ABCDEFGHIJKLMNOPQRSTUVWXYZ";

      // this.randomPass = nanoid();
      this.imputPass = nanoid();
    },
    removePass(index) {
      this.itemsPass.splice(index, 1);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "https://fonts.googleapis.com/css2?family=Material+Symbols+Rounded:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200";
.material-symbols-rounded {
  font-variation-settings: "FILL" 0, "wght" 400, "GRAD" 0, "opsz" 48;
}
</style>
