<template>
  <div class="container">
    <global-header :user="currentUser"></global-header>
    <!--    <column-list :list="list"></column-list>-->
    <validate-form @form-submit="onFormSubmit">
      <div class="mb-3">
        <label class="form-label">邮箱地址</label>
        <validate-input :rules="emailRules" v-model="emailVal"
                        placeholder="请输入邮箱地址"
                        type="text"></validate-input>
      </div>
      <div class="mb-3">
        <label class="form-label">密码</label>
        <validate-input :rules="passwordRules" v-model="passwordVal"
                        placeholder="请输入密码"
                        type="password"></validate-input>
      </div>
      <template #submit>
        <span class="btn btn-danger">Submit</span>
      </template>
    </validate-form>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import 'bootstrap/dist/css/bootstrap.min.css';
import ColumnList, { ColumnProps } from '@/components/ColumnList.vue';
import GlobalHeader, { UserProps } from '@/components/GlobalHeader.vue';
import ValidateInput, { RulesProp } from '@/components/ValidateInput.vue';
import ValidateForm from '@/components/ValidateForm.vue';

const currentUser: UserProps = {
  isLogin: true,
  name: 'Tom'
};

const testData: ColumnProps[] = [
  {
    id: 1,
    title: 'test1的专栏',
    description: '这是test1的专栏，有一段非常有意思的简介，这就是简介。'
    // avatar: 'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=3547703274,3363083080&fm=11&gp=0.jpg'
  },
  {
    id: 2,
    title: 'test2的专栏',
    description: '这是test2的专栏，有一段非常有意思的简介，这就是简介。',
    avatar: 'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=3547703274,3363083080&fm=11&gp=0.jpg'
  },
  {
    id: 3,
    title: 'test2的专栏',
    description: '这是test2的专栏，有一段非常有意思的简介，这就是简介。',
    avatar: 'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=3547703274,3363083080&fm=11&gp=0.jpg'
  },
  {
    id: 4,
    title: 'test2的专栏',
    description: '这是test2的专栏，有一段非常有意思的简介，这就是简介。',
    avatar: 'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=3547703274,3363083080&fm=11&gp=0.jpg'
  }
];

export default defineComponent({
  name: 'App',
  components: {
    ColumnList,
    GlobalHeader,
    ValidateInput,
    ValidateForm
  },
  setup() {
    const emailVal = ref('123@test.com');
    const emailRules: RulesProp = [
      { type: 'required', message: '电子邮箱地址不能为空' },
      { type: 'email', message: '请输入正确的电子邮箱格式' }
    ];
    const passwordVal = ref('123');
    const passwordRules: RulesProp = [
      { type: 'required', message: '密码不能为空' }
    ];
    const onFormSubmit = (result: boolean) => {
      console.log('1234', result);
    };
    return {
      list: testData,
      currentUser,
      emailVal,
      emailRules,
      passwordVal,
      passwordRules,
      onFormSubmit
    };
  }
});
</script>

<style>
</style>
