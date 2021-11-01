<template>
  <v-container fluid fill-height>
    <v-layout align-center justify-center>
      <v-flex xs12 sm12 md10 lg8>
        <v-card class="elevation-4" width="100%">
          <v-toolbar>
            <v-toolbar-title>Contact Us</v-toolbar-title>
          </v-toolbar>
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
            <v-card-text>
              <v-text-field
                v-model="form.name"
                :rules="nameRules()"
                label="Name"
                required
                name="name"
              ></v-text-field>

                <v-text-field
                  v-model="form.email"
                  :rules="emailRules()"
                  label="Email address"
                  required
                  name="email"
                ></v-text-field>

                <v-text-field
                  v-model="form.phone"
                  label="Phone number (Optional)"
                  name="phone"
                ></v-text-field>

                <v-text-field
                  v-model="form.company"
                  label="Company (Optional)"
                  name="company"
                ></v-text-field>
                <v-textarea
                  v-model="form.message"
                  auto-grow
                  :rules="messageRules()"
                  label="Message"
                  rows="5"
                  required
                  name="message"
                ></v-textarea>
                <p>
                  Please detail any specific inquiries or areas of interest.
                </p>
              </v-card-text>
            <v-card-actions>
              <v-btn
                :disabled="!valid"
                color="primary"
                type="submit"
                value="Submit"
                @click="validate"
              >
                Send
                <v-icon right>mdi-send</v-icon>
              </v-btn>
              <v-btn color="secondary" @click="reset" >
                Clear<v-icon right>mdi-close-thick</v-icon>
              </v-btn>
            </v-card-actions>
          </v-form>
        </v-card>
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
