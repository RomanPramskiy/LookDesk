<script setup>
const props = defineProps({
  open: {
    type: Boolean,
    required: true
  }
})

const emit = defineEmits(['close'])

function closeModal() {
  emit('close')
}
</script>


<template>
    <div class="chatai" v-if="props.open">
        <div class="chatai__inner">
            <div class="chatai-header">
                <button @click="closeModal"><svg width="8" height="14" viewBox="0 0 8 14" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M6.75 0.75C6.75 0.75 0.75001 5.1689 0.75 6.75C0.74999 8.3312 6.75 12.75 6.75 12.75" stroke="#141B34" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
                Dashboard</button>
            </div>
            <div class="chatai-messages">
                <div class="chatai-messages__date">Nov 11</div>
                <div class="massage-right">
                <div class="message__inner">
                    <p>Where can I find the new GDPR compliance rules?</p>
                    <span>10:30</span>
                </div>
                </div>
                <div class="massage-left">
                <div class="message__inner">
                    <p>To request remote work approval, start by reviewing your company’s remote work policy to ensure you meet all eligibility criteria. Then, prepare a short written request to your manager or HR, explaining the reason for your request, the duration, and how you plan to maintain productivity while working remotely. Include any tools or communication methods you’ll use to stay connected. Once submitted, wait for feedback or further instructions from your supervisor.</p>
                    <span>10:30</span>
                </div>
                </div>
                <div class="massage-right">
                <div class="message__inner">
                    <p>Where can I find the new GDPR compliance rules?</p>
                    <span>10:30</span>
                </div>
                </div>
                <div class="massage-left">
                <div class="message__inner">
                    <p>To request remote work approval, start by reviewing your company’s remote work policy to ensure you meet all eligibility criteria. Then, prepare a short written request to your manager or HR, explaining the reason for your request, the duration, and how you plan to maintain productivity while working remotely. Include any tools or communication methods you’ll use to stay connected. Once submitted, wait for feedback or further instructions from your supervisor.</p>
                    <span>10:30</span>
                </div>
                </div>
                <div class="chatai-messages__date chatai-messages__date--today">Today</div>
                <div class="massage-right">
                <div class="message__inner">
                    <p>Where can I find the new GDPR compliance rules?</p>
                    <span>10:30</span>
                </div>
                </div>
            </div>
          <form class="chat__form aichat__form">
            <input type="text" placeholder="Ask a question or search for specific information" class="chat__input">
            <button class="chat__button">Send<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M9.935 3.9917C13.9136 2.63538 15.9028 1.95722 16.9728 3.02718C18.0427 4.09714 17.3646 6.08643 16.0083 10.065L15.0847 12.7743C14.0431 15.8298 13.5222 17.3576 12.6637 17.484C12.4329 17.518 12.194 17.4976 11.9656 17.4243C11.1162 17.1516 10.6672 15.5408 9.76925 12.3192C9.57008 11.6046 9.4705 11.2473 9.24366 10.9743C9.17783 10.8952 9.10483 10.8222 9.02566 10.7563C8.75275 10.5295 8.39541 10.4299 7.68087 10.2308C4.45926 9.33275 2.84845 8.88375 2.57575 8.03439C2.50243 7.80603 2.48197 7.56711 2.51596 7.33629C2.6424 6.47777 4.17016 5.95695 7.22566 4.91532L9.935 3.9917Z" stroke="white" stroke-width="1.5"/></svg></button>
          </form>
            <div class="chatai-feedback">
                <div class="chatai-useful">
                    <h3>Was this answer useful to you?</h3>
                    <div class="chatai-useful__buttons">
                        <button class="chatai-useful__button--yes">Useful</button>
                        <button class="chatai-useful__button--no">Not useful</button>
                    </div>
                </div>
                <div class="chatai__comment">
                    <h4>Your comment will help us improve accuracy and quality.</h4>
                    <input type="text" placeholder="Please enter your answer">
                </div>
                <div class="chatai__warning">Up to 120 characters</div>
            </div>

        </div>
        <div class="chatai__end">
            <button @click="closeModal">End the dialogue</button>
        </div>
    </div>
</template>