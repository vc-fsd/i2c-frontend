<template>
    <div class="container">
        <form enctype="multipart/form-data" @submit.prevent="uploadFile()">
            <div class="upload-section jumbotron">
               <div v-if="!currentStatus">
                    <div class="py-5">
                        <label for="upload-photo"><i class="my-auto fa fa-plus fa-5x upload-icon" aria-hidden="true"></i></label>
                    </div>
                    <input type="file" name="photo" id="upload-photo" accept="image/*" @change.prevent="filesChange($event.target.name, $event.target.files)"/>
               </div>
               <div v-else>
                   <img :src=imgUrl class="preview-img"/>
               </div>
            </div>    
            <div class="">
                <button class="mr-2 p-2 btn btn-info" type="button" @click="uploadFile()"><i class="fa fa-search"></i> Search</button>
                <button class="p-2 btn btn-info" type="button" @click="reset()"><i class="fa fa-undo"></i> Reset</button>
            </div>
        </form>
    </div>    
</template>

<script>
import axios from 'axios'

const STATUS_INITIAL=0, STATUS_UPLOADED=1;
export default {
    name: 'UploadImage',
    data () {
        return {
            serverLink: "http://localhost:8080/upload",
            formData: "",
            currentStatus: STATUS_INITIAL,
            imgUrl: "",
            FILE: null
        }
    },
    methods: {
        filesChange(filename, files) {
            this.FILE = files[0];
            this.currentStatus = STATUS_UPLOADED;
            this.imgUrl = URL.createObjectURL(this.FILE);
            // if(!filename.length) {
            //     alert("Please upload an image (.jpg,.png")
            //     return;
            // }

            // this.currentStatus = STATUS_UPLOADED;
            // this.imgUrl = URL.createObjectURL(files[0]);

            // console.log(filename, files);
            // this.formData = new FormData();
            // for (let i = 0; i < files.length; i++) {
            //     this.formData.append(filename, files[i], files[i].name);
            // }
        },
        uploadFile() {
            const filename = this.FILE.name;
            if(!filename.length) {
                alert("Please upload an image (.jpg,.png")
                return;
            }


            console.log(filename, this.FILE);
            this.formData = new FormData();
            this.formData.append(filename, this.FILE, filename);

            axios.post(this.serverLink, this.formData).then(
                rsp => {
                console.log(rsp)
                }
            ).catch(err => {
                console.log(err)
            })
        },
        reset() {
            this.currentStatus = STATUS_INITIAL;
            this.imgUrl = "";
        }
    }
}

</script>

<style scoped>
.upload-section {
    min-height: 300px;
}

.upload-icon {
    cursor: pointer;
}

.jumbotron {
    background-color: lightblue;
}

.preview-img {
    width:150px;
}

#upload-photo {
    opacity: 0;
}
</style>