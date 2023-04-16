<template>
   <navbar-page
        :pages ="pages"
        :active-page="activePage"
        :nav-link-click="(index) => activePage=index"

        ></navbar-page>
        <page-viewer-vue 
        v-if="pages.length>0"
        :page="pages[activePage]"></page-viewer-vue>
</template>
<script>

import NavbarPage from './components/NavbarPage.vue'
import PageViewerVue from './components/PageViewerVue.vue'
export default{
    components:{
        NavbarPage,
        PageViewerVue
       
    },
    created(){
        this.getPages()
    },
     data(){
                return{
                    activePage:0,
                    
                    pages :[]
               }},
               methods:{
                async getPages(){
                    let res = await fetch("pages.json")
                    let data = await res.json()
                    this.pages=data;
                }
               }
           
}
</script>
