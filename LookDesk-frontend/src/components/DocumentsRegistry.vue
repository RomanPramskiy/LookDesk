<script setup>
import { ref} from 'vue'
import Pagination from './Pagination.vue';
const page = ref(1);



const isExportOpen = ref(false);
const openRow = ref(null)

function toggleRow(id) {
  openRow.value = openRow.value === id ? null : id
}

const toggleExport = () => {
  isExportOpen.value = !isExportOpen.value
}
const closeOnOutside = (e) => {
  if (!e.target.closest('.export') && isExportOpen.value) {
    isExportOpen.value = false
  }
}


const rows = ref([
  {
    id: 1,
    name: "Manual on the organization of inte...",
    author: "Lindsey Saris",
    date: "2025-11-09",
    category: "Policy",
    favorite: false
  },
  {
    id: 2,
    name: "Incident Reporting Procedure",
    author: "Kaiya Carder",
    date: "2025-11-09",
    category: "Instruction",
    favorite: false
  },
    {
    id: 3,
    name: "Cybersecurity Awareness Guide",
    author: "Justin George",
    date: "2025-11-09",
    category: "Policy",
    favorite: false
  },
    {
    id: 4,
    name: "Data Privacy & Security Policy",
    author: "Lydia Passaquindici",
    date: "2025-11-09",
    category: "Order",
    favorite: false
  },
    {
    id: 5,
    name: "IT Security Policy",
    author: "Emerson Siphron",
    date: "2025-11-09",
    category: "none",
    favorite: false
  },
    {
    id: 6,
    name: "Equal Employment Opportunity Po...",
    author: "Allison Septimus",
    date: "2025-11-09",
    category: "Training",
    favorite: false
  },
    {
    id: 7,
    name: "Data Backup & Recovery Procedure",
    author: "Kaiya George",
    date: "2025-11-09",
    category: "Minutes",
    favorite: false
  },
    {
    id: 8,
    name: "How to Access the HR Portal",
    author: "Marilyn Bator",
    date: "2025-11-09",
    category: "Knowledge Article",
    favorite: false
  },
    {
    id: 9,
    name: "Step-by-Step Guide: Submitting E..",
    author: "Tatiana Vaccaro",
    date: "2025-11-09",
    category: "Policy",
    favorite: false
  },
    {
    id: 10,
    name: "Workplace Rules & Expectations...",
    author: "Abram Philips",
    date: "2025-11-09",
    category: "Policy",
    favorite: false
  },
])

function toggleFavorite(row) {
  row.favorite = !row.favorite
}

window.addEventListener('click', closeOnOutside)
</script>


