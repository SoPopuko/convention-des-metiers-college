<template>
    <div class="relative z-10" aria-labelledby="modal-title" role="dialog" aria-modal="true">
      <div class="fixed inset-0 z-10 w-screen overflow-y-auto">
        <div class="flex justify-center p-4 text-center">
          <div class="relative transform overflow-hidden rounded-lg bg-white text-left shadow-xl transition-all my-36 w-full h-48 max-w-lg bg-orange-200">
            <div class="px-4 pb-4 pt-5">
                <div class="text-center mt-10">
                  <div v-if="victory === 1" class="text-3xl font-semibold leading-6 text-gray-900" id="modal-title">Bravo !</div>
                  <div v-if="victory === 2" class="text-3xl font-semibold leading-6 text-gray-900" id="modal-title">Pas de chance ! !</div>
                  <div class="mt-4">
                    <p v-if="victory === 1" class="text-lg text-gray-500">Félicitations, tu as gagné !</p>
                    <p v-if="victory === 2" class="text-lg text-gray-500">Dommage, tu as perdu !</p>
                  </div>
                </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>

  <script>
  export default {
    props: {
      victory: {
        type: Number,
        required: true,
      },
    },
  };
  </script>
