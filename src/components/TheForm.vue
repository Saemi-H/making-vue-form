<template>
  <form @submit.prevent="submitForm()">
      <!-- validation check -->
      <!-- add class for UI/UX style-->
    <div class="form-control" :class="{invalidStyle : inputValidity === 'invalid'}">
      <label for="user-name">Your Name</label>
      <!-- @blur -->
      <input id="user-name" name="user-name" type="text" v-model.trim="userName" @blur="validityInput"/>
      <!-- add warning  -->
      <!-- add condition -->
      <p v-if="inputValidity === 'invalid'">Please check your user name!</p>
    </div>
    <div class="form-control">
      <label for="age">Your Age (Years)</label>
      <input id="age" name="age" type="number" v-model="userAge" ref="ageInput"/>
    </div>
    <div class="form-control">
      <label for="referrer">How did you hear about us?</label>
      <select id="referrer" name="referrer" v-model="referrer">
        <option value="google">Google</option>
        <option value="wom">Word of mouth</option>
        <option value="newspaper">Newspaper</option>
      </select>
    </div>
    <div class="form-control">
      <h2>What are you interested in?</h2>
      <div>
        <input id="interest-news" name="interest" type="checkbox" value="news" v-model="interest"/>
        <label for="interest-news">News</label>
      </div>
      <div>
        <input id="interest-tutorials" name="interest" type="checkbox" value="tutorials" v-model="interest"/>
        <label for="interest-tutorials">Tutorials</label>
      </div>
      <div>
        <input id="interest-nothing" name="interest" type="checkbox" value="nothing" v-model="interest"/>
        <label for="interest-nothing">Nothing</label>
      </div>
    </div>
    <div class="form-control">
      <h2>How do you learn?</h2>
      <div>
        <input id="how-video" name="how" type="radio" />
        <label for="how-video">Video Courses</label>
      </div>
      <div>
        <input id="how-blogs" name="how" type="radio" />
        <label for="how-blogs">Blogs</label>
      </div>
      <div>
        <input id="how-other" name="how" type="radio" />
        <label for="how-other">Other</label>
      </div>
    </div>
    <div class="agree-check">
      <input id="agree-check" type="checkbox" name="agree-check" v-model="agree" />
      <label for="agree-check">Agree to check?</label>
    </div>
    <div>
      <button>Save Data</button>
    </div>
  </form>
</template>

<script>
  export default {
    data(){
      return{
        userName:"",
        userAge:null,
        ageInput:null,
        referrer:"wom",
        interest:[], //checkbox = multiple selection & needs different values to select each
        how:"", //radio btn = select only one
        agree: false,
        inputValidity: "pending"  // data checking validity
      }
    },
    methods : {
      submitForm(){
        console.log(this.userName);
        this.userName=''
        console.log(this.userAge);
        // v-model = automatically convert into num = ref.num
        console.log(this.$refs.ageInput.value);
        this.interest=[]
        this.how=""
        console.log(this.agree);
        // only 1 checkbox = true/false
        this.agree = false;
      },
      // build validityInput function
      validityInput(){
        if(this.userName === ''){
          this.inputValidity = "invalid"
          console.log(`inputValidity : ${this.inputValidity}`);
        }else{
          this.inputValidity = "valid"
        }
      },
    }
  }

</script>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  background-color: #ffffff;
}

.form-control {
  margin: 0.5rem 0;
}

label {
  font-weight: bold;
}

h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}

input,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}

select {
  width: auto;
}

input[type='checkbox'],
input[type='radio'] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}

input[type='checkbox'] + label,
input[type='radio'] + label {
  font-weight: normal;
}

.invalidStyle input{
  border: 1px solid red
}

button {
  font: inherit;
  border: 1px solid #0076bb;
  background-color: #0076bb;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 30px;
}

button:hover,
button:active {
  border-color: #002350;
  background-color: #002350;
}
</style>