<template>
    <section class="registry">
        <div class="block__header">
            <h3>Documents Registry</h3>
        </div>
        <div class="registry__inner">
            <div class="registry-add">
                <div class="registry-add__search">
                    <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M10 1.66699V2.66699C10 3.6098 10 4.08121 10.2929 4.3741C10.5858 4.66699 11.0572 4.66699 12 4.66699H13" stroke="#7A7482" stroke-linecap="round" stroke-linejoin="round"/><path d="M2.66663 10.6663V5.33301C2.66663 3.44739 2.66663 2.50458 3.25241 1.91879C3.8382 1.33301 4.78101 1.33301 6.66663 1.33301H9.44769C9.72016 1.33301 9.85643 1.33301 9.97896 1.38375C10.1014 1.4345 10.1978 1.53085 10.3905 1.72353L12.9428 4.27581C13.1354 4.4685 13.2318 4.56485 13.2826 4.68736C13.3333 4.80987 13.3333 4.94613 13.3333 5.21863V10.6663C13.3333 12.5519 13.3333 13.4947 12.7475 14.0805C12.1617 14.6663 11.2189 14.6663 9.33329 14.6663H6.66663C4.78101 14.6663 3.8382 14.6663 3.25241 14.0805C2.66663 13.4947 2.66663 12.5519 2.66663 10.6663Z" stroke="#7A7482" stroke-linecap="round" stroke-linejoin="round"/><path d="M5.33337 7.33301H10.6667M5.33337 9.33301H10.6667M5.33337 11.333H8.11391" stroke="#7A7482" stroke-linecap="round" stroke-linejoin="round"/></svg>
                    <input type="text" placeholder="Search Documents by Name, Keyword, Added by, Function">
                </div>
                <button><svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M18.3333 10.0003C18.3333 5.39795 14.6023 1.66699 9.99996 1.66699C5.39758 1.66699 1.66663 5.39795 1.66663 10.0003C1.66663 14.6027 5.39758 18.3337 9.99996 18.3337C14.6023 18.3337 18.3333 14.6027 18.3333 10.0003Z" stroke="white" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/><path d="M9.99996 6.66699V13.3337M13.3333 10.0003H6.66663" stroke="white" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
                Add new document
                </button>
            </div>
            <div class="registry-buttons">
                <div class="registry-favorite">
                    <button>Favorite<svg width="8" height="7" viewBox="0 0 8 7" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M7.8515 0.226157C7.75261 0.075344 7.63538 0 7.49994 0L0.500038 0C0.364534 0 0.247392 0.075344 0.148419 0.226157C0.0494455 0.377137 0 0.555636 0 0.761988C0 0.968298 0.0494455 1.1468 0.148419 1.29765L3.64838 6.63082C3.74746 6.78163 3.86461 6.85714 4 6.85714C4.13539 6.85714 4.25265 6.78163 4.35154 6.63082L7.8515 1.29761C7.95036 1.1468 8 0.968298 8 0.761946C8 0.555636 7.95036 0.377137 7.8515 0.226157Z" fill="#110E12"/></svg></button>
                </div>
                <div class="registry-categories">
                    <button>Categories<svg width="8" height="7" viewBox="0 0 8 7" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M7.8515 0.226157C7.75261 0.075344 7.63538 0 7.49994 0L0.500038 0C0.364534 0 0.247392 0.075344 0.148419 0.226157C0.0494455 0.377137 0 0.555636 0 0.761988C0 0.968298 0.0494455 1.1468 0.148419 1.29765L3.64838 6.63082C3.74746 6.78163 3.86461 6.85714 4 6.85714C4.13539 6.85714 4.25265 6.78163 4.35154 6.63082L7.8515 1.29761C7.95036 1.1468 8 0.968298 8 0.761946C8 0.555636 7.95036 0.377137 7.8515 0.226157Z" fill="#110E12"/></svg></button>
                </div>
                <div class="registry-functions">
                    <button>Functions<svg width="8" height="7" viewBox="0 0 8 7" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M7.8515 0.226157C7.75261 0.075344 7.63538 0 7.49994 0L0.500038 0C0.364534 0 0.247392 0.075344 0.148419 0.226157C0.0494455 0.377137 0 0.555636 0 0.761988C0 0.968298 0.0494455 1.1468 0.148419 1.29765L3.64838 6.63082C3.74746 6.78163 3.86461 6.85714 4 6.85714C4.13539 6.85714 4.25265 6.78163 4.35154 6.63082L7.8515 1.29761C7.95036 1.1468 8 0.968298 8 0.761946C8 0.555636 7.95036 0.377137 7.8515 0.226157Z" fill="#110E12"/></svg></button>
                </div>
                <div class="registry-date">
                    <button><svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M9.16675 10.8334H13.3334H9.16675ZM6.66675 10.8334H6.67423H6.66675ZM10.8334 14.1667H6.66675H10.8334ZM13.3334 14.1667H13.3259H13.3334Z" fill="#110E12"/><path d="M9.16675 10.8334H13.3334M6.66675 10.8334H6.67423M10.8334 14.1667H6.66675M13.3334 14.1667H13.3259" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/><path d="M15 1.66664V3.33331V1.66664ZM5 1.66664V3.33331V1.66664Z" fill="#110E12"/><path d="M15 1.66664V3.33331M5 1.66664V3.33331" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/><path d="M2.08325 10.2027C2.08325 6.57162 2.08325 4.75607 3.12669 3.62803C4.17012 2.5 5.84949 2.5 9.20825 2.5H10.7916C14.1503 2.5 15.8298 2.5 16.8732 3.62803C17.9166 4.75607 17.9166 6.57162 17.9166 10.2027V10.6307C17.9166 14.2618 17.9166 16.0773 16.8732 17.2053C15.8298 18.3333 14.1503 18.3333 10.7916 18.3333H9.20825C5.84949 18.3333 4.17012 18.3333 3.12669 17.2053C2.08325 16.0773 2.08325 14.2618 2.08325 10.6307V10.2027Z" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/><path d="M2.5 6.66664H17.5H2.5Z" fill="#110E12"/><path d="M2.5 6.66664H17.5" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/></svg>
                        Date added
                    </button>
                </div>
                <div class="export">
                    <button class="recent__export" @click="toggleExport">
                        <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M10.0001 12.0833V3.75M10.0001 12.0833C9.41658 12.0833 8.32636 10.4214 7.91675 10M10.0001 12.0833C10.5836 12.0833 11.6738 10.4214 12.0834 10" stroke="#110E12" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                        <path d="M16.6666 13.75C16.6666 15.8183 16.2349 16.25 14.1666 16.25H5.83325C3.76492 16.25 3.33325 15.8183 3.33325 13.75" stroke="#110E12" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                        </svg>
                        Export PDF
                    </button>
                    <div class="export-modal" v-if="isExportOpen">
                        <div class="export-modal__inner">
                        <button><svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M8.00016 9.66667V3M8.00016 9.66667C7.53336 9.66667 6.66118 8.33713 6.3335 8M8.00016 9.66667C8.46696 9.66667 9.33916 8.33713 9.66683 8" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/><path d="M13.3332 11C13.3332 12.6547 12.9878 13 11.3332 13H4.6665C3.01184 13 2.6665 12.6547 2.6665 11" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/></svg>
                        PDF
                        </button>
                        <button><svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M8.00016 9.66667V3M8.00016 9.66667C7.53336 9.66667 6.66118 8.33713 6.3335 8M8.00016 9.66667C8.46696 9.66667 9.33916 8.33713 9.66683 8" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/><path d="M13.3332 11C13.3332 12.6547 12.9878 13 11.3332 13H4.6665C3.01184 13 2.6665 12.6547 2.6665 11" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/></svg>
                        XLS
                        </button>
                    </div>
                    </div>
                </div>
            </div>
            <div class="registry-table">
                <div class="registry__table">
                    <div class="table__head">
                        <div class="table__row">
                            <div class="table__item">Name of Document<div class="name__arrows"><svg width="7" height="6" viewBox="0 0 7 6" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M0.129939 5.80211C0.216468 5.93407 0.319039 6 0.437557 6H6.56247C6.68103 6 6.78353 5.93407 6.87013 5.80211C6.95674 5.67 7 5.51382 7 5.33326C7 5.15274 6.95674 4.99655 6.87013 4.86455L3.80767 0.198034C3.72097 0.066072 3.61847 0 3.5 0C3.38153 0 3.27894 0.066072 3.19241 0.198034L0.129939 4.86459C0.0434327 4.99655 0 5.15274 0 5.3333C0 5.51382 0.0434327 5.67 0.129939 5.80211Z" fill="#B8B6BC"/></svg><svg width="7" height="6" viewBox="0 0 7 6" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M6.87006 0.197888C6.78353 0.065926 6.68096 0 6.56244 0L0.437533 0C0.318968 0 0.216468 0.065926 0.129866 0.197888C0.0432648 0.329995 0 0.486182 0 0.66674C0 0.847261 0.0432648 1.00345 0.129866 1.13545L3.19233 5.80197C3.27903 5.93393 3.38153 6 3.5 6C3.61847 6 3.72106 5.93393 3.80759 5.80197L6.87006 1.13541C6.95657 1.00345 7 0.847261 7 0.666703C7 0.486182 6.95657 0.329995 6.87006 0.197888Z" fill="#B8B6BC"/></svg></div></div>
                            <div class="table__item">Added by</div>
                            <div class="table__item">Modified</div>
                            <div class="table__item">Category</div>
                            <div class="table__item">Actions</div>
                        </div>
                    </div>
                    <div class="table__body">
                    <div class="table__row" v-for="row in rows" :key="row.id">
                        <div class="table__item">
                        <svg
                            class="registry-star"
                            :class="{ active: row.favorite }"
                            @click="toggleFavorite(row)"
                            width="22" height="22" viewBox="0 0 22 22" fill="currentColor"
                        >
                            <path d="M12.4791 2.19418L14.2389 5.74288C14.4789 6.23687 15.1188 6.7107 15.6588 6.80143L18.8484 7.33575C20.8882 7.67853 21.3682 9.1706 19.8983 10.6425L17.4186 13.1427C16.9986 13.5661 16.7687 14.3827 16.8986 14.9675L17.6086 18.0625C18.1685 20.5123 16.8786 21.46 14.7289 20.1796L11.7392 18.3952C11.1993 18.0726 10.3094 18.0726 9.75936 18.3952L6.76973 20.1796C4.62996 21.46 3.33011 20.5022 3.89005 18.0625L4.59997 14.9675C4.72995 14.3827 4.49998 13.5661 4.08002 13.1427L1.6003 10.6425C0.140464 9.1706 0.610414 7.67853 2.65018 7.33575L5.83983 6.80143C6.36977 6.7107 7.0097 6.23687 7.24967 5.74288L9.00946 2.19418C9.96936 0.268607 11.5292 0.268607 12.4791 2.19418Z"
                            stroke="#110E12" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"
                            />
                        </svg>
                        {{ row.name }}
                        </div>

                        <div class="table__item">{{ row.author }}</div>
                        <div class="table__item">{{ row.date }}</div>
                        <div class="table__item">
                        <span class="category-text" :class="'category--' + row.category.toLowerCase()">{{ row.category }}</span>
                        </div>

                        <div class="table__item">
                            <div class="table__item-modal-wrapper">
                                <button @click.stop="toggleRow(row.id)"><svg width="4" height="17" viewBox="0 0 4 17" fill="none" xmlns="http://www.w3.org/2000/svg"><circle cx="1.5" cy="1.5" r="1.5" fill="#110E12"/><circle cx="1.5" cy="8.5" r="1.5" fill="#110E12"/><circle cx="1.5" cy="15.5" r="1.5" fill="#110E12"/></svg></button>
                                <div class="table__item-modal" v-if="openRow === row.id">
                                    <div class="table__item-modal-inner">
                                        <button><svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M12.6667 8.67078V7.10772C12.6667 6.56249 12.6667 6.28987 12.5652 6.04474C12.4637 5.7996 12.271 5.60683 11.8856 5.22129L8.72793 2.06222C8.39533 1.72948 8.22907 1.56312 8.023 1.46454C7.98013 1.44404 7.93627 1.42584 7.89147 1.41002C7.67607 1.33398 7.44093 1.33398 6.97053 1.33398C4.80721 1.33398 3.72554 1.33398 2.99289 1.92496C2.84487 2.04434 2.71005 2.17923 2.59071 2.3273C2 3.06027 2 4.14242 2 6.3067V9.33745C2 11.8527 2 13.1103 2.78105 13.8917C3.40977 14.5207 4.34695 14.6434 6 14.6673M8 1.66746V2.00094C8 3.88738 8 4.8306 8.5858 5.41664C9.1716 6.00268 10.1144 6.00268 12 6.00268H12.3333" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/><path d="M10.6666 14.666C12.5075 14.666 13.9999 12.666 13.9999 12.666C13.9999 12.666 12.5075 10.666 10.6666 10.666C8.82565 10.666 7.33325 12.666 7.33325 12.666C7.33325 12.666 8.82565 14.666 10.6666 14.666Z" stroke="#110E12" stroke-linejoin="round"/><path d="M10.6602 12.666H10.6662" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/></svg>
                                        View
                                        </button>
                                        <button><svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M12.6667 8.67078V7.10772C12.6667 6.56249 12.6667 6.28987 12.5652 6.04474C12.4637 5.7996 12.271 5.60683 11.8856 5.22129L8.72793 2.06222C8.39533 1.72948 8.22907 1.56312 8.023 1.46454C7.98013 1.44404 7.93627 1.42584 7.89147 1.41002C7.67607 1.33398 7.44093 1.33398 6.97053 1.33398C4.80721 1.33398 3.72554 1.33398 2.99289 1.92496C2.84487 2.04434 2.71005 2.17923 2.59071 2.3273C2 3.06027 2 4.14242 2 6.3067V9.33745C2 11.8527 2 13.1103 2.78105 13.8917C3.40977 14.5207 4.34695 14.6434 6 14.6673M8 1.66746V2.00094C8 3.88738 8 4.8306 8.5858 5.41664C9.1716 6.00268 10.1144 6.00268 12 6.00268H12.3333" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/><path d="M7.875 13.959C7.875 14.2302 7.875 14.3659 7.90482 14.4771C7.98573 14.7791 8.22158 15.0149 8.52354 15.0958C8.63481 15.1257 8.77043 15.1257 9.04167 15.1257H11.9583C12.2296 15.1257 12.3652 15.1257 12.4765 15.0958C12.7784 15.0149 13.0143 14.7791 13.0952 14.4771C13.125 14.3659 13.125 14.2302 13.125 13.959" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/><path d="M11.8125 12.3542C11.8125 12.3542 10.8459 13.6667 10.5 13.6667C10.1541 13.6667 9.1875 12.3542 9.1875 12.3542M10.5 13.375V9.875" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/></svg>
                                        Download
                                        </button>
                                        <button><svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M8.66675 13.8852V14.6673H9.44901C9.72188 14.6673 9.85835 14.6673 9.98108 14.6165C10.1037 14.5657 10.2003 14.4692 10.3932 14.2763L13.6089 11.0603C13.791 10.8783 13.882 10.7873 13.9307 10.6891C14.0232 10.5023 14.0232 10.2831 13.9307 10.0963C13.882 9.99805 13.791 9.90705 13.6089 9.72505C13.4269 9.54305 13.3359 9.45205 13.2377 9.40338C13.0509 9.31085 12.8316 9.31085 12.6448 9.40338C12.5466 9.45205 12.4556 9.54305 12.2736 9.72505L9.05788 12.9411C8.86488 13.134 8.76841 13.2305 8.71755 13.3531C8.66675 13.4759 8.66675 13.6123 8.66675 13.8852Z" stroke="#110E12" stroke-linejoin="round"/><path d="M12.6667 7.33398C12.6667 7.33398 12.6667 6.28772 12.5652 6.04269C12.4637 5.79766 12.271 5.60498 11.8856 5.2196L8.72793 2.0619C8.39533 1.72932 8.22907 1.56302 8.023 1.46448C7.98013 1.44398 7.93627 1.4258 7.89147 1.40999C7.67607 1.33398 7.44093 1.33398 6.97053 1.33398C4.80721 1.33398 3.72554 1.33398 2.99289 1.9247C2.84487 2.04404 2.71005 2.17886 2.59071 2.32687C2 3.05952 2 4.1412 2 6.30454V9.33398C2 11.8481 2 13.1053 2.78105 13.8863C3.48978 14.595 4.59047 14.6607 6.66667 14.6667M8 1.66732V2.00065C8 3.88627 8 4.82908 8.5858 5.41486C9.1716 6.00065 10.1144 6.00065 12 6.00065H12.3333" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/></svg>
                                        Edit
                                        </button>
                                        <button><svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M12.6667 7.33398C12.6667 7.33398 12.6667 6.28772 12.5652 6.04269C12.4637 5.79766 12.271 5.60498 11.8856 5.2196L8.72793 2.0619C8.39533 1.72932 8.22907 1.56302 8.023 1.46448C7.98013 1.44398 7.93627 1.4258 7.89147 1.40999C7.67607 1.33398 7.44093 1.33398 6.97053 1.33398C4.80721 1.33398 3.72554 1.33398 2.99289 1.9247C2.84487 2.04404 2.71005 2.17886 2.59071 2.32687C2 3.05952 2 4.1412 2 6.30454V9.33398C2 11.8481 2 13.1053 2.78105 13.8863C3.48978 14.595 4.59047 14.6607 6.66667 14.6667M8 1.66732V2.00065C8 3.88627 8 4.82908 8.5858 5.41486C9.1716 6.00065 10.1144 6.00065 12 6.00065H12.3333" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/><path d="M12.7499 10.5273L12.5778 13.3121C12.5338 14.0236 12.5118 14.3793 12.3335 14.6351C12.2453 14.7615 12.1318 14.8683 12.0001 14.9485C11.7338 15.1107 11.3774 15.1107 10.6646 15.1107C9.95079 15.1107 9.59389 15.1107 9.32743 14.9481C9.1957 14.8678 9.08214 14.7609 8.994 14.6342C8.81572 14.3781 8.79421 14.0218 8.7512 13.3093L8.58325 10.5273" stroke="#110E12" stroke-linecap="round"/><path d="M8.16675 10.5279H13.1667M11.7933 10.5279L11.6037 10.1367C11.4777 9.87685 11.4147 9.74692 11.3061 9.66589C11.282 9.64791 11.2565 9.63193 11.2298 9.61808C11.1095 9.55566 10.9651 9.55566 10.6763 9.55566C10.3803 9.55566 10.2323 9.55566 10.11 9.6207C10.0829 9.63511 10.057 9.65175 10.0327 9.67043C9.92276 9.75475 9.86137 9.88943 9.73858 10.1588L9.57034 10.5279" stroke="#110E12" stroke-width="1.5" stroke-linecap="round"/></svg>
                                        Delete
                                        </button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    </div>
                </div>
            </div>
            <div class="registry__pagination">
                <Pagination :total="14" :perPage="10" :currentPage="page" @update:currentPage="page = $event"/>
            </div>
        </div>
    </section>
</template>