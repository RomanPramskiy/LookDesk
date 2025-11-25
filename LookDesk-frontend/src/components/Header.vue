<script setup>
import { ref, onMounted, nextTick, onBeforeUnmount } from 'vue'

const isChatOpen = ref(false)

const closeChat = () => {
  isChatOpen.value = false
}

const onOverlayClick = () => {
  isChatOpen.value = false
}

const updateLineForLink = (link) => {
  if (!link) return
  const nav = link.parentElement
  nav.style.setProperty('--underline-left', link.offsetLeft + 'px')
  nav.style.setProperty('--underline-width', link.offsetWidth + 'px')
}

const onNavMouseover = (e) => {
  const link = e.target.closest('a')
  if (!link) return
  updateLineForLink(link)
}

const onNavMouseleave = (e) => {
  const nav = e.currentTarget
  const active = nav.querySelector('a.active') || nav.querySelector('a')
  updateLineForLink(active)
}

const onResize = (e) => {
  const nav = document.querySelector('.header__nav')
  if (!nav) return
  const active = nav.querySelector('a.active') || nav.querySelector('a')
  updateLineForLink(active)
}

onMounted(async () => {
  await nextTick()
  const nav = document.querySelector('.header__nav')
  if (!nav) return
  const active = nav.querySelector('a.active') || nav.querySelector('a')
  updateLineForLink(active)

  window.addEventListener('resize', onResize)
})

onBeforeUnmount(() => {
  window.removeEventListener('resize', onResize)
})


const isModalOpen = ref(false)

const toggleModal = () => {
  isModalOpen.value = !isModalOpen.value
}
</script>

