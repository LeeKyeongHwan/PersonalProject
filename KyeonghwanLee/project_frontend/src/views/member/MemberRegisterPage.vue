<template>
  <div align="center">
    <member-register-form @submit="onSubmit" />
  </div>
</template>

<script>
import MemberRegisterForm from "@/components/member/MemberRegisterForm.vue";
import axios from "axios";

export default {
  name: "MemberRegisterPage",
  components: {
    MemberRegisterForm,
  },
  methods: {
    onSubmit(payload) {
      const { userId, password, name, phoneNo, email, address, auth } = payload;
      axios
        .post("http://localhost:7777/vuejpamember/register", {
          userId,
          password,
          name,
          phoneNo,
          email,
          address,
          auth,
        })
        .then(res => {
          alert("등록 성공! - " + res);
          console.log("상품 번호: " + res.data.memberNo.toString());
          /*
                        this.$router.push({
                            name: 'ProductListPage'
                        })
                        */
        })
        .catch(res => {
          alert(res.response.data.message);
        });
    },
  },
};
</script>
