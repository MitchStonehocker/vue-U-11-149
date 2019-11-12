<template>
  <div class="container">
    <form>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <h1>Comment? Issue? Tell us!</h1>
          <hr>
          <div class="form-group">
            <label for="email">Email</label>
            <input 
              type="text"
              id="email"
              class="form-control"
              v-model="userData.email"
            >
          </div>
          <div class="form-group">
            <label for="email2">Email - 2</label>
            <input 
              type="text"
              id="email2"
              class="form-control"
              :value="userData.email2"
              @input="userData.email2 = $event.target.value"
            >
          </div>
          <div class="form-group">
            <label for="password">Password</label>
            <input 
              type="password"
              id="password"
              class="form-control"
               v-model="userData.password"
            >
          </div>
          <div class="form-group">
            <label for="age">Age</label>
            <input 
              type="number"
              id="age"
              class="form-control"
               v-model="userData.age"
            >
          </div>
          <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
              <label for="message">Message</label>
              <br>
              <!-- Interpolation between <textarea>{{ test }}</textarea> doesn't work!-->
              <textarea
                id="message"
                rows="5"
                class="form-control"
                v-model="message">
              </textarea>
            </div>
          </div>
          <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
              <div class="form-group">
                <label for="sendmail">
                  <input
                    type="checkbox"
                    id="sendmail"
                    value="SendMail"
                    v-model="sendMail"
                  > Send Mail
                </label>
                <label for="sendInfomail">
                  <input
                    type="checkbox"
                    id="sendInfomail"
                    value="SendInfoMail"
                    v-model="sendMail"
                  > Send Infomail
                </label>
              </div>
            </div>
          </div>
          <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
              <label for="male">
                <input
                  type="radio"
                  id="male"
                  value="Male"
                  v-model="gender"
                > Male
              </label>
              <label for="female">
                <input
                  type="radio"
                  id="female"
                  value="Female"
                  v-model="gender"
                > Female
              </label>
            </div>
          </div>
          <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
              <label for="prioritySelected">Priority</label>
              <select v-model="prioritySelected">
                <option v-for="(option, index) in priorities" v-bind:value="option.text" :key="`${index}`">
                  {{ option.text }}
                </option>
              </select>
            </div>
          </div>
          <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
              <app-switch v-model="dataSwitch"></app-switch>
            </div>
          </div>
          <hr>
          <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
              <button
                class="btn btn-primary"
                @click.prevent="submitForm"
              >Preview
              </button>
            </div>
          </div>
        </div>
      </div>
    </form>
    <hr>
    <div class="row" v-if="isSubmitted">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <div class="panel panel-default">
          <div class="panel-heading">
            <h4>Your Form Data</h4>
          </div>
          <div class="panel-body">
            <p>Email: {{ userData.email }}</p>
            <p>Email - 2: {{ userData.email2 }}</p>
            <p>Password: {{ userData.password }}</p>
            <p>Age: {{ userData.age }}</p>
            <p style="white-space: pre">Message: {{ message }}</p>
            <p><strong>Send Email?</strong></p>
            <ul>
              <li v-for="(item, index) in sendMail" :key="`item-${index}`">{{ item }}</li>
            </ul>
            <p>Gender: {{ gender }}</p>
            <p>Priority: {{ prioritySelected }}</p>
            <p>Switch: {{ dataSwitch }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Switch from './Switch'
export default {
  data () {
    return {
      userData: {
        email: '',
        email2: '',
        password: '',
        age: 0
      },
      message: 'your message',
      sendMail: [],
      gender: '',
      prioritySelected: 'Medium',
      priorities: [
        { text: 'High' },
        { text: 'Medium', },
        { text: 'Low', }
      ],
      dataSwitch: true,
      isSubmitted: false
    }
  },
  methods: {
    submitForm () {
      this.isSubmitted = true
    }
  },
  components: {
    appSwitch: Switch
  }
}
</script>

<style>

</style>
