<template>
  <div></div>
</template>
<script>
import { tsParticles } from 'tsparticles-engine'
import { loadFull } from 'tsparticles'

function randomIntFromInterval(min, max) {
  // min and max included
  return Math.floor(Math.random() * (max - min + 1) + min)
}

function setCookie() {
  const now = new Date()
  const time = now.getTime()
  const expireTime = time + 1000 * 60 * 60 // 60 seconds * 60 minutes
  now.setTime(expireTime)
  document.cookie = 'cookie=ok;expires=' + now.toUTCString() + ';path=/'
}

export default {
  name: 'Particles',
  async mounted() {
    if (document.cookie) return
    await loadFull(tsParticles)

    // eslint-disable-next-line
    const particles = [...Array(30)].map(function(x, idx) {
      return {
        position: {
          x: (100 / 30) * idx,
          y: 0 + randomIntFromInterval(1, 20) - randomIntFromInterval(10, 20)
        }
      }
    })

    const foods = [
      'Bento box 1.png',
      'Schnitty.png',
      'curry.png',
      'pie.png',
      'street bao.png',
      'Bento box 2.png',
      'Spaghetti.png',
      'dumplings.png',
      'pizza.png',
      'sushi.png',
      'Fried chicken.png',
      'Taco.png',
      'fish and chips.png',
      'rice and sauce.png',
      'wrap.png',
      'Kebab.png',
      'brekky.png',
      'hot dog.png',
      'roll.png',
      'yum cha.png',
      'Ramen.png',
      'burger and chips.png',
      'sandwich.png',
      'Rice.png',
      'burger.png',
      'noodle box.png',
      'steak.png'
    ]

    await tsParticles.load('tsparticles', {
      manualParticles: [...particles],
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
          value: 0,
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
              // eslint-disable-next-line
              ...foods.map((name) => ({
                src: `food-icons/${name}`,
                width: 32,
                height: 32,
                particles: {
                  size: {
                    value: 32
                  }
                }
              }))
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

    setCookie()
  }
}
</script>
