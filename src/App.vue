<template>
   <navbar-page
        :pages ="pages"
        :active-page="activePage"
        :nav-link-click="(index) => activePage=index"

        ></navbar-page>
        <!-- <page-viewer-vue 
        v-if="pages.length>0"
        :page="pages[activePage]"></page-viewer-vue> -->
        <create-page
        :page-created="pageCreated"
        ></create-page>
</template>
<script>
// import createdPageVue from './components/createdPage.vue'
import NavbarPage from './components/NavbarPage.vue'
// import PageViewerVue from './components/PageViewerVue.vue'
import CreatePage from './components/CreatePage.vue'

export default{
    components:{
        NavbarPage,
        // PageViewerVue,
        CreatePage
       
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
                },
                pageCreated(pageObj){
                    console.log(pageObj)
                }
               }
           
}
</script>
