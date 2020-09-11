<template>
  <div class="stations">
    <div class="continent" v-for="item in data.radios" v-bind:key="item">
        <div @click="openCountries(item.continent_id)" class="continent-title">
            {{ item.continent_name }} <i class="fa fa-chevron-down"></i>
        </div>
        <div :id="`countries-${ item.continent_id }`" class="countries">
            <div class="country" v-for="country in item" v-bind:key="country">
                <div @click="openRadios(country.country_id)" class="country-title">
                    {{ country.country_name }} <i v-if="country.country_name" class="fa fa-chevron-down"></i>
                </div>
                <div :id="`radios-${ country.country_id }`" class="radios">
                    <div class="radio" v-for="radio in country" v-bind:key="radio.id">
                        <div class="radio-name">
                            <a @click="$emit('change-radio', radio)">    
                                {{ radio.name }}
                            </a>
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
    name: 'Stations',
    props: ['data'],
    methods: {
        openRadios(id) {
            let radios = document.getElementById(`radios-${id}`);
            if (radios.classList.contains('opened')) {
                radios.classList.remove('opened')
            } else {
                radios.classList.add('opened');
            }
        },
        openCountries(id) {
            let countries = document.getElementById(`countries-${id}`);
            if (countries.classList.contains('opened')) {
                countries.classList.remove('opened');
            } else {
                countries.classList.add('opened');
            }
        } 
    }
}
</script>

<style>
.stations {
    color: #fff;
    font-family: 'Teko', sans-serif;
    height: 285px;
    overflow-y: auto;
    margin-left: 5%;
    margin-top: 5%;
}

.continent-title {
    font-size: 32px;
}

.continent-title:hover {
    cursor: pointer;
}

.continent-title::selection {
    background-color: #84C2C0;
}

.fa-chevron-down {
    font-size: 24px;
    margin-left: 5px;
}

.country-title {
    font-size: 24px;
}

.country-title:hover {
    cursor: pointer;
}

.country-title::selection {
    background-color: #84C2C0;
}

.countries {
    display: none;
    margin-left: 10px;
}

.radios {
    display: none;
}

.radio-name:hover {
    cursor: pointer;
}

.opened {
    display: block;
}
</style>