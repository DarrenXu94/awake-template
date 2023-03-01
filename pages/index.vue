<template>
  <div id="home-page" class="page-wrapper home-page">
    <div id="tsparticles"></div>

    <site-hero :title="title" :subtitle="subtitle" :image="featureImage">
    </site-hero>
    <main-section theme="one-column">
      <template v-slot:default>
        <posts-grid />
      </template>
      <template v-slot:sidebar>
        Nothing here
      </template>
    </main-section>
    <news-letter-form-modal />
  </div>
</template>

<script>
// import ConfettiGenerator from 'confetti-js'
import { mapState } from 'vuex'
import { tsParticles } from 'tsparticles-engine'
import { loadFull } from 'tsparticles'

import { setPageData } from '../helper'
import NewsLetterFormModal from '~/components/NewsLetterFormModal'

export default {
  name: 'HomePage',
  head() {
    return {
      title: `Home | ${this.$siteConfig.siteName}`
    }
  },
  components: {
    NewsLetterFormModal
  },

  computed: {
    ...mapState(['title', 'subtitle', 'featureImage'])
  },
  fetch({ store, params }) {
    setPageData(store, { slug: 'home' })
  },
  async mounted() {
    await loadFull(tsParticles)

    await tsParticles.load('tsparticles', {
      particles: {
        color: {
          value: ['#FFFFFF', '#FFd700']
        },
        move: {
          direction: 'bottom',
          enable: true,
          gravity: {
            enable: true,
            acceleration: 1.5
          },
          outModes: {
            default: 'destroy',
            bottom: 'destroy',
            left: 'destroy',
            right: 'destroy',
            top: 'none'
          },
          size: true,
          speed: {
            min: 1,
            max: 2
          }
        },
        number: {
          value: 30,
          density: {
            enable: true,
            area: 800
          }
        },
        opacity: {
          value: 1,
          animation: {
            enable: false,
            startValue: 'max',
            destroy: 'min',
            speed: 0.3,
            sync: true
          }
        },
        rotate: {
          value: {
            min: 0,
            max: 360
          },
          direction: 'random',
          move: true,
          animation: {
            enable: true,
            speed: 60
          }
        },
        tilt: {
          direction: 'random',
          enable: true,
          move: true,
          value: {
            min: 0,
            max: 360
          },
          animation: {
            enable: true,
            speed: 60
          }
        },
        shape: {
          type: ['image'],
          options: {
            image: [
              {
                src: 'burger.svg',
                width: 32,
                height: 32,
                particles: {
                  size: {
                    value: 32
                  }
                }
              },
              {
                src: 'hotdog.svg',
                width: 32,
                height: 32,
                particles: {
                  size: {
                    value: 32
                  }
                }
              },
              {
                src: 'pizza.svg',
                width: 32,
                height: 32,
                particles: {
                  size: {
                    value: 32
                  }
                }
              },
              {
                src: 'eggplant.svg',
                width: 32,
                height: 32,
                particles: {
                  size: {
                    value: 32
                  }
                }
              },
              {
                src: 'icecream.svg',
                width: 32,
                height: 32,
                particles: {
                  size: {
                    value: 32
                  }
                }
              },
              {
                src: 'donut.svg',
                width: 32,
                height: 32,
                particles: {
                  size: {
                    value: 32
                  }
                }
              },
              {
                src: 'sushi.svg',
                width: 32,
                height: 32,
                particles: {
                  size: {
                    value: 32
                  }
                }
              },
              {
                src: 'pan.svg',
                width: 32,
                height: 32,
                particles: {
                  size: {
                    value: 32
                  }
                }
              }
            ]
          }
        },
        size: {
          value: {
            min: 2,
            max: 4
          }
        },
        roll: {
          darken: {
            enable: true,
            value: 30
          },
          enlighten: {
            enable: true,
            value: 30
          },
          enable: true,
          speed: {
            min: 15,
            max: 25
          }
        },
        wobble: {
          distance: 30,
          enable: true,
          move: true,
          speed: {
            min: -15,
            max: 15
          }
        }
      }
    })
  }
}
</script>

<style>
.home-page .under-subtitle {
  border-top: none;
  position: relative;
}

/* #my-canvas {
  position: absolute;
  z-index: 1;
} */

#tsparticles {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  z-index: 1;

  /* z-index: -1; */
}
</style>
