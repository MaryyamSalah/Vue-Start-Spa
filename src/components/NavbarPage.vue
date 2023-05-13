<template>
    <nav 
        :class="[`navbar-${theme}`,`bg-${theme}`,'navbar' ,'navbar-expand-lg']">
        
            <ul  class="navbar-nav">
              <li v-for="(page ,index) in publishedPgaes" class="nav-item" :key ="index">
                <navbar-link
                :page="page"
                :isActive="activePage == index"
                @click.prevent="navLinkClick(index)"
                ></navbar-link>
              </li>
            </ul>
            <form class="d-flex">
                <button  type="button" class="btn btn-primary" @click.prevent="changeTheme()">Toggle Navbar</button>
            </form>
      </nav>
</template>

<script>
import NavbarLink from './NavbarLink.vue'
export default{
    components:{
    NavbarLink
    },
    created(){
              this.getThemeSetting
               },

    computed:{
            publishedPgaes(){
               return this.pages.filter(p =>p.published);
               }},
     props:['pages','activePage','navLinkClick'],
               
       data(){
                return{
                    theme:'dark',
                }
            }, 
            methods:{
                changeTheme(){
                    let theme = 'light';
                    if(this.theme=='light'){
                        theme='dark'
                    }
                    this.theme=theme;
                    this.storeThemeSetting();
                },
                 storeThemeSetting(){
                localStorage. setItem ('theme',this.theme)
                
            },
            getThemeSetting(){
                let theme = localStorage.getItem('theme')

                if(theme){
                    this.theme=theme
                }
                
            }
            },
           
}
</script>
