<template>
  <div class="flex flex-col mb-2">
    <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
      <div class="py-2 align-middle inline-block min-w-full sm:px-6 lg:px-8">
        <div class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg">
          <table class="min-w-full divide-y divide-gray-200">
            <thead class="bg-gray-100">
              <tr>
                <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                  Character
                </th>
                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                  Score
                </th>
                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                  DOS
                </th>
                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                  HOA
                </th>
                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                  MISTS
                </th>
                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                  PF
                </th>
                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                  SD
                </th>
                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                  SOA
                </th>
                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                  NW
                </th>
                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                  TOP
                </th>
                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                  
                </th>
              </tr>
            </thead>
            <tbody class="bg-white divide-y divide-gray-200">  
            
              <tr v-for="character in characters">
                <td class="px-6 py-4 whitespace-nowrap">
                  <div class="flex items-center">
                    <div class="flex-shrink-0 h-10 w-10">
                      <img class="h-10 w-10 rounded-full" :src="character.thumbnail_url" alt="">
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
                <td class="px-6 py-4 whitespace-nowrap text-center">
                  <div class="text-sm text-gray-900">Total</div>
                  <div class="text-sm" :style="{'color': character.mythic_plus_scores_by_season[0].segments.all.color}">{{ Math.round(character.mythic_plus_scores_by_season[0].segments.all.score) }}</div>
                </td>
                <td class="items-center px-6 py-4 whitespace-nowrap text-center">
                  <div class="flex flex-col">
                    <span class="text-xs leading-5 font-semibold rounded-full bg-green-100 text-green-800 mb-2">
                      {{ character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').mythic_level ? character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').mythic_level : "N/A" }} {{ character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').affixes[0].name == "Fortified" ? "(F)" : "(T)" }}
                    </span>
                    <span class="text-xs leading-5 font-semibold rounded-full bg-blue-100 text-blue-800">
                      {{ character.mythic_plus_alternate_runs.find(x => x.short_name === 'DOS').mythic_level ? character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').mythic_level : "N/A" }} {{ character.mythic_plus_alternate_runs.find(x => x.short_name === 'DOS').affixes[0].name == "Fortified" ? "(F)" : "(T)" }}
                    </span>
                  </div>
                </td>
                <td class="items-center px-6 py-4 whitespace-nowrap text-center">
                  <div class="flex flex-col">
                    <span class="text-xs leading-5 font-semibold rounded-full bg-green-100 text-green-800 mb-2">
                      {{ character.mythic_plus_best_runs.find(x => x.short_name === 'HOA').mythic_level ? character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').mythic_level : "N/A" }} {{ character.mythic_plus_best_runs.find(x => x.short_name === 'HOA').affixes[0].name == "Fortified" ? "(F)" : "(T)" }}
                    </span>
                    <span class="text-xs leading-5 font-semibold rounded-full bg-blue-100 text-blue-800">
                      {{ character.mythic_plus_alternate_runs.find(x => x.short_name === 'HOA').mythic_level ? character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').mythic_level : "N/A" }} {{ character.mythic_plus_alternate_runs.find(x => x.short_name === 'HOA').affixes[0].name == "Fortified" ? "(F)" : "(T)" }}
                    </span>
                  </div>
                </td>
                <td class="px-6 py-4 whitespace-nowrap text-center">
                  <div class="flex flex-col">
                    <span class="text-xs leading-5 font-semibold rounded-full bg-green-100 text-green-800 mb-2">
                      {{ character.mythic_plus_best_runs.find(x => x.short_name === 'MISTS').mythic_level ? character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').mythic_level : "N/A" }} {{ character.mythic_plus_best_runs.find(x => x.short_name === 'MISTS').affixes[0].name == "Fortified" ? "(F)" : "(T)" }}
                    </span>
                    <span class="text-xs leading-5 font-semibold rounded-full bg-blue-100 text-blue-800">
                      {{ character.mythic_plus_alternate_runs.find(x => x.short_name === 'MISTS').mythic_level ? character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').mythic_level : "N/A" }} {{ character.mythic_plus_alternate_runs.find(x => x.short_name === 'MISTS').affixes[0].name == "Fortified" ? "(F)" : "(T)" }}
                    </span>
                  </div>
                </td>
                <td class="px-6 py-4 whitespace-nowrap text-center">
                  <div class="flex flex-col">
                    <span class="text-xs leading-5 font-semibold rounded-full bg-green-100 text-green-800 mb-2">
                      {{ character.mythic_plus_best_runs.find(x => x.short_name === 'PF').mythic_level ? character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').mythic_level : "N/A" }} {{ character.mythic_plus_best_runs.find(x => x.short_name === 'PF').affixes[0].name == "Fortified" ? "(F)" : "(T)" }}
                    </span>
                    <span class="text-xs leading-5 font-semibold rounded-full bg-blue-100 text-blue-800">
                      {{ character.mythic_plus_alternate_runs.find(x => x.short_name === 'PF').mythic_level ? character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').mythic_level : "N/A" }} {{ character.mythic_plus_alternate_runs.find(x => x.short_name === 'PF').affixes[0].name == "Fortified" ? "(F)" : "(T)" }}
                    </span>
                  </div>
                </td>
                <td class="px-6 py-4 whitespace-nowrap text-center">
                  <div class="flex flex-col">
                    <span class="text-xs leading-5 font-semibold rounded-full bg-green-100 text-green-800 mb-2">
                      {{ character.mythic_plus_best_runs.find(x => x.short_name === 'SD').mythic_level ? character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').mythic_level : "N/A" }} {{ character.mythic_plus_best_runs.find(x => x.short_name === 'SD').affixes[0].name == "Fortified" ? "(F)" : "(T)" }}
                    </span>
                    <span class="text-xs leading-5 font-semibold rounded-full bg-blue-100 text-blue-800">
                      {{ character.mythic_plus_alternate_runs.find(x => x.short_name === 'SD').mythic_level ? character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').mythic_level : "N/A" }} {{ character.mythic_plus_alternate_runs.find(x => x.short_name === 'SD').affixes[0].name == "Fortified" ? "(F)" : "(T)" }}
                    </span>
                  </div>
                </td>
                <td class="px-6 py-4 whitespace-nowrap text-center">
                  <div class="flex flex-col">
                    <span class="text-xs leading-5 font-semibold rounded-full bg-green-100 text-green-800 mb-2">
                      {{ character.mythic_plus_best_runs.find(x => x.short_name === 'SOA').mythic_level ? character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').mythic_level : "N/A" }} {{ character.mythic_plus_best_runs.find(x => x.short_name === 'SOA').affixes[0].name == "Fortified" ? "(F)" : "(T)" }}
                    </span>
                    <span class="text-xs leading-5 font-semibold rounded-full bg-blue-100 text-blue-800">
                      {{ character.mythic_plus_alternate_runs.find(x => x.short_name === 'SOA').mythic_level ? character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').mythic_level : "N/A" }} {{ character.mythic_plus_alternate_runs.find(x => x.short_name === 'SOA').affixes[0].name == "Fortified" ? "(F)" : "(T)" }}
                    </span>
                  </div>
                </td>
                <td class="px-6 py-4 whitespace-nowrap text-center">
                  <div class="flex flex-col">
                    <span class="text-xs leading-5 font-semibold rounded-full bg-green-100 text-green-800 mb-2">
                      {{ character.mythic_plus_best_runs.find(x => x.short_name === 'NW').mythic_level ? character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').mythic_level : "N/A" }} {{ character.mythic_plus_best_runs.find(x => x.short_name === 'NW').affixes[0].name == "Fortified" ? "(F)" : "(T)" }}
                    </span>
                    <span class="text-xs leading-5 font-semibold rounded-full bg-blue-100 text-blue-800">
                      {{ character.mythic_plus_alternate_runs.find(x => x.short_name === 'NW').mythic_level ? character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').mythic_level : "N/A" }} {{ character.mythic_plus_alternate_runs.find(x => x.short_name === 'NW').affixes[0].name == "Fortified" ? "(F)" : "(T)" }}
                    </span>
                  </div>
                </td>
                <td class="px-6 py-4 whitespace-nowrap text-center">
                  <div class="flex flex-col">
                    <span class="text-xs leading-5 font-semibold rounded-full bg-green-100 text-green-800 mb-2">
                      {{ character.mythic_plus_best_runs.find(x => x.short_name === 'TOP').mythic_level ? character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').mythic_level : "N/A" }} {{ character.mythic_plus_best_runs.find(x => x.short_name === 'TOP').affixes[0].name == "Fortified" ? "(F)" : "(T)" }}
                    </span>
                    <span class="text-xs leading-5 font-semibold rounded-full bg-blue-100 text-blue-800">
                      {{ character.mythic_plus_alternate_runs.find(x => x.short_name === 'TOP').mythic_level ? character.mythic_plus_best_runs.find(x => x.short_name === 'DOS').mythic_level : "N/A" }} {{ character.mythic_plus_alternate_runs.find(x => x.short_name === 'TOP').affixes[0].name == "Fortified" ? "(F)" : "(T)" }}
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
    const androl = await $axios.$get(`https://raider.io/api/v1/characters/profile?region=eu&realm=draenor&name=androl&fields=mythic_plus_best_runs%2Cmythic_plus_alternate_runs%2Cmythic_plus_scores_by_season%3Acurrent`)
    const ryoca = await $axios.$get(`https://raider.io/api/v1/characters/profile?region=eu&realm=draenor&name=ryoca&fields=mythic_plus_best_runs%2Cmythic_plus_alternate_runs%2Cmythic_plus_scores_by_season%3Acurrent`)
    const regnen = await $axios.$get(`https://raider.io/api/v1/characters/profile?region=eu&realm=draenor&name=regnen&fields=mythic_plus_best_runs%2Cmythic_plus_alternate_runs%2Cmythic_plus_scores_by_season%3Acurrent`)
    const gaidin = await $axios.$get(`https://raider.io/api/v1/characters/profile?region=eu&realm=draenor&name=gaidin&fields=mythic_plus_best_runs%2Cmythic_plus_alternate_runs%2Cmythic_plus_scores_by_season%3Acurrent`)
    const enkazin = await $axios.$get(`https://raider.io/api/v1/characters/profile?region=eu&realm=draenor&name=enkazin&fields=mythic_plus_best_runs%2Cmythic_plus_alternate_runs%2Cmythic_plus_scores_by_season%3Acurrent`)
    const enkamonk = await $axios.$get(`https://raider.io/api/v1/characters/profile?region=eu&realm=draenor&name=enkamonk&fields=mythic_plus_best_runs%2Cmythic_plus_alternate_runs%2Cmythic_plus_scores_by_season%3Acurrent`)
    const enkadk = await $axios.$get(`https://raider.io/api/v1/characters/profile?region=eu&realm=draenor&name=enkadk&fields=mythic_plus_best_runs%2Cmythic_plus_alternate_runs%2Cmythic_plus_scores_by_season%3Acurrent`)
    const pogbear = await $axios.$get(`https://raider.io/api/v1/characters/profile?region=eu&realm=draenor&name=pogbear&fields=mythic_plus_best_runs%2Cmythic_plus_alternate_runs%2Cmythic_plus_scores_by_season%3Acurrent`)
    const lamer = await $axios.$get(`https://raider.io/api/v1/characters/profile?region=eu&realm=draenor&name=lamer&fields=mythic_plus_best_runs%2Cmythic_plus_alternate_runs%2Cmythic_plus_scores_by_season%3Acurrent`)
    const konstanz = await $axios.$get(`https://raider.io/api/v1/characters/profile?region=eu&realm=draenor&name=konstanz&fields=mythic_plus_best_runs%2Cmythic_plus_alternate_runs%2Cmythic_plus_scores_by_season%3Acurrent`)
    const pogfel = await $axios.$get(`https://raider.io/api/v1/characters/profile?region=eu&realm=draenor&name=pogfel&fields=mythic_plus_best_runs%2Cmythic_plus_alternate_runs%2Cmythic_plus_scores_by_season%3Acurrent`)
    const knoof = await $axios.$get(`https://raider.io/api/v1/characters/profile?region=eu&realm=draenor&name=knoof&fields=mythic_plus_best_runs%2Cmythic_plus_alternate_runs%2Cmythic_plus_scores_by_season%3Acurrent`)
	  const characters = [androl, ryoca, regnen, gaidin, enkazin, enkamonk, enkadk, pogbear, lamer, konstanz, pogfel, knoof]
	
    return { characters }
  },
}
</script>
