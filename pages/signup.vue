<template>
  <div>
    <v-container>
      <v-card>
        <v-subheader>회원가입</v-subheader>
        <v-form ref="form" v-model="valid" @submit.prevent="onSubmitForm">
          <v-container>
            <v-text-field
            v-model="email" 
            label="이메일"
            type="email"
            :rules="emailRules"
            required
            />
            <v-text-field 
              label="비밀번호"
              v-model="password"
              type="password"
              :rules="passwordRules"
              required
            />
            <v-text-field 
              label="비밀번호확인"
              v-model="passwordCheck"
              :rules="passwordCheckRules"
              type="password"
              required
            />
            <v-text-field 
              label="닉네임"
              v-model="nickname"
              :rules="nicknameRules"
              type="nickname"
              required
            />
            <v-checkbox
              v-model="terms" 
              required
              :rules="[v => !!v || '약관에동의해야합니다',]"
              label="동의합니다."
            />
            <v-btn  color="green" type="submit">회원가입</v-btn>
            <v-btn nuxt to="/">취소</v-btn>
          </v-container>
        </v-form>
      </v-card>
    </v-container>  
  </div>     
</template>

<script>
export default {
  data () {
    return {
      valid :false,
      email: '',
      password: '',
      passwordCheck: '',
      nickname: '',
      terms: false,
      emailRules: [
        v => !!v || '이메일은 필수입니다.',
        v => /.+@.+/.test(v) || '이메일이 유효하지 않습니다.',
      ],
      passwordRules: [
        v => !!v || '비밀번호는 필수입니다.',
      ],
      passwordCheckRules: [
        v => !!v || '비밀번호확인은 필수입니다.',
        v => v === this.password || '비밀번호가 일치하지않습니다.'
      ],
      nicknameRules: [
        v => !!v || '닉네임은 필수입니다.',
      ],
    };
  },
  head: {
    title: '회원가입',
  },
  methods: {
    onSubmitForm() {
      if (this.$refs.form.validate()) {
        alert('회원가입시도');
      } else {
        alert ('폼이유효하지않습니다');
      }; 
    }
  },
}
</script>


<style>

</style>