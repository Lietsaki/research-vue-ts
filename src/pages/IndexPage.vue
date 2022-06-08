<template>
  <div class="participate">
    <div class="participate-area">
      <div class="participate-area__icon">
        <q-icon name="description" size="xl" />
        <q-icon name="check_circle" size="sm" class="check-circle"></q-icon>
      </div>
      <div
        class="participate-area__title text-h6 text-bold q-my-md text-center"
      >
        Thank you for considering participating to this paper
      </div>

      <q-card class="participate-card">
        <q-card-section class="q-pb-sm">
          <div class="text-grey-7">{{ Research.type }}</div>
          <div class="text-h6 text-bold">
            {{ Research.title }}
          </div>
        </q-card-section>

        <q-card-section class="q-py-none">
          <div>
            <span class="text-bold">Authors</span>
            <span
              v-for="author of Research.authors"
              :key="author.id"
              class="q-mx-xs"
            >
              <span class="user-reference cursor-pointer">
                {{ author.fullName }}
              </span>
              ,
            </span>
          </div>
        </q-card-section>

        <q-card-section class="">
          <div>
            <span class="text-bold">Editor</span>
            <span class="user-reference cursor-pointer q-mx-xs">
              {{ Research.editor.fullName }}
            </span>
          </div>

          <div>
            <span class="text-bold">Yourself</span>
            <!-- <span class="user-reference cursor-pointer q-mx-xs">
              {{ Research.yourself.fullName }}
            </span> -->
            <UserReference class="q-mx-xs" />
          </div>
        </q-card-section>

        <q-card-section class="text-bold">
          <div>{{ Research.journal }} | {{ Research.section }}</div>
        </q-card-section>
      </q-card>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Research from 'src/store/research.json';
import UserReference from 'src/components/UserReference.vue';

export default defineComponent({
  name: 'ParticipationSubmitCard',
  components: { UserReference },
  data() {
    return { Research };
  },
  methods: {},
  mounted() {
    console.log(Research);
  },
});
</script>

<style lang="scss">
.participate {
  height: calc(100vh - var(--header-height));
  background-color: $bg;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.participate-area {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 660px;

  @media screen and (max-width: 660px) {
    width: 90%;
  }

  &__icon {
    color: $carbon;

    .check-circle {
      position: relative;
      color: $positive;
      border-radius: 100%;
      background-color: $bg;
      top: 15px;
      right: 18px;
    }
  }
}

.participate-card {
  width: 99%;
  display: flex;
  flex-direction: column;
}
</style>
