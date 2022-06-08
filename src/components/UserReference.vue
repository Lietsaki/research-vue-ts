<template>
  <span class="user-reference cursor-pointer"
    >Johnny

    <q-tooltip
      anchor="top middle"
      self="bottom middle"
      :offset="[10, 10]"
      transition-show="scale"
      transition-hide="scale"
      class="bg-white shadow-3"
      v-model="tooltip"
    >
      <div class="user-reference-card">
        <q-card-section class="">
          <div class="flex justify-between">
            <div>
              <div class="text-bold text-subtitle1">Johnny Sfondi</div>
              <div class="text-grey-7">Realmo,</div>
              <div class="text-grey-7">Swartzville, United Arab Emirates</div>
            </div>
            <div class="user-reference-card__profile-picture">
              <img
                src="https://loop.frontiersin.org/images/profile/11954/74"
                alt=""
              />
            </div>
          </div>
        </q-card-section>
      </div>
    </q-tooltip>
  </span>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'UserReference',
  components: {},
  data() {
    return { tooltip: true };
  },
  methods: {},
});
</script>

<style lang="scss">
.user-reference {
  text-decoration: underline;
}

.user-reference-card {
  background-color: white;
  color: $carbon;
  width: 385px;
  height: 162px;
  padding: 0;
  z-index: 9001;
  position: relative;

  &__profile-picture {
    img {
      width: 56px;
      height: 56px;
      border-radius: 100%;
    }
  }
}
</style>
