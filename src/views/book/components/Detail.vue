<template>
  <el-form ref="postForm" :model="postForm">
    <sticky
      :class-name="'sub-navbar' + postForm.status"
    >
      <el-button
        v-if="!isEdit"
        @click="showGuide"
      >
        显示帮助
      </el-button>
      <el-button
        v-loading="loading"
        type="success"
        style="margin-left: 10px"
        @click="submitForm"
      >
        {{ isEdit ? '编辑电子书' : '新增电子书' }}
      </el-button>
    </sticky>
    <div class="detail-container">
      <el-row>
        <warning />
        <el-col :span="24">
          <!-- 编写具体表单控件 -->
          <ebook-upload
            :file-list="fileList"
            :disabled="isEdit"
            @onSuccess="onUploadSuccess"
            @onRemove="onUploadRemove"
          />
        </el-col>
        <el-col :span="24">
          <!-- 编写具体表单控件 -->
          <el-form-item prop="title">
            <MdInput
              v-model="postForm.title"
              max-length="100"
              name="name"
              required
            >
              书名
            </MdInput>
          </el-form-item>
          <el-row>
            <el-col :span="12">
              <el-form-item label="作者：" :lable-width="lableWidth">
                <el-input
                  v-model="postForm.author"
                  placeholder="作者"
                />
              </el-form-item>
            </el-col>
            <el-col :span="12">
              <el-form-item label="出版社：" :lable-width="lableWidth">
                <el-input
                  v-model="postForm.publisher"
                  placeholder="出版社"
                />
              </el-form-item>
            </el-col>
          </el-row>
          <el-row>
            <el-col :span="12">
              <el-form-item label="语言：" :lable-width="lableWidth">
                <el-input
                  v-model="postForm.language"
                  placeholder="语言"
                />
              </el-form-item>
            </el-col>
            <el-col :span="12">
              <el-form-item label="根文件：" :lable-width="lableWidth">
                <el-input
                  v-model="postForm.rootFile"
                  placeholder="根文件"
                  disabled
                />
              </el-form-item>
            </el-col>
          </el-row>
          <el-row>
            <el-col :span="12">
              <el-form-item label="文件路径：" :lable-width="lableWidth">
                <el-input
                  v-model="postForm.filePath"
                  placeholder="文件路径"
                  disabled
                />
              </el-form-item>
            </el-col>
            <el-col :span="12">
              <el-form-item label="解压路径：" :lable-width="lableWidth">
                <el-input
                  v-model="postForm.unzipPath"
                  placeholder="解压路径"
                  disabled
                />
              </el-form-item>
            </el-col>
          </el-row>
          <el-row>
            <el-col :span="12">
              <el-form-item label="封面路径：" :lable-width="lableWidth">
                <el-input
                  v-model="postForm.coverPath"
                  placeholder="封面路径"
                  disabled
                />
              </el-form-item>
            </el-col>
            <el-col :span="12">
              <el-form-item label="文件名称：" :lable-width="lableWidth">
                <el-input
                  v-model="postForm.fileName"
                  placeholder="文件名称"
                  disabled
                />
              </el-form-item>
            </el-col>
          </el-row>
          <el-row>
            <el-col :span="24">
              <el-form-item label="封面：" lable-width="60px">
                <a
                  v-if="postForm.cover"
                  :href="postForm.cover"
                  target="_blank"
                >
                  <img :src="postForm.cover" class="priview-img">
                </a>
                <span v-else>无</span>
              </el-form-item>
            </el-col>
          </el-row>
          <el-row>
            <el-col :span="24">
              <el-form-item label="目录：" :lable-width="lableWidth">
                <div
                  v-if="postForm.contents && postForm.contents.length > 0"
                  class="contents-wrapper"
                >
                  <el-tree />
                </div>
                <span v-else>无</span>
              </el-form-item>
            </el-col>
          </el-row>
        </el-col>
      </el-row>
    </div>
  </el-form>
</template>

<script>
import Sticky from '../../../components/Sticky/index'
import Warning from './Warning'
import EbookUpload from '../../../components/EbookUpload'
import MdInput from '../../../components/MDinput/index'

export default {
  components: { Sticky, Warning, EbookUpload, MdInput },
  props: {
    isEdit: Boolean
  },
  data() {
    return {
      loading: false,
      postForm: {
        status: ''
      },
      fileList: [],
      lableWidth: '120px'
    }
  },
  methods: {
    onUploadSuccess() {
      console.log('onUploadSuccess')
    },
    onUploadRemove() {
      console.log('onUploadRemove')
    },
    submitForm() {
      this.loading = true
      setTimeout(() => {
        this.loading = false
      }, 1000)
    },
    showGuide() {
      console.log('show guide...')
    }
  }
}
</script>

<style lang="scss" scoped>
  .detail-container {
    padding: 40px 50px 20px;
    .preview-img {
      width: 200px;
      height: 270px;
    }
  }
</style>
