<template>
  <div class="testimonials">
      <h1>Testimonials</h1>
    <!-- loop comments -->
      <el-row :gutter="12" >
        <el-col :span="12" v-for="(list,index) in comments" :key="index">
          <el-card shadow="always">  
              <p><strong>{{list.Name}} - {{list.Position}}</strong></p>        
              <p>{{list.Comment}}</p>
          </el-card>
        </el-col>
      </el-row>

    <!-- the form start from here -->
    <div class="Form">
      <el-form :model="form" :rules="rules" ref="form">
        <h3>Leave us a testimonial</h3>
        <el-row>          
          <!-- First Name -->
          <el-form-item prop="yourName">
              <el-col :span="12">
                <el-input class="inline-input" placeholder="Enter Your Name Here < 50" id="userName" v-model="form.yourName"></el-input>
            </el-col>
          </el-form-item>
          
          <!-- position Title -->
          <el-form-item prop="position">
              <el-col :span="12">
                    <el-input class="inline-input" placeholder="Your Occupation < 100" id="userPosition" v-model="form.position"></el-input>
              </el-col>
          </el-form-item>
          
          <!-- Description -->
          <el-form-item prop="desc">
            <el-input type="textarea" placeholder="Enter Your Comments Here < 300" id="userDesc" v-model="form.desc"></el-input>
          </el-form-item>
        </el-row>
      </el-form>

      <!-- Submit button -->
      <el-button type="success" @click="submitForm('form')">Submit</el-button>

    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {

  data () {
    return {
          
        form: {
          yourName: null,
          position: null,
          desc: null,  
        },

        comments:[],

        // Setting the Rules for the form:--------
        // name, position, descriptions can not be empty;
        // name =< 50 words, Occupation =< 100 words, comment description  =< 300 words.
        rules: {
          yourName:[
            {required: true, message: 'Please input Frist Name', trigger: 'blur'},
            { min:0, max: 50, message: 'You name cannot be more than 50 words', trigger: ['blur', 'change'] }
          ],
          position:[
            { required: true, message: 'Please input the position', trigger: 'blur' },
            { min:0, max: 100, message: 'Occupation title cannot be more than 100 words', trigger: ['blur', 'change'] }
          ],
          desc:[
            { required: true, message: 'Please input the comment', trigger: 'blur' },
            { min:0, max: 300, message: 'Comment cannot be more than 300 words', trigger: ['blur', 'change'] }
          ],
        }
    };
  },

  methods: {
     

    submitForm(form) {
      this.$refs[form].validate((valid) => {
        if (valid) { 

          let obj = {
             'Name': this.form.yourName,
             'Position': this.form.position,
             'Comment': this.form.desc,
          };
          
          // let userComment = this.form.yourName + ' - ' + this.form.position + ' : ' + this.form.desc
          // push the comments

          
          // import axios to make api calls
          axios 
          .post("https://chou0120-midterm.firebaseio.com/data.json", JSON.stringify(obj))
          .then(response => {
              console.log(response);
              console.log("Your data was saved status:" + response.status)

              // here we are making a GET request using AXIOS to get the data
              axios
                .get("https://chou0120-midterm.firebaseio.com/data.json")
                .then(response => {
                  // console.log(response);
                  console.log(response.data);
                  // Checking if the response has some data
                  if (response.data) {
                    this.comments = response.data;
                  }
                })
                .catch(error => {
                  console.log("There was an error in getting data: " + error.response);
                });
          })

          // catching the error in console
          .catch(error => {
              console.log(error);
          })

          // reset the form once pushed 
          this.$refs[form].resetFields();
        } else {
          console.log('error submit!!');
          return false;
        }    
      });
    },
  },

// created is a life cycle hook which will run when the instance is created
  created() {
      
  // here we are making a GET request using AXIOS to get the data
  axios
    .get("https://chou0120-midterm.firebaseio.com/data.json")
    .then(response => {
      // console.log(response);
       console.log(response.data);
      // Checking if the response has some data
      if (response.data) {
        this.comments = response.data;
}
    })
    .catch(error => {
      console.log("There was an error in getting data: " + error.response);
    });
  }
}
</script>

<style scoped>
  .Form{
    border: 1px solid darkslategray;
    border-radius: 2.5rem;
    padding: 2rem;
  }
  .el-row{
    margin-bottom: 1.5rem;
  }

  .el-card {
    margin-bottom: 1.5rem;
    background-color: #c57070;
    border-radius: 2rem;
  }
</style>



