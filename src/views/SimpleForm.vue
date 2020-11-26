<template>
  <div>
    <h1>Create an event</h1>
    <form>

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
        <BaseRadio
          name="pets"
          label="Yes"
          v-model="event.pets"
          :value="1"
        >
        </BaseRadio>
      </div>

      <div>
        <BaseRadio
          name="pets"
          label="No"
          v-model="event.pets"
          :value="0"
        >
        </BaseRadio>
      </div>

      <h3>Extras</h3>
      <div>
        <BaseCheckbox
          v-model="event.extras.catering"
          label="Catering"
        >
        </BaseCheckbox>
      </div>

      <div>
        <BaseCheckbox
          v-model="event.extras.music"
          label="Live music"
        >
        </BaseCheckbox>
      </div>

      {{ event }}

      <button class="button -fill-gradient" type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
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
  }
}
</script>
