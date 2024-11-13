<template>
    <div class="mx-auto px-4 sm:px-6 lg:px-8 my-5">
      <div class="bg-white shadow-xl rounded-lg overflow-hidden">
        <div class="sm:flex sm:items-center sm:justify-between">
          <div class="flex flex-col gap-4 h-full w-1/3 justify-center rounded-lg shadow">
                <img src="/public/images/CV Informatique Elie Lajoinie.png" alt="avatar"/>
          </div>
          <div class="flex flex-col px-6 py-8 sm:p-10 z-0 w-2/3 gap-4">
            <h1 class="text-4xl font-bold text-gray-900">Ce que je recherche</h1>
            <p class=" text-xl font-medium text-gray-900">
                Je suis actuellement à la recherche d'un poste d'alternant développeur Fullstack Junior ou développeur d'Applications Junior. Je suis prêt à m'investir dans une alternance de 12 mois, avec un rythme de deux semaines en entreprise et deux semaines en formation, jusqu'à septembre prochain.
            </p>
            <a 
              href="/public/other/CV%20Fullstack%20Elie%20Lajoinie.pdf" 
              download="CV Lajoinie Elie.pdf" 
              class="self-center text-center w-1/2 py-3 bg-gray-200 text-gray-700 rounded-full text-sm download-btn z-1">
              Télécharger mon CV
            </a>
          </div>
        </div>
      </div>
    </div>
</template>

<style lang="scss" scoped>
.download-btn {
    position: relative;
    overflow: hidden;
    transition: color 0.3s ease;
}

.download-btn::before {
    @apply absolute flex top-0 w-full h-full -left-full bg-gray-800 text-center items-center justify-center z-0 text-white;
    content: "Télécharger mon CV";
    transition: left 0.5s ease;
}

.download-btn:hover::before {
    left: 0;
}

.download-btn > * {
    position: relative;
}
</style>