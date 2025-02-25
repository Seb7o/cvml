<template>
    <div class="max-w-4xl mx-auto p-8 bg-base-100 shadow-lg rounded-xl border border-gray-300 grid grid-cols-3 gap-6">
      <!-- Left Column -->
      <div class="col-span-1 bg-gray-100 p-6 rounded-lg">
        <!-- Header -->
        <div class="text-center mb-6">
          <img :src="cvData.personal_info.photo" alt="Photo" class="w-24 h-24 rounded-full border-2 border-gray-400 mx-auto" />
          <h1 class="text-2xl font-bold mt-4">{{ cvData.personal_info.first_name }} {{ cvData.personal_info.last_name }}</h1>
          <p class="text-gray-600 text-sm">{{ cvData.sumary }}</p>
        </div>
        
        <!-- Contact Info -->
        <div class="mb-4">
          <h2 class="text-lg font-semibold border-b pb-2">Contact</h2>
          <p class="text-sm text-gray-700">{{ cvData.personal_info.email }}</p>
          <p class="text-sm text-gray-700">{{ cvData.personal_info.phone }}</p>
        </div>
        
        <!-- Skills -->
        <div class="mb-4">
          <h2 class="text-lg font-semibold border-b pb-2">Compétences</h2>
          <ul class="mt-2 list-disc ml-4 text-sm text-gray-700">
            <li v-for="skill in cvData.skills" :key="skill.name">{{ skill.name }} ({{ skill.level }})</li>
          </ul>
        </div>
        
        <!-- Languages -->
        <div class="mb-4">
          <h2 class="text-lg font-semibold border-b pb-2">Langues</h2>
          <ul class="mt-2 list-disc ml-4 text-sm text-gray-700">
            <li v-for="lang in cvData.languages" :key="lang.language">{{ lang.language }} ({{ lang.level }})</li>
          </ul>
        </div>
      </div>
  
      <!-- Right Column -->
      <div class="col-span-2">
        <!-- Experience -->
        <div class="mb-6">
          <h2 class="text-xl font-semibold border-b pb-2">Expérience</h2>
          <div v-for="exp in cvData.experience" :key="exp.company" class="mt-4">
            <h3 class="font-semibold text-lg">{{ exp.title }} - {{ exp.company }}</h3>
            <p class="text-sm text-gray-500">{{ exp.start_date }} - {{ exp.end_date }} | {{ exp.location }}</p>
            <p class="text-sm text-gray-700 whitespace-pre-line">{{ exp.description }}</p>
            <p class="text-sm text-gray-600 mt-2">Skills: {{ exp.skills.join(", ") }}</p>
          </div>
        </div>
        
        <!-- Education -->
        <div class="mb-6">
          <h2 class="text-xl font-semibold border-b pb-2">Éducation</h2>
          <ul class="mt-2 text-sm text-gray-700">
            <li v-for="edu in cvData.education" :key="edu.institution">{{ edu.degree }} - {{ edu.institution }}</li>
          </ul>
        </div>
  
        <!-- Projects -->
        <div class="mb-6">
          <h2 class="text-xl font-semibold border-b pb-2">Projets</h2>
          <ul class="mt-2 text-sm text-gray-700">
            <li v-for="project in cvData.projects" :key="project.name">
              <a :href="project.url" class="text-primary font-medium" target="_blank">{{ project.name }}</a>: {{ project.description }}
            </li>
          </ul>
        </div>
  
        <!-- References -->
        <div>
          <h2 class="text-xl font-semibold border-b pb-2">Références</h2>
          <ul class="mt-2 text-sm text-gray-700">
            <li v-for="ref in cvData.references" :key="ref.email">
              {{ ref.name }}, {{ ref.company }} - <a :href="'mailto:' + ref.email" class="text-primary">{{ ref.email }}</a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { defineProps } from 'vue';
  
  defineProps({
    cvData: {
      type: Object,
      required: true
    }
  });
  </script>
  