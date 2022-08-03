<template>
  <div class="flex flex-col mb-2">
    <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
      <div class="py-2 align-middle inline-block min-w-full sm:px-6 lg:px-8">
        <div class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg">
          <table class="min-w-full divide-y divide-gray-200">
            <thead class="bg-gray-100">
              <tr>
                <th scope="col" class="col-label text-left">Character</th>
                <th scope="col" class="col-label text-center">Score</th>
                <th scope="col" class="col-label text-center">DOS</th>
                <th scope="col" class="col-label text-center">HOA</th>
                <th scope="col" class="col-label text-center">MISTS</th>
                <th scope="col" class="col-label text-center">PF</th>
                <th scope="col" class="col-label text-center">SD</th>
                <th scope="col" class="col-label text-center">SOA</th>
                <th scope="col" class="col-label text-center">NW</th>
                <th scope="col" class="col-label text-center">TOP</th>
                <th scope="col" class="col-label text-center">STRT</th>
                <th scope="col" class="col-label text-center">GMBT</th>
                <th scope="col" class="col-label text-center"></th>
              </tr>
            </thead>
            
            <tbody class="bg-white divide-y divide-gray-200">  
              <tr v-for="character in characters">
                <td class="px-6 py-4 whitespace-nowrap">
                  <div class="flex items-center">
                    <div class="flex-shrink-0 h-10 w-10">
                      <img class="h-10 w-10 rounded-full" :src="character.thumbnail_url" alt="Character thumbnail">
                    </div>
                    <div class="ml-4">
                      <div class="text-sm font-medium text-gray-900">
                        {{ character.name }}
                      </div>
                      <div class="text-sm text-gray-500">
                        {{ character.class }} - {{ character.active_spec_name }}
                      </div>
                    </div>
                  </div>
                </td>
                <td class="key-levels whitespace-nowrap">
                  <div class="text-sm text-gray-900">Total</div>
                  <div class="text-sm" :style="{'color': character.mythic_plus_scores_by_season[0].segments.all.color}">{{ Math.round(character.mythic_plus_scores_by_season[0].segments.all.score) }}</div>
                </td>
                <td class="key-levels whitespace-nowrap">
                  <div class="flex flex-col">
                    <span class="best-run">
                      {{ character.mythic_plus_best_runs.find(x => x.short_name === 'GMBT').mythic_level }} {{ character.mythic_plus_best_runs.find(x => x.short_name === 'GMBT').affixes[0].name == "Fortified" ? "(F)" : "(T)" }}
                    </span>
                    <span class="alternative-run">
                      N/A
                    </span>
                  </div>
                </td>
                <td class="px-6 py-4 whitespace-nowrap text-center text-sm font-medium">
                  <a :href="character.profile_url" class="text-indigo-600 hover:text-indigo-900">Profile</a>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    const ryoca = await $axios.$get(`https://raider.io/api/v1/characters/profile?region=eu&realm=draenor&name=ryoca&fields=mythic_plus_best_runs%2Cmythic_plus_alternate_runs%2Cmythic_plus_scores_by_season%3Acurrent`)
    const smedn = await $axios.$get(`https://raider.io/api/v1/characters/profile?region=eu&realm=draenor&name=smedn&fields=mythic_plus_best_runs%2Cmythic_plus_alternate_runs%2Cmythic_plus_scores_by_season%3Acurrent`)
    
    const characters = [ryoca, smedn]
    
    characters.sort(function (a, b) {
      return b.mythic_plus_scores_by_season[0].segments.all.score - a.mythic_plus_scores_by_season[0].segments.all.score;
    });
	
    return { characters }
  }
}
</script>
