<template>
  <v-container fluid fill-height class="contact-panel">
    <v-layout align-center justify-center>
      <v-flex xs12 sm12 md12 lg12 align-self-start>
        <v-row>
          <v-col>
            <v-content>
              <h1>Let's get to work</h1>
              <p>
                Whether your challenge is tiny
                or titanic, we're eager to help.
                Drop us a line and let's discuss
                how, together, we can make
                your project a success.
              </p>
            </v-content>
          </v-col>
          <v-col>
            <v-form
              ref="form"
              v-model="valid"
              lazy-validation
              name="contact"
              method="POST"
              data-netlify="true"
              data-netlify-honeypot="bot-field"
              @submit.prevent="handleSubmit"
            >
              <input type="hidden" name="form-name" value="contact" />
              <v-row dense>
                <v-col>
                  <v-text-field
                    v-model="form.name"
                    solo
                    :rules="nameRules()"
                    label="Name"
                    required
                    name="name"
                  ></v-text-field>
                </v-col>
                <v-col>
                  <v-text-field
                    v-model="form.email"
                    solo
                    :rules="emailRules()"
                    label="Email address"
                    required
                    name="email"
                  ></v-text-field>
                </v-col>
              </v-row>
              <v-row dense>
                <v-col>
                  <v-text-field
                    v-model="form.phone"
                    solo
                    label="Phone Number"
                    name="phone"
                  ></v-text-field>
                </v-col>
                <v-col>
                  <v-text-field
                    v-model="form.company"
                    solo
                    label="Company Website"
                    name="company"
                  ></v-text-field>
                </v-col>
              </v-row>
              <v-row>
                <v-col>
                  <v-textarea
                    v-model="form.message"
                    solo
                    auto-grow
                    :rules="messageRules()"
                    label="Project Description"
                    rows="5"
                    required
                    name="message"
                  ></v-textarea>
                </v-col>
              </v-row>
              <v-btn
                :disabled="!valid"
                color="primary"
                class="slanted"
                type="submit"
                value="Submit"
                outlined
                @click="validate"
              >
                Submit
              </v-btn>
            </v-form>
          </v-col>
        </v-row>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  name: 'Contact',
  data: () => ({
    valid: true,
    form: {
      name: '',
      message: '',
      phone: '',
      email: '',
      company: ''
    }
  }),
  head() {
    return {
      title: "Contact Us | " + 'Product Concept Development, Inc.'
    };
  },
  methods: {
    nameRules() {
      return [v => !!v || 'Name is required']
    },
    emailRules() {
      return [
        v => !!v || 'Email address is required',
        v => /.+@.+/.test(v) || 'Email address must be valid'
      ]
    },
    messageRules() {
      return [v => !!v || 'Message is required']
    },
    validate() {
      this.$refs.form.validate()
    },
    reset() {
      this.$refs.form.reset()
    },
    encode(data) {
      return Object.keys(data)
        .map(
          key => `${encodeURIComponent(key)}=${encodeURIComponent(data[key])}`
        )
        .join('&')
    },
    handleSubmit() {
      fetch('/', {
        method: 'POST',
        headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
        body: this.encode({
          'form-name': 'contact',
          ...this.form
        })
      })
        .then(() => {
          this.$router.push('/thanks')
        })
        .catch(() => {
          this.$router.push('/404')
        })
    }
  }
}
</script>

<style scoped>
.contact-panel {
  background: #afbd21;
}
.slanted {
  -ms-transform: skewX(-30deg);
  -webkit-transform: skewX(-30deg);
  transform: skewX(-30deg);
}
</style>