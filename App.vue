<template>
  <div class="form-container">
    <h1>Formulaire d'inscription</h1>

    <form @submit.prevent="validerFormulaire" class="formulaire" novalidate>
      <div class="form-group">
        <label for="nom">Nom :</label>
        <input id="nom" v-model="form.nom" type="text" />
        <span v-if="erreurs.nom" class="erreur">{{ erreurs.nom }}</span>
      </div>

      <div class="form-group">
        <label for="prenom">Prénom :</label>
        <input id="prenom" v-model="form.prenom" type="text" />
        <span v-if="erreurs.prenom" class="erreur">{{ erreurs.prenom }}</span>
      </div>

      <div class="form-group">
        <label for="email">Email :</label>
        <input id="email" v-model="form.email" type="email" />
        <span v-if="erreurs.email" class="erreur">{{ erreurs.email }}</span>
      </div>

      <div class="form-group">
        <label>Sexe :</label>
        <div class="radio-group">
          <label>
            <input type="radio" value="Homme" v-model="form.sexe" />
            Homme
          </label>
          <label>
            <input type="radio" value="Femme" v-model="form.sexe" />
            Femme
          </label>
        </div>
        <span v-if="erreurs.sexe" class="erreur">{{ erreurs.sexe }}</span>
      </div>

      <div class="form-group">
        <label for="adresse">Adresse :</label>
        <input id="adresse" v-model="form.adresse" type="text" />
        <span v-if="erreurs.adresse" class="erreur">{{ erreurs.adresse }}</span>
      </div>

      <div class="form-group">
        <label for="codePostal">Code postal :</label>
        <input id="codePostal" v-model="form.codePostal" type="text" />
        <span v-if="erreurs.codePostal" class="erreur">{{ erreurs.codePostal }}</span>
      </div>

      <div class="form-group">
        <label for="ville">Ville :</label>
        <input id="ville" v-model="form.ville" type="text" />
        <span v-if="erreurs.ville" class="erreur">{{ erreurs.ville }}</span>
      </div>

      <div class="form-group">
        <label for="institut">Nom de l'institut :</label>
        <input id="institut" v-model="form.institut" type="text" />
        <span v-if="erreurs.institut" class="erreur">{{ erreurs.institut }}</span>
      </div>

      <div class="form-buttons">
        <button type="submit" class="btn btn-primary">Valider</button>
        <button type="button" @click="annulerFormulaire" class="btn btn-secondary">Annuler</button>
      </div>
    </form>

    <div v-if="formulaireValide" class="recapitulatif">
      <h2>Récapitulatif des informations :</h2>
      <p><strong>Nom :</strong> {{ form.nom }}</p>
      <p><strong>Prénom :</strong> {{ form.prenom }}</p>
      <p><strong>Email :</strong> {{ form.email }}</p>
      <p><strong>Sexe :</strong> {{ form.sexe }}</p>
      <p><strong>Adresse :</strong> {{ form.adresse }}</p>
      <p><strong>Code postal :</strong> {{ form.codePostal }}</p>
      <p><strong>Ville :</strong> {{ form.ville }}</p>
      <p><strong>Institut :</strong> {{ form.institut }}</p>
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue';

interface Form {
  nom: string;
  prenom: string;
  email: string;
  sexe: string;
  adresse: string;
  codePostal: string;
  ville: string;
  institut: string;
}

const form = reactive<Form>({
  nom: '',
  prenom: '',
  email: '',
  sexe: '',
  adresse: '',
  codePostal: '',
  ville: '',
  institut: '',
});

const erreurs = reactive<{
  nom: string;
  prenom: string;
  email: string;
  sexe: string;
  adresse: string;
  codePostal: string;
  ville: string;
  institut: string;
}>({
  nom: '',
  prenom: '',
  email: '',
  sexe: '',
  adresse: '',
  codePostal: '',
  ville: '',
  institut: '',
});

const formulaireValide = ref(false);

const validerFormulaire = () => {
  erreurs.nom = '';
  erreurs.prenom = '';
  erreurs.email = '';
  erreurs.sexe = '';
  erreurs.adresse = '';
  erreurs.codePostal = '';
  erreurs.ville = '';
  erreurs.institut = '';

  if (!form.nom) {
    erreurs.nom = 'Le nom est requis.';
  }
  if (!form.prenom) {
    erreurs.prenom = 'Le prénom est requis.';
  }
  if (!form.email) {
    erreurs.email = 'L’email est requis.';
  } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.email)) {
    erreurs.email = 'Veuillez saisir un email valide.';
  }
  if (!form.sexe) {
    erreurs.sexe = 'Veuillez sélectionner un sexe.';
  }
  if (!form.adresse) {
    erreurs.adresse = 'L’adresse est requise.';
  }
  if (!form.codePostal) {
    erreurs.codePostal = 'Le code postal est requis.';
  }
  if (!form.ville) {
    erreurs.ville = 'La ville est requise.';
  }
  if (!form.institut) {
    erreurs.institut = 'Le nom de l’institut est requis.';
  }

  // Vérifier s’il y a au moins un message d’erreur
  const hasError = Object.values(erreurs).some((msg) => msg !== '');
  formulaireValide.value = !hasError;
};

const annulerFormulaire = () => {
  form.nom = '';
  form.prenom = '';
  form.email = '';
  form.sexe = '';
  form.adresse = '';
  form.codePostal = '';
  form.ville = '';
  form.institut = '';

  formulaireValide.value = false;

  Object.keys(erreurs).forEach((key) => {
    erreurs[key] = '';
  });
};
</script>

<style scoped>
.form-container {
  max-width: 600px;
  margin: 40px auto;
  padding: 20px;
  background-color: #f9f9ff;
  border-radius: 8px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.form-container h1 {
  text-align: center;
  margin-bottom: 20px;
}

.formulaire {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.form-group {
  display: flex;
  flex-direction: column;
}

.form-group label {
  font-weight: 600;
  margin-bottom: 5px;
}

.radio-group {
  display: flex;
  gap: 15px;
  margin-top: 5px;
}

.form-group input[type="text"],
.form-group input[type="email"],
.form-group input[type="radio"] {
  padding: 8px;
  font-size: 1rem;
}

.form-buttons {
  display: flex;
  gap: 15px;
  margin-top: 10px;
}

.btn {
  padding: 10px 16px;
  font-size: 1rem;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.btn-primary {
  background-color: #4caf50;
  color: white;
}

.btn-secondary {
  background-color: #f44336;
  color: white;
}

.erreur {
  color: #ff0000;
  font-size: 0.85rem;
  margin-top: 5px;
}

.recapitulatif {
  margin-top: 30px;
  padding: 20px;
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.recapitulatif h2 {
  margin-bottom: 15px;
}
</style>