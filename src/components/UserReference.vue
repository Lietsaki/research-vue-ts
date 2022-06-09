<template>
  <span
    @mouseenter="openMenu"
    @mouseleave="startCloseTimeout"
    class="user-reference cursor-pointer"
    >{{ user.fullName }}
    <q-menu
      @mouseenter="openMenu"
      @mouseleave="startCloseTimeout"
      v-model="showing"
      class="q-px-md q-pt-md q-pb-sm"
    >
      <div class="user-reference-card">
        <q-card-section class="q-pa-none full-height">
          <div class="flex justify-between full-height">
            <div>
              <div class="text-bold text-subtitle1">{{ user.fullName }}</div>
              <div class="font-size-13">
                <div class="text-grey-7">{{ user.affiliations[0].name }},</div>
                <div class="text-grey-7">
                  {{ user.affiliations[0].city }},
                  {{ user.affiliations[0].country }}
                </div>
              </div>
            </div>

            <div class="user-reference-card__profile-picture">
              <img :src="user.pictureUrl" alt="" />
            </div>

            <div class="flex text-subtitle1 font-size-13">
              <span class="q-mr-md">
                <span class="text-bold text-accent">{{
                  user.publications
                }}</span>
                Publications
              </span>

              <span class="q-mr-md">
                <span class="text-bold text-accent">
                  {{
                    user.views.toLocaleString('en-US', {
                      maximumFractionDigits: 2,
                    })
                  }}</span
                >
                Views
              </span>

              <span>
                <span class="text-bold text-accent">
                  {{
                    user.followers.toLocaleString('en-US', {
                      maximumFractionDigits: 2,
                    })
                  }}</span
                >
                Followers
              </span>
            </div>

            <div class="flex full-width justify-end">
              <q-btn
                flat
                icon="exit_to_app"
                color="accent"
                label="View profile"
                :to="user.profileUrl"
              />
            </div>
          </div>
        </q-card-section>
      </div>
    </q-menu>
  </span>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'UserReference',
  props: {
    user: {
      type: Object,
      required: true,
    },
  },
  components: {},
  data() {
    return {
      showing: false,
      closeTimeoutId: null as null | ReturnType<typeof setTimeout>,
    };
  },
  methods: {
    openMenu() {
      if (this.closeTimeoutId) clearTimeout(this.closeTimeoutId);
      this.showing = true;
    },
    startCloseTimeout() {
      this.closeTimeoutId = setTimeout(() => {
        this.showing = false;
      }, 100);
    },
  },
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
      border: 1px solid $bg;
    }
  }
}
</style>