<template>
    <header class="header" :class="{ active: isChatOpen }">
        <div class="container">
            <div class="header__inner">
                <div class="header__logo">
                    <a href="/">LookDesk.ai</a>
                </div>
                <nav class="header__nav" @mouseover="onNavMouseover" @mouseleave="onNavMouseleave">
                    <a href="/" class="active">Dashboard</a>
                    <a href="/">Documents</a>
                    <a href="/">Users</a>
                    <a href="/">Belings</a>
                </nav>
                <div class="header__actions">
                  <div class="header__language">
                    <button @click="toggleModal"><svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M9.99996 1.04187C5.05996 1.04187 1.04163 5.06104 1.04163 10.0002C1.04163 14.9394 5.05996 18.9585 9.99996 18.9585C14.94 18.9585 18.9583 14.9394 18.9583 10.0002C18.9583 5.06104 14.94 1.04187 9.99996 1.04187ZM17.6766 9.3752H14.3016C14.1924 7.08937 13.4891 4.76021 12.2725 2.63438C15.225 3.54771 17.4191 6.19187 17.6766 9.3752ZM10.6083 2.32269C12.0716 4.49853 12.9241 6.96687 13.0516 9.3752H6.9483C7.07497 6.96687 7.92828 4.49853 9.39162 2.32269C9.59328 2.30686 9.79496 2.29187 9.99996 2.29187C10.205 2.29187 10.4075 2.30686 10.6083 2.32269ZM7.72747 2.63438C6.5108 4.76021 5.80747 7.08937 5.6983 9.3752H2.32329C2.58079 6.19187 4.77497 3.54771 7.72747 2.63438ZM2.32329 10.6252H5.6983C5.80747 12.911 6.5108 15.2402 7.72747 17.366C4.77497 16.4527 2.58079 13.8085 2.32329 10.6252ZM9.39162 17.6777C7.92828 15.5019 7.0758 13.0335 6.9483 10.6252H13.0516C12.9249 13.0335 12.0716 15.5019 10.6083 17.6777C10.4066 17.6935 10.205 17.7085 9.99996 17.7085C9.79496 17.7085 9.59245 17.6935 9.39162 17.6777ZM12.2725 17.366C13.4891 15.2402 14.1924 12.911 14.3016 10.6252H17.6766C17.4191 13.8085 15.225 16.4527 12.2725 17.366Z" fill="#110E12"/></svg>
                    </button>
                    <div class="modal__language" v-show="isModalOpen">
                      <div class="modal__language__inner">
                        <div class="modal__language-item active">En</div>
                        <div class="modal__language-item">DE</div>
                      </div>
                    </div>
                  </div>
                    <button @click="isChatOpen = true"><svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M14.1666 11.5037C14.1666 11.2157 14.1666 11.0717 14.21 10.9433C14.336 10.5703 14.6681 10.4257 15.0009 10.2741C15.375 10.1037 15.562 10.0185 15.7473 10.0035C15.9577 9.98649 16.1685 10.0318 16.3483 10.1327C16.5867 10.2665 16.753 10.5207 16.9232 10.7275C17.7093 11.6823 18.1024 12.1598 18.2462 12.6863C18.3623 13.1112 18.3623 13.5555 18.2462 13.9803C18.0365 14.7482 17.3737 15.392 16.8831 15.9878C16.6322 16.2926 16.5067 16.445 16.3483 16.5339C16.1685 16.6348 15.9577 16.6802 15.7473 16.6632C15.562 16.6482 15.375 16.563 15.0009 16.3926C14.6681 16.241 14.336 16.0963 14.21 15.7233C14.1666 15.595 14.1666 15.451 14.1666 15.1629V11.5037Z" stroke="#110E12" stroke-width="1.5"/>
                            <path d="M7.91663 17.5C9.06721 18.6111 10.9327 18.6111 12.0833 17.5" stroke="#110E12" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                            <path d="M5.83329 11.5037C5.83329 11.1411 5.82311 10.8151 5.52988 10.5601C5.42323 10.4674 5.28183 10.403 4.99905 10.2741C4.62497 10.1038 4.43793 10.0186 4.25259 10.0036C3.69655 9.95864 3.39739 10.3381 3.07673 10.7276C2.29058 11.6824 1.89751 12.1598 1.75368 12.6863C1.63761 13.1111 1.63761 13.5555 1.75368 13.9803C1.96346 14.7482 2.62623 15.3918 3.1168 15.9876C3.42603 16.3632 3.72143 16.706 4.25259 16.663C4.43793 16.648 4.62497 16.5628 4.99905 16.3924C5.28183 16.2636 5.42323 16.1992 5.52988 16.1065C5.82311 15.8515 5.83329 15.5256 5.83329 15.1628V11.5037Z" stroke="#110E12" stroke-width="1.5"/>
                            <path d="M1.66663 13.3334V10.0001C1.66663 5.39771 5.39758 1.66675 9.99996 1.66675C14.6023 1.66675 18.3333 5.39771 18.3333 10.0001L18.3334 13.3334" stroke="#110E12" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
                    </button>
                    <button><svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M15.8333 14.9998V7.91646C15.8333 4.69481 13.2216 2.08313 9.99996 2.08313C6.7783 2.08313 4.16663 4.69481 4.16663 7.91646V14.9998" stroke="#110E12" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                            <path d="M17.0833 15H2.91663" stroke="#110E12" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                            <path d="M11.25 16.6669C11.25 17.3572 10.6903 17.9169 10 17.9169M10 17.9169C9.30967 17.9169 8.75 17.3572 8.75 16.6669M10 17.9169V16.6669" stroke="#110E12" stroke-width="1.5" stroke-linejoin="round"/></svg>
                            <div class="notifications__circle"></div>
                    </button>
                    <button class="actions__profile"></button>
                    <button class="burger-menu" @click="$emit('toggleSidebar')">
                      <span></span>
                      <span></span>
                      <span></span>
                    </button>
                </div>
            </div>
        </div>
    </header>




    <div class="overlay" @click="onOverlayClick" v-if="isChatOpen">
      <div class="chat" @click.stop>
        <div class="chat__inner">
          <div class="chat__header"><button @click="closeChat"><svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M16.6655 16.6668L3.3335 3.3335M3.33492 16.6668L16.6668 3.3335" stroke="#110E12" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/></svg></button></div>
          <h3><svg width="20" height="27" viewBox="0 0 20 27" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M14.1665 17.6287C14.1665 17.3407 14.1665 17.1967 14.2098 17.0683C14.3358 16.6953 14.668 16.5507 15.0008 16.3991C15.3748 16.2287 15.5618 16.1435 15.7472 16.1285C15.9576 16.1115 16.1683 16.1568 16.3482 16.2577C16.5866 16.3915 16.7528 16.6457 16.9231 16.8525C17.7092 17.8073 18.1023 18.2848 18.2461 18.8113C18.3622 19.2362 18.3622 19.6805 18.2461 20.1053C18.0363 20.8732 17.3736 21.517 16.883 22.1128C16.6321 22.4176 16.5066 22.57 16.3482 22.6589C16.1683 22.7598 15.9576 22.8052 15.7472 22.7882C15.5618 22.7732 15.3748 22.688 15.0008 22.5176C14.668 22.366 14.3358 22.2213 14.2098 21.8483C14.1665 21.72 14.1665 21.576 14.1665 21.2879V17.6287Z" stroke="#110E12" stroke-width="1.5"/><path d="M7.9165 23.625C9.06709 24.7361 10.9326 24.7361 12.0832 23.625" stroke="#110E12" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/><path d="M5.66667 17.6287C5.66667 17.2661 5.65648 16.9401 5.36326 16.6851C5.25661 16.5924 5.11521 16.528 4.83242 16.3991C4.45834 16.2288 4.2713 16.1436 4.08597 16.1286C3.52992 16.0836 3.23077 16.4631 2.91011 16.8526C2.12396 17.8074 1.73088 18.2848 1.58705 18.8113C1.47098 19.2361 1.47098 19.6805 1.58705 20.1053C1.79683 20.8732 2.4596 21.5168 2.95018 22.1126C3.25941 22.4882 3.55481 22.831 4.08597 22.788C4.2713 22.773 4.45834 22.6878 4.83242 22.5174C5.11521 22.3886 5.25661 22.3242 5.36326 22.2315C5.65648 21.9765 5.66667 21.6506 5.66667 21.2878V17.6287Z" stroke="#110E12" stroke-width="1.5"/><path d="M1.6665 19.4582V16.1248C1.6665 11.5225 5.39746 7.7915 9.99984 7.7915C14.6022 7.7915 18.3332 11.5225 18.3332 16.1248L18.3333 19.4582" stroke="#110E12" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
            Chat with Real Agent
          </h3>
          <p>Response will be provided within 12 business hours</p>
          <div class="chat__box">
            <div class="massage-left">
              <div class="message__inner">
                <p>Torem ipsum dolor sit amet, consectetur adipiscing elit. Nunc vulputate libero et velit interdum, ac aliquet odio mattis.</p>
                <span>10:30</span>
              </div>
            </div>
            <div class="massage-right">
              <div class="message__inner">
                <p>Torem ipsum dolor sit amet, consectetur adipiscing elit. Nunc vulputate libero et velit interdum, ac aliquet odio mattis.</p>
                <span>10:30</span>
              </div>
            </div>
            <div class="massage-left">
              <div class="message__inner">
                <p>Torem ipsum dolor sit amet, consectetur adipiscing elit. Nunc vulputate libero et velit interdum, ac aliquet odio mattis.</p>
                <span>10:30</span>
              </div>
            </div>
            <div class="massage-right">
              <div class="message__inner">
                <p>Torem ipsum dolor sit amet, consectetur adipiscing elit. Nunc vulputate libero et velit interdum, ac aliquet odio mattis.</p>
                <span>10:30</span>
              </div>
            </div>
          </div>
          <form class="chat__form">
            <input type="text" placeholder="Write your text" class="chat__input">
            <button class="chat__button">Send<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M9.935 3.9917C13.9136 2.63538 15.9028 1.95722 16.9728 3.02718C18.0427 4.09714 17.3646 6.08643 16.0083 10.065L15.0847 12.7743C14.0431 15.8298 13.5222 17.3576 12.6637 17.484C12.4329 17.518 12.194 17.4976 11.9656 17.4243C11.1162 17.1516 10.6672 15.5408 9.76925 12.3192C9.57008 11.6046 9.4705 11.2473 9.24366 10.9743C9.17783 10.8952 9.10483 10.8222 9.02566 10.7563C8.75275 10.5295 8.39541 10.4299 7.68087 10.2308C4.45926 9.33275 2.84845 8.88375 2.57575 8.03439C2.50243 7.80603 2.48197 7.56711 2.51596 7.33629C2.6424 6.47777 4.17016 5.95695 7.22566 4.91532L9.935 3.9917Z" stroke="white" stroke-width="1.5"/>
  </svg></button>
          </form>
        </div>
      </div>
    </div>
</template>