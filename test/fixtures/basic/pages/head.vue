<script>
export default defineNuxtComponent({
  setup () {
    const a = ref('')
    useHead({
      // title template function example
      titleTemplate: title => `${title} - Title Template Fn Change`,
      bodyAttrs: {
        class: 'body-attrs-test',
      },
      script: [
        {
          src: 'https://a-body-appended-script.com',
          tagPosition: 'bodyClose',
        },
      ],
      meta: [{ name: 'description', content: 'first' }],
    })
    useHead({ meta: [{ charset: 'utf-16' }, { name: 'description', content: computed(() => `${a.value} with an inline useHead call`) }] })
    a.value = 'overriding'
  },
  head () {
    return {
      htmlAttrs: {
        class: 'html-attrs-test',
      },
    }
  },
})
</script>

<template>
  <div>
    <Head>
      <Title>Using a dynamic component</Title>
      <Meta
        http-equiv="content-security-policy"
        content="default-src https"
      />
    </Head>
  </div>
</template>
