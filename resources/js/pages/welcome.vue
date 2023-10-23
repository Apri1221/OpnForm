<template>
  <div>
    <section class="bg-gradient-to-b relative from-white to-gray-100 py-8 sm:py-16 ">
      <div class="absolute inset-0">
        <img class="w-full h-full object-cover object-top"
             :src="asset('img/pages/ai_form_builder/background-pattern.svg')" alt="">
      </div>

      <div class="px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto relative -mb-32 md:-mb-52 lg:-mb-72">
        <div class="flex justify-center mb-5">
          <div
            class="relative flex items-center shadow-sm bg-white gap-x-4 rounded-full px-4 py-1 text-sm leading-6 text-gray-600 ring-1 ring-gray-900/10 hover:ring-gray-900/20">
            <span class="font-semibold text-gray-500">We're Open-Source</span><span class="h-4 w-px bg-gray-900/10"
                                                                                    aria-hidden="true"></span>
            <a
              target="_blank" class="flex items-center gap-x-1 hover:no-underline" href="https://github.com/jhumanj/opnform">
              <span class="absolute inset-0" aria-hidden="true"></span>
              Star us on GitHub
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                   stroke="currentColor" aria-hidden="true" class="-mr-2 h-5 w-5 text-gray-400">
                <path stroke-linecap="round" stroke-linejoin="round" d="M8.25 4.5l7.5 7.5-7.5 7.5"></path>
              </svg>
            </a></div>
        </div>
        <div class="max-w-4xl mx-auto text-center">
          <h1 class="text-4xl sm:text-5xl lg:text-6xl font-semibold text-gray-900 tracking-tight">
            Build
            <span class="bg-clip-text text-transparent bg-gradient-to-r from-blue-600 to-blue-400">BNI Form</span>
          </h1>
          <p class="mt-4 sm:mt-5 text-base leading-7 sm:text-xl sm:leading-9 font-medium text-gray-500">
            BNI Form by 
            <span class="font-semibold">Maverick</span>!
          </p>

          <div class="mt-8 flex justify-center">
            <v-button v-if="!authenticated" class="mr-1" :to="{ name: 'forms.create.guest' }" :arrow="true">
              Create a form for FREE
            </v-button>
            <v-button v-else class="mr-1" :to="{ name: 'forms.create' }" :arrow="true">
              Create a form for FREE
            </v-button>
          </div>

          <div class="justify-center flex gap-2 mt-10">
            <div class="flex items-center text-gray-400 text-sm">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2"
                   stroke="currentColor" class="w-4 h-4 mr-1 ticks">
                <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5"/>
              </svg>
              <span>Unlimited forms</span>
            </div>
            <div class="flex items-center text-gray-400 text-sm">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2"
                   stroke="currentColor" class="w-4 h-4 mr-1 ticks">
                <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5"/>
              </svg>
              <span>
                  Unlimited fields
                </span>
            </div>
            <div class="flex text-gray-400 text-sm">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2"
                   stroke="currentColor" class="w-4 h-4 mr-1 ticks">
                <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5"/>
              </svg>
              <span>Unlimited responses</span>
            </div>
          </div>
        </div>

        <div
          class="w-full mt-12 relative px-6 mx-auto max-w-4xl sm:px-10 lg:px-0 z-10 flex items-center justify-center">
          <div
            class="-m-2 rounded-xl bg-blue-900/5 p-2 backdrop-blur-sm ring-1 ring-inset ring-blue-900/10 lg:-m-4 lg:rounded-2xl lg:p-4">
            <img :src="asset('img/pages/welcome/product-cover.jpg')"
                 alt="Product screenshot" loading="lazy" class="rounded-md shadow-2xl ring-1 ring-gray-900/10">
          </div>
        </div>
      </div>
    </section>

    <div class="flex flex-col bg-gray-50 dark:bg-notion-dark">
      <div class="bg-white dark:bg-notion-dark-light pt-32 md:pt-52 lg:pt-72 pb-8">
        <div class="md:max-w-5xl md:mx-auto w-full">
          <features class="pb-8"/>
        </div>
      </div>

      <open-form-footer class="dark:border-t border-t"/>

    </div>
  </div>
</template>

<script>
import {mapGetters} from 'vuex'
import Features from '~/components/pages/welcome/Features.vue'
import MoreFeatures from '~/components/pages/welcome/MoreFeatures.vue'
import PricingTable from '../components/pages/pricing/PricingTable.vue'
import AiFeature from '~/components/pages/welcome/AiFeature.vue'
import OpenFormFooter from '../components/pages/OpenFormFooter.vue'
import Testimonials from '../components/pages/welcome/Testimonials.vue'
import TemplatesSlider from '../components/pages/welcome/TemplatesSlider.vue'
import SeoMeta from '../mixins/seo-meta.js'

export default {
  components: {Testimonials, OpenFormFooter, Features, MoreFeatures, PricingTable, AiFeature, TemplatesSlider},

  layout: 'default',

  mixins: [SeoMeta],

  data: () => ({
    title: window.config.appName,
    metaTitle: 'Create beautiful & open-source forms for free',
  }),

  mounted() {
  },

  methods: {
    // openCrisp () {
    //   window.$crisp.push(['do', 'chat:show'])
    //   window.$crisp.push(['do', 'chat:open'])
    //   window.$crisp.push(['do', 'message:send', ['text', "Hi! I'd like to learn more about OpnForm"]])
    // }
  },

  computed: {
    ...mapGetters({
      authenticated: 'auth/check'
    }),
    configLinks: () => window.config.links,
    paidPlansEnabled() {
      return window.config.paid_plans_enabled
    }
  }
}
</script>

<style lang="scss" scoped>

.customer-logo-container {
  max-width: 130px;
  width: 100%;
}

.ticks {
  color: #2563eb;
}

@screen md {
  #macbook-video {
    position: absolute;
    max-width: 84.8% !important;
    right: 0px;
    top: 6.8%;
  }
}
</style>
