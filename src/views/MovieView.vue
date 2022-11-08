<template>
  <div>
    <HeaderCont />
    <section className="cont__title">
      <div className="container">
        <h1 v-for="title in titles" v-bind:key="title.text">
          {{ title.text }}
        </h1>
      </div>
    </section>
    <TitleCont />
    <ContactCont />
    <FooterCont />
  </div>
</template>

<script>
import HeaderCont from "@/components/HeaderCont.vue";
import TitleCont from "@/components/TitleCont.vue";
import FooterCont from "@/components/FooterCont.vue";
import ContactCont from "@/components/ContactCont.vue";

export default {
  components: {
    HeaderCont,
    TitleCont,
    FooterCont,
    ContactCont,
  },
  data: function () {
    return {
      titles: [{ text: "MOVIE" }, { text: "REFERENCE API" }],
    };
  },
};
</script>
