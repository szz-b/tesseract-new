<template>
    <div>
        <el-upload
                action="/upload"
                :on-preview="handlePreview"
                multiple
                :limit="10"
                accept=".pdf">
            <el-button size="small" type="primary">点击上传</el-button>
            <div slot="tip" class="el-upload__tip">只能上传pdf文件，且不超过100MB</div>
        </el-upload>
        <iframe :src="resUrl" width="100%" height="100%"></iframe>
    </div>

</template>

<script>

    export default {
        data() {
            return {
                resUrl: ''
            }
        },
        methods:{
            handlePreview(file) {
                console.log(file);
                this.resUrl = file.response.url;
                window.open(file.response.url);
            }
        },
        name: "PdfOcr.vue"
    }
</script>

<style scoped>

</style>