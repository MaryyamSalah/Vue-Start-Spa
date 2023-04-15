<template>
    <nav 
        :class="[`navbar-${theme}`,`bg-${theme}`,'navbar' ,'navbar-expand-lg']">
        
            <ul  class="navbar-nav">
              <li v-for="(page ,index) in pages" class="nav-item" :key ="index">
                <a class="nav-link"
                :class="{active:activePage==index}"
                :href="page.link.url"
                :title="`This page goes to ${page.link.text} page`"
                @click.prevent="navLinkClick(index)"
                
                >{{page.link.text}}</a>
              </li>
            </ul>
            <form class="d-flex">
                <button  type="button" class="btn btn-primary" @click.prevent="changeTheme()">Toggle Navbar</button>
            </form>
      </nav>
</template>

<script>
export default{
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
                }
            }
}
</script>
