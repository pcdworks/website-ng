<template>
  <v-container fluid fill-height class="contact-panel">
    <v-container>
      <v-layout align-center justify-center>
        <v-flex xs12 sm12 md12 lg12 align-self-start>
          <v-row>
            <v-col cols="12" xs="12" md="12" lg="1" xl="2"></v-col>
            <v-col cols="12" xs="12" md="4" lg="3" xl="2">
              <v-main>
                <h1 id="mega">
                  Let's get<br>
                  to work
                </h1>
                <p id="mega-message">
                  Whether your challenge is tiny
                  or titanic, we're eager to help.
                  Drop us a line and let's discuss
                  how, together, we can make
                  your project a success.
                </p>
              </v-main>
            </v-col>
            <v-col cols="12" xs="12" md="8" lg="7" xl="6">
              <v-form
                id="contact"
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
                      :rules="phoneRules()"
                      label="Phone Number"
                      name="phone"
                    ></v-text-field>
                  </v-col>
                  <v-col>
                    <v-text-field
                      v-model="form.company"
                      solo
                      :rules="companyRules()"
                      label="Company Website"
                      name="company"
                    ></v-text-field>
                  </v-col>
                </v-row>
                <v-row dense>
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
                <button
                  id="contact-send"
                  :disabled="!valid"
                  outlined
                  type="submit"
                  value="Submit"
                  @click="validate"
                >
                  <span>Submit</span>
                </button>
              </v-form>
            </v-col>
            <v-col cols="12" xs="12" md="12" lg="1" xl="2"></v-col>
          </v-row>
        </v-flex>
      </v-layout>
    </v-container>
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
      title: "Contact | " + 'Product Concept Development, Inc.'
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
    phoneRules() {
      return [v => !!v || 'Phone number is required']
    },
    companyRules() {
      return [v => !!v || 'Company website is required']
    },
    messageRules() {
      return [v => !!v || 'Project description is required']
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
#mega {
  font-size: 3.2rem;
  font-weight: 740;
  text-transform: uppercase;
}
#mega-message {
  font-weight: 650;
}
.contact-panel {
  background: #afbd21;
  padding-top: 84px;
  padding-bottom: 84px;
}

#contact-send {
  background: #afbd21;
  text-align: center;
  text-decoration: none;
  padding: 10px 42px;
  border: 2px solid white;
  display: inline-block;
  transform: skew(-30deg);
  text-transform: uppercase;
  margin: 0 32px;
  max-width: 100%;
  color: white;
}


#contact-send:visited {
  color: #fff;
}

#contact-send:hover {
  color: white;
}

#contact-send > span {
  display: inline-block;
  transform: skew(30deg);
}


</style>