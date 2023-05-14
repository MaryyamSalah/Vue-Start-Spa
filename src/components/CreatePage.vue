<template>
    <div class="container mb-3" >
        <form action=""></form>
        <div class="mb-3">
            <label for="" class="form-label">Page Title</label>
            <input type="text" class="form-control" v-model="pageTitle"
            />
        </div>
        <div class="mb-3">
            <label for="" class="form-label">Content</label>
            <textarea type="text" class="form-control" rows="5" v-model="content"></textarea>
        </div>
        <div class="col">
            <div class="mb-3">
                <label for="" class="form-label">Link Text</label>
                <input type="text" class="form-control" v-model="linkText"/>
            </div>
             <div class="mb-3">
                <label for="" class="form-label">Link URL</label>
                <input type="url" class="form-control" v-model="linkUrl"/>
            </div>
            <div class="row mb-3">
                <div class="form-check">
                    <label class="form-check-label" for="gridCheck1">Published</label>
                    <input class="form-check-input" type="checkbox" v-model="published" >
                </div>
            </div>
        </div>
        <div class="mb-3">
          <button class="btn btn-primary" @click.prevent="submitForm" :disabled="isFormInvalid">Create page</button>
        </div>
    </div>
</template>
<script>


export default {
    props:['pageCreated'],
    computed:{
     isFormInvalid(){
    return !this.pageTitle || !this.linkText || !this.content || !this.linkUrl
     }
    },
    data(){
        return {
            pageTitle: "" ,
            content:"" ,
            linkText:"" ,
            linkUrl:"" ,
            published:true
        }
    },
    methods:{
        submitForm(){
            if(!this.pageTitle || !this.linkText || !this.content || !this.linkUrl){
                alert("Please fill the form");
                return;
            }
            this.pageCreated({
                pageTitle: this.pageTitle,
                content:this.content,
                linkText:this.linkText,
                linkUrl:this.linkUrl,
                published:this.published
            });

           this.pageTitle;'' ;
           this. content;"" ;
            this.linkText; "" ;
            this.linkUrl; "" ;
            this.published; true;

        }

    },
    watch:{
        pageTitle(newTitle , oldTitle){
            if(this.linkText === oldTitle){
                this.linkText = newTitle;
            }
        }
    }
}
</script>
