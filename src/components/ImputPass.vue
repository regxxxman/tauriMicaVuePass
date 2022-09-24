<template>
  <div class="form-control">
    <div class="input-group">
      <input
        placeholder="password"
        class="input input-bordered w-full"
        v-model="value"
      />
      <button class="btn btn-square">
        <span class="material-symbols-rounded bg-transparent">
          visibility
        </span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    value: String,
  },
};
</script>

<style lang="scss" scoped></style>
