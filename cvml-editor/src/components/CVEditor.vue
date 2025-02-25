<template>
    <div class="w-1/2 bg-base-900 p-4 shadow text-left rounded-lg">
      <form @submit.prevent>
        
        <label class="block">Prénom: <input v-model="cvData.personal_info.first_name" class="input input-bordered w-full"></label>
        <label class="block">Nom: <input v-model="cvData.personal_info.last_name" class="input input-bordered w-full"></label>
        <label class="block">Email: <input v-model="cvData.personal_info.email" type="email" class="input input-bordered w-full"></label>
        <label class="block">Téléphone: <input v-model="cvData.personal_info.phone" type="tel" class="input input-bordered w-full"></label>
        <label class="block">Photo (URL): <input v-model="cvData.personal_info.photo" class="input input-bordered w-full"></label>
        <label class="block">Résumé: <input v-model="cvData.sumary" type="text" class="input input-bordered w-full"></label>
        
        <h3 class="text-lg font-semibold mt-4">Sites Web</h3>
        <div v-for="(website, index) in cvData.personal_info.websites" :key="index" class="flex gap-2 items-center">
          <input v-model="cvData.personal_info.websites[index]" class="input input-bordered w-full">
          <button @click.prevent="removeWebsite(index)" class="btn btn-error">X</button>
        </div>
        <button @click.prevent="addWebsite" class="btn btn-primary mt-2">Ajouter un site</button>


        <h3 class="text-lg font-semibold mt-4">Expériences</h3>
        <div v-for="(experience, index) in cvData.experiences" :key="index" class="flex gap-2 items-center">
          <input v-model="cvData.experiences[index].company" placeholder="Entreprise" class="input input-bordered w-full">
          <input v-model="cvData.experiences[index].title" placeholder="Titre" class="input input-bordered w-full">
          <input v-model="cvData.experiences[index].start_date" placeholder="Début" class="input input-bordered w-full">
          <input v-model="cvData.experiences[index].end_date" placeholder="Fin" class="input input-bordered w-full">
          <input v-model="cvData.experiences[index].location" placeholder="Lieu" class="input input-bordered w-full">
          <input v-model="cvData.experiences[index].description" placeholder="Description" class="input input-bordered w-full">
          <button @click.prevent="removeExperience(index)" class="btn btn-error">X</button>
        </div>
        <button @click.prevent="addExperience" class="btn btn-primary mt-2">Ajouter une expérience</button>
        
        <h3 class="text-lg font-semibold mt-4">Compétences</h3>
        <div v-for="(skill, index) in cvData.skills" :key="index" class="flex gap-2 items-center">
          <input v-model="cvData.skills[index].name" placeholder="Nom" class="input input-bordered w-full">
          <input v-model="cvData.skills[index].level" placeholder="Niveau (optionnel)" class="input input-bordered w-full">
          <button @click.prevent="removeSkill(index)" class="btn btn-error">X</button>
        </div>
        <button @click.prevent="addSkill" class="btn btn-primary mt-2">Ajouter une compétence</button>

        <h3 class="text-lg font-semibold mt-4">Diplomes</h3>
        <div v-for="(degree, index) in cvData.education" :key="index" class="flex gap-2 items-center">
          <input v-model="cvData.education[index].institution" placeholder="Institution" class="input input-bordered w-full">
          <input v-model="cvData.education[index].degree" placeholder="Niveau" class="input input-bordered w-full">
          <button @click.prevent="removeEducation(index)" class="btn btn-error">X</button>
        </div>
        <button @click.prevent="addEducation" class="btn btn-primary mt-2">Ajouter un diplome</button>

        <h3 class="text-lg font-semibold mt-4">Langues</h3>
        <div v-for="(language, index) in cvData.languages" :key="index" class="flex gap-2 items-center">
          <input v-model="cvData.languages[index].language" placeholder="Langue" class="input input-bordered w-full">
          <input v-model="cvData.languages[index].level" placeholder="Niveau" class="input input-bordered w-full">
          <button @click.prevent="removeLanguage(index)" class="btn btn-error">X</button>
        </div>
        <button @click.prevent="addLanguage" class="btn btn-primary mt-2">Ajouter une langue</button>

        <h3 class="text-lg font-semibold mt-4">Projets</h3>
        <div v-for="(project, index) in cvData.projects" :key="index" class="flex gap-2 items-center">
          <input v-model="cvData.projects[index].name" placeholder="Nom" class="input input-bordered w-full">
          <input v-model="cvData.projects[index].description" placeholder="Description" class="input input-bordered w-full">
          <input v-model="cvData.projects[index].url" placeholder="url" class="input input-bordered w-full">
          <button @click.prevent="removeProject(index)" class="btn btn-error">X</button>
        </div>
        <button @click.prevent="addProject" class="btn btn-primary mt-2">Ajouter un Projet</button>

        <h3 class="text-lg font-semibold mt-4">Réferences</h3>
        <div v-for="(reference, index) in cvData.references" :key="index" class="flex gap-2 items-center">
          <input v-model="cvData.references[index].name" placeholder="Nom" class="input input-bordered w-full">
          <input v-model="cvData.references[index].company" placeholder="Entreprise" class="input input-bordered w-full">
          <input v-model="cvData.references[index].email" placeholder="email" class="input input-bordered w-full">
          <button @click.prevent="removeReference(index)" class="btn btn-error">X</button>
        </div>
        <button @click.prevent="addReference" class="btn btn-primary mt-2">Ajouter une Réference</button>
      </form>
    </div>
  </template>
  
  <script>
  import { defineComponent } from 'vue';
  
  export default defineComponent({
    props: ['modelValue'],
    computed: {
      cvData: {
        get() { return this.modelValue; },
        set(value) { this.$emit('update:modelValue', value); }
      }
    },
    methods: {
      addExperience() { this.cvData.experiences.push({ company: "", title: "", start_date: "", end_date: "", location: "", description: "", skills: [] }); },
      removeExperience(index) { this.cvData.experiences.splice(index, 1); },
      addWebsite() { this.cvData.personal_info.websites.push(""); },
      removeWebsite(index) { this.cvData.personal_info.websites.splice(index, 1); },
      addSkill() { this.cvData.skills.push({ name: "", level: "" }); },
      removeSkill(index) { this.cvData.skills.splice(index, 1); },
      addEducation() { this.cvData.education.push({ institution: "", degree: "" }); },
      removeEducation(index) { this.cvData.education.splice(index, 1); },
      addLanguage() { this.cvData.languages.push({ language: "", level: "" }); },
      removeLanguage(index) { this.cvData.languages.splice(index, 1); },
      addProject() { this.cvData.projects.push({ name: "", description: "", url: "" }); },
      removeProject(index) { this.cvData.projects.splice(index, 1); },
      addReference() { this.cvData.references.push({ name: "", company: "", email: "" }); },
      removeReference(index) { this.cvData.references.splice(index, 1); }
    }
  });
  </script>
  