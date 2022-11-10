<template>
  <div>
    <HeaderCont />
    <TitleCont name1="reference" name2="api" />
    <section class="cont__refer">
      <div class="container">
        <div class="refer__inner">
          <h2>CSS</h2>
          <ul class="refer__list">
            <li v-for="refer in refers" :key="refer.num">
              <a href="/">
                <span class="num">{{ refer.num }}</span>
                <span class="name">{{ refer.title }}</span>
                <span class="desc">{{ refer.desc }}</span>
                <span class="star">{{ refer.descStar }}</span>
                <a
                  class="link"
                  :href="`https://developer.mozilla.org/en-US/docs/Web/CSS/${refer.title}`"
                  ><span class="star">보기</span></a
                >
              </a>
            </li>
          </ul>
        </div>
      </div>
    </section>
    <ContactCont />
    <FooterCont />
  </div>
</template>

<script>
import HeaderCont from "@/components/HeaderCont.vue";
import TitleCont from "@/components/TitleCont.vue";
import FooterCont from "@/components/FooterCont.vue";
import ContactCont from "@/components/ContactCont.vue";
import { ref } from "vue";

export default {
  components: {
    HeaderCont,
    TitleCont,
    FooterCont,
    ContactCont,
  },

  setup() {
    const refers = ref([]);

    const reference = () => {
      fetch("https://younghwan12.github.io/reactapi/src/utils/reference.json")
        .then((response) => response.json())
        .then((result) => (refers.value = result.cssRefer))
        // .then((result) => console.log(result.cssRefer))
        .catch((error) => console.log("error", error));
    };
    reference();

    return {
      refers,
      reference,
    };
  },
};
</script>

<style lang="scss">
.refer__inner {
  padding-bottom: 200px;
  h2 {
    font-size: 30px;
    color: var(--black);
  }
}

.refer__list {
  border: 1px solid var(--bg-light-border);
  font-family: var(--font-kor);

  li {
    border-bottom: 1px solid var(--bg-light-border);
    a {
      display: flex;
      align-items: center;
      width: 100%;
      color: var(--black);

      span {
        display: inline-block;
        padding: 15px 20px;
      }

      .num {
        flex: 1 1 6%;
        text-align: center;
      }
      .name {
        flex: 1 1 19%;
        border-right: 1px solid var(--bg-light-border);
        border-left: 1px solid var(--bg-light-border);

        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;

        &:hover {
          white-space: inherit;
          overflow: auto;
          text-overflow: inherit;
        }
      }
      .desc {
        flex: 1 1 65%;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;

        &:hover {
          white-space: inherit;
          overflow: auto;
          text-overflow: inherit;
        }
      }
      .star {
        flex: 1 1 8%;
        text-align: center;
        border-right: 1px solid var(--bg-light-border);
        border-left: 1px solid var(--bg-light-border);
      }
      .link {
        flex: 1 1 7%;
        text-align: center;
      }
    }
  }
}
</style>
