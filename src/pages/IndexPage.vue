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
          <div class="text-h6 text-bold line-28">
            {{ Research.title }}
          </div>
        </q-card-section>

        <q-card-section class="q-py-none">
          <div>
            <span class="text-bold q-mr-xs">Authors</span>
            <span
              v-for="(author, i) of Research.authors"
              :key="author.id"
              class="q-mr-xs"
            >
              <UserReference :user="author" />
              <span v-if="i !== Research.authors.length - 1">,</span>
            </span>
          </div>
        </q-card-section>

        <q-card-section class="">
          <div>
            <span class="text-bold">Editor</span>
            <UserReference :user="Research.editor" class="q-mx-xs" />
          </div>

          <div>
            <span class="text-bold">Yourself</span>
            <UserReference :user="Research.yourself" class="q-mx-xs" />
          </div>
        </q-card-section>

        <q-card-section class="q-py-none">
          <q-expansion-item
            dense
            dense-toggle
            expand-separator
            header-class="text-accent expansion-header"
            label="Affiliations"
          >
            <div>
              <div
                v-for="(affiliation, i) of Research.editor.affiliations"
                :key="affiliation.id"
                class="affiliation-item"
              >
                <span class="list-number">{{ i }}</span> {{ affiliation.name }},
                {{ affiliation.city }},
                {{ affiliation.country }}
              </div>
            </div>
          </q-expansion-item>
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

  .expansion-header {
    width: max-content;
    padding-left: 0;
    transition: all 0.2s ease-in-out;

    i {
      color: $accent;
    }

    &:hover,
    &:focus {
      font-weight: 600;
      transform: scale(1.03);

      .q-focus-helper {
        background: transparent !important;
      }
    }
  }

  .affiliation-item {
    color: $grey-7;
    font-weight: 300;

    .list-number {
      font-weight: 400;
      color: $carbon;
      font-size: 10px;
      bottom: 4px;
      position: relative;
    }
  }
}
</style>
