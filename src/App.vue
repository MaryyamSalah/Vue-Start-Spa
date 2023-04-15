<template>
   <navbar-page
        :pages ="pages"
        :active-page="activePage"
        :nav-link-click="(index) => activePage=index"

        ></navbar-page>
        <page-viewer-vue :page="pages[activePage]"></page-viewer-vue>
</template>
<script>

import NavbarPage from './components/NavbarPage.vue'
import PageViewerVue from './components/PageViewerVue.vue'
export default{
    components:{
        NavbarPage,
        PageViewerVue
       
    },
     data(){
                return{
                    activePage:0,
                    
                    pages :[
                    {
                    link: {text:'Home' , url:'index.html'},
                    pageTitle:'Home page' ,
                    content:'this is Home page'
                },
                {

                    link: {text:'About' , url:'about.html'},
                    pageTitle:'About page' ,
                    content:'this is About page'
                },
                {
                    link: {text:'Contact' , url:'contact.html'},
                    pageTitle:'Contact page' ,
                    content:'this is Contact page'
                },
                           

              
               ] }},
           
}
</script>
