<template>
    <div class="ajax-suggestion-search-input">
        <input v-model="search" v-on:keyup="onKeyUp" class="form-control" :class="inputClass" type="text" />
        <div>
            <ul>
                <li v-for="result in results" v-bind:key="result.id" :class="[{'has-image': result.img!=undefined}, {'has-subtitle': result.subtitle!=undefined}]">
                    <img :src="result.img" width="38" height="38"/>
                    <div class="ajax-suggestion-search-input-txts">
                        <span class="ajax-suggestion-search-input-title">{{result.title}}</span>
                        <span class="ajax-suggestion-search-input-subtitle">{{result.subtitle}}</span>
                    </div>
                </li>
            </ul>
        </div>
    </div>
</template>
<script>
    import axios from 'axios'
    export default {
        data() {
            return {
                search: '',
                results: [
                    {
                        id: 1,
                        title: 'Sirvan Khosravi',
                        subtitle: 'Tehran, Iran',
                        img: 'https://www.vowave.com/uploads/arts/PjsWjz/122_ZduQ4UKGntg5iqAZMSKL_s.jpg'
                    },
                    {
                        id: 2,
                        title: 'Sirvan Khosravi',
                        subtitle: 'Tehran, Iran',
                        img: 'https://www.vowave.com/uploads/arts/PjsWjz/122_ZduQ4UKGntg5iqAZMSKL_s.jpg'
                    },
                    {
                        id: 3,
                        title: 'Sirvan Khosravi',
                        img: 'https://www.vowave.com/uploads/arts/PjsWjz/122_ZduQ4UKGntg5iqAZMSKL_s.jpg'
                    }
                ]
            }
        },
        props: {
            inputClass: {
                type: Array,
                default: function () { return [] },
                validator: (classes) => classes.every(e => typeof e === 'string')
            },
        },
        created() {
        },
        methods: {

            onKeyUp(e) {
                console.log(this.search)
            }
        }
    };
</script>
<style>
    .ajax-suggestion-search-input {
        position: relative;
        display: -ms-flexbox;
        display: -webkit-box;
        display: flex;
        -ms-flex-wrap: wrap;
        flex-wrap: wrap;
        -ms-flex-align: stretch;
        -webkit-box-align: stretch;
        align-items: stretch;
        width: 100%;
        font-family: tahoma;
    }
    .ajax-suggestion-search-input > input {
        height: 22px;
        padding: 6px 12px;
        border-radius: 0.25rem;
        box-shadow: none;
        border: 1px solid #ccc;
        margin: 0;
        position: relative;
        -ms-flex: 1 1 auto;
        -webkit-box-flex: 1;
        flex: 1 1 auto;
        width: 1%;
        margin-bottom: 0;
    }
    .ajax-suggestion-search-input > input:focus {
        box-shadow: none;
        border: 1px solid #ccc;
        outline: none;
    }
    .ajax-suggestion-search-input > div {
        position: absolute;
        left: 0;
        right: 0;
        top: 100%;
        background: #999;
        margin-top: -5px;
        border-radius: 0 0 .25rem .25rem;
        padding: 6px 12px;
    }
    .ajax-suggestion-search-input > div > ul {
        padding: 0;
        margin: 0;
        list-style: none;
    }
    .ajax-suggestion-search-input > div > ul > li {
        height: 38px;
        position: relative;
        margin-top: 4px;
    }
    .ajax-suggestion-search-input > div > ul > li:first-child {
        margin-top: 0;
    }
    .ajax-suggestion-search-input > div > ul > li .ajax-suggestion-search-input-txts {
        padding-top: 3px;
    }
    .ajax-suggestion-search-input > div > ul > li:not(.has-subtitle) .ajax-suggestion-search-input-txts {
        padding-top: 10px;
    }
    .ajax-suggestion-search-input > div > ul > li.has-image {
        padding-left: 45px;
    }
    .ajax-suggestion-search-input > div > ul > li > img {
        position: absolute;
        left: 0;
        top: 0;
    }
    .ajax-suggestion-search-input > div > ul > li span {
        display: block;
    }
    .ajax-suggestion-search-input-title {
        font-size: 15px;
    }
    .ajax-suggestion-search-input-subtitle {
        font-size: 10px;
    }
</style>
