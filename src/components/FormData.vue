<template>
  <ElCard class="form-card">
    <ElForm :model="formData" :rules="rules">
      <ElFormItem label="Type" prop="type">
        <ElSelect class="type-select" v-model="formData.type" placeholder="Choose type...">
          <ElOption label="Income" value="INCOME"/>
          <ElOption label="Outcome" value="OUTCOME"/>
          
        </ElSelect>
      </ElFormItem>
      <ElFormItem label="Comments" prop="comment">
        <ElInput v-model="formData.comment"/>
      </ElFormItem>
      <ElFormItem label="Value" prop="value">
        <ElInput v-model.number="formData.value"/>
      </ElFormItem>
      <ElButton type="primary" @click="onSubmitForm">Submit</ElButton>
    </ElForm>
  </ElCard>
</template>

<script>
export default {
  name: 'FormData',
  data: () => ({
    formData: {
      type: "INCOME",
      comment: "",
      value: 0,
    },
    rules: {
      type: [
        {required: true, message: 'Please select type', trigger: 'blur',}
      ],
      comment: [
        {required: true, message: 'Please input comment', trigger: 'blur',}
      ],
      value: [
        {required: true, message: 'Please input value', trigger: 'blur',},
        {type: 'number', message: 'Value must be a number', trigger: 'blur',}
      ],
    }
  }),
  methods: {
    onSubmitForm() {

    },
  }

}
</script>

<style scoped>
.form-card {
  max-width: 500px;
  margin: auto;
}

.type-select {
  width: 100%;
}
</style>
