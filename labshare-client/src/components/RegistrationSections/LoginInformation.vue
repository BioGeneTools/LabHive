<template>
  <div>
    <h3 class="section" v-if="profileUpdate">{{ $t("registration.steps.loginInformation.title") }}</h3>
    <p class="step-info-sub" v-else>{{ $t("registration.steps.loginInformation.subTitle") }}</p>

    <b-row>
      <b-col sm="*" md="5" lg="4">
        <InputForm
          :name="role === 'volunteer' ? 'general.email' : 'registration.steps.loginInformation.textfieldPlaceholders.officialEmail'"
          v-model="formData.contact.email"
          :valFunc="val.validEmail"
          inType="email"
        ></InputForm>
      </b-col>
      <b-col sm="*" md="5" lg="4">
        <template v-if="!profileUpdate">
          <Password v-model="formData.password"></Password>
        </template>
      </b-col>
    </b-row>
    
    <template v-if="!profileUpdate">
      <NavButtons :disableSubmit="disableSubmit"></NavButtons>
    </template>
  </div>
</template>

<script>
import registrationSection from "@/mixins/registrationSection";
import Password from "@/components/PasswordFields";

export default {
  mixins: [registrationSection],
  components: {
    Password
  }
};
</script>
