<template>
    <div class="mx-auto px-4 sm:px-6 lg:px-8 mt-7 mb-10">
      <div class="bg-white shadow-xl rounded-lg overflow-hidden">
        <div class="flex w-full items-center justify-between lg:flex-row max-lg:flex-col max-lg:items-center max-lg:justify-center max-lg:text-center">
          <div class="flex flex-col gap-4 h-full lg:w-1/3 max-lg:w-full justify-center rounded-lg shadow">
                <img src="/static/images/CV Informatique Elie Lajoinie.png" alt="avatar"/>
          </div>
          <div class="flex flex-col px-6 py-8 sm:p-10 z-0 lg:w-2/3 max-lg:w-full max-lg:justify-center max-lg:text-center gap-4">
            <h1 class="title">Ce que je recherche</h1>
            <p class="text-xl font-medium text-gray-900">
                Je suis actuellement à la recherche d'un poste d'alternant développeur Fullstack Junior ou développeur d'Applications Junior. Je suis prêt à m'investir dans une alternance de 12 mois, avec un rythme de deux semaines en entreprise et deux semaines en formation, jusqu'à septembre prochain.
            </p>
            <h1 class="title text-end">Pourquoi moi ?</h1>
            <p class="text-xl font-medium text-gray-900">
                Passioné par le développement informatique, je suis toujours prêt à redéfinir mes limites avec de nouveaux projets de plus en plus complexes. Mon approche se concentre autant sur la technique que sur le sens : j’aime comprendre en profondeur ce que je fais et pourquoi, et cette réflexion guide mes choix de développement.
            </p>
            <p class="text-xl font-medium text-gray-900">
              Organisé et rigoureux, je veille à ce que mon travail soit structuré et facile à maintenir.
              Mon objectif est de créer des applications fiables, bien codées et intuitives pour les utilisateurs.
            </p>
            <p class="text-xl font-medium text-gray-900">
              J’ai également à cœur de partager mes connaissances : j’aime aider les autres à comprendre, car je crois qu’un bon développeur contribue non seulement au code, mais aussi à l’équipe qui l’entoure.
            </p>
            <a 
              href="/other/CV_Fullstack_Elie_Lajoinie.pdf.pdf" 
              download="CV Fullstack Elie Lajoinie.pdf" 
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