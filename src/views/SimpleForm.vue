<template>
  <div>
    <h1>Create an event</h1>
    <form @submit.prevent="sendForm">

      <BaseSelect
        v-model="event.category"
        label="Select a category"
        :options="categories"
      ></BaseSelect>

      <h3>Name & describe your event</h3>

      <BaseInput
        v-model="event.title"
        label="Title"
        type="text"
      ></BaseInput>

      <BaseInput
        v-model="event.description"
        label="Description"
        type="text"
      ></BaseInput>

      <h3>Where is your event?</h3>

      <BaseInput
        v-model="event.location"
        label="Location"
        type="text"
      ></BaseInput>

      <h3>Are pets allowed?</h3>
      <div>
        <BaseRadioGroup
          v-model="event.pets"
          :options="petOptions"
          name="pets"
        ></BaseRadioGroup>
      </div>

      <h3>Extras</h3>
      <div>
        <BaseCheckbox
          v-model="event.extras.catering"
          label="Catering"
        ></BaseCheckbox>
      </div>

      <div>
        <BaseCheckbox
          v-model="event.extras.music"
          label="Live music"
        ></BaseCheckbox>
      </div>

      {{ event }}

      <button class="button -fill-gradient" type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      categories: [
        'sustainability',
        'nature',
        'animal welfare',
        'housing',
        'education',
        'food',
        'community'
      ],
      petOptions: [
        { value: 1, label: 'Yes' },
        { value: 0, label: 'No' }
      ],
      event: {
        category: '',
        title: '',
        description: '',
        location: '',
        pets: 1,
        extras: {
          catering: false,
          music: false
        }
      }
    }
  },
  methods: {
    sendForm () {
      axios.post(
        'https://my-json-server.typicode.com/Code-Pop/Vue-3-Forms/events',
        this.event
      )
        .then(function (response) {
          console.log('Response', response)
        })
        .catch(function (err) {
          console.log('Error', err)
        })
    }
  }
}
</script>
