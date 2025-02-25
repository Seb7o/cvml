<template>
    <div class="container mx-auto p-4">
        <div class="flex gap-4">
            <CVEditor v-model="cvData" />
            <CVPreview :cvData="cvData" />
        </div>
    </div>
    <CVPreviewHuman :cvData="cvData" />
</template>

<script>
import { ref, onMounted } from 'vue';
import CVEditor from './CVEditor.vue';
import CVPreview from './CVPreview.vue';
import CVPreviewHuman from './CVPreviewHuman.vue';
import schema from '../assets/schema.json';

export default {
    components: { CVEditor, CVPreview, CVPreviewHuman },
    setup() {
        const cvSchema = ref(null);
        const cvData = ref({
            personal_info: {
                first_name: "John",
                last_name: "Doe",
                email: "",
                phone: "",
                photo: "",
                websites: []
            },
            experiences: [],
            skills: [],
            education: [],
            languages: [],
            projects: [],
            references: [],
        });

        onMounted(() => {
            cvSchema.value = JSON.parse(JSON.stringify(schema)); // Clone pour éviter de modifier directement le fichier
            console.log(cvSchema.value)
        });

        return { cvData, cvSchema };
    }
};
</script>
