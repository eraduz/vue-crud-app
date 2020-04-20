<template>
  <form id="contact-form" role="form">
    <div class="jumbotron">
      <div class="col-sm-8 mx-auto">
        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <label for="form_name">Name *</label>
              <input
                id="form_name"
                type="text"
                v-model="name"
                class="form-control"
                placeholder="Vul je naam in *"
                required="required"
                data-error="Name is required."
              />
              <div class="help-block with-errors"></div>
            </div>
          </div>
          <div class="col-md-6">
            <div class="form-group">
              <label for="form_email">E-mail *</label>
              <input
                id="form_email"
                type="email"
                v-model="email"
                class="form-control"
                placeholder="Vul je e-mailaddress in *"
                required="required"
                data-error="E-mailaddress is required."
              />
              <div class="help-block with-errors"></div>
            </div>
          </div>
          <div class="col-md-12">
            <div class="form-group">
              <label for="form_message">Message *</label>
              <textarea
                id="form_message"
                class="form-control"
                placeholder="Voer je bericht in *"
                rows="4"
                v-model="message"
                required="required"
                data-error="Please, leave us a message."
              ></textarea>
              <div class="help-block with-errors"></div>
            </div>
          </div>
          <div class="col-md-12 d-flex justify-content-end">
            <button type="submit" @click="addMessage" class="btn btn-primary btn-send">Send message</button>
          </div>
        </div>
      </div>
    </div>
  </form>
</template>
<script>
import db from '../components/firebaseInit'

export default {
  data () {
    return {
      id: null,
      name: null,
      email: null,
      message: null
    }
  },
  methods: {
    addMessage () {
      db.collection('messages')
        .add({
          id: ++this.id,
          name: this.name,
          email: this.email,
          message: this.message
        })
        .then(docRef => {
          console.log('Client added: ', docRef.id)
        })
        .catch(error => {
          console.error('Error adding to database: ', error)
        })
    }
  }
}
</script>
