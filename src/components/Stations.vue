<template>
  <div class="stations">
    <div class="continent" v-for="item in data.radios" v-bind:key="item">
        <div class="continent-title">
            {{ item.continent_name }} <i class="fa fa-chevron-down"></i>
        </div>
        <div class="country" v-for="country in item" v-bind:key="country">
            <div class="country-title">
                {{ country.country_name }}
            </div>
            <div class="radios">
                <div class="radio" v-for="radio in country" v-bind:key="radio.id">
                    <div class="radio-name">
                        {{ radio.name }}
                    </div>
                </div>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
    name: 'Stations',
    props: ['data']
}
</script>

<style>
.stations {
    color: #fff;
    font-family: 'Teko', sans-serif;
}

.continent-title {
    font-size: 32px;
}

.fa-chevron-down {
    font-size: 24px;
    margin-left: 5px;
}

.country-title {
    font-size: 24px;
}
</style>