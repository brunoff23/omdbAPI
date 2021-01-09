<template>
  <div id="details">
        <div class="columns is-multiline" v-if="info != null && show == false">
            <div class="column is-6 is-offset-3 has-text-centered">
                <strong>Detalhes do filme</strong>
            </div>
            <div class="column is-6 is-offset-3 has-background-dark has-text-link-light">   
                <article class="media">
                    <div class="media-left">
                        <figure class="image is-128x128">
                            <img v-bind:src="info.Poster">
                        </figure>
                    </div>
                    <div class="media-content">
                        <div class="content">
                            <p>Título: {{info.Title}}</p>
                            <small>Lançamento: {{info.Released}} / {{info.Country}} -- Tempo: {{info.Runtime}}</small>
                            <p>Sinopse: {{info.Plot}}</p>
                            <p>Diretor: {{info.Director}}</p>
                            <p>Atores: {{info.Actors}}</p>
                            
                        </div>
                    </div>
                </article>
            </div>
        </div>
  </div>
</template>

<script>
export default {
    name: "Details",
    props: {
        info: Object,
        show: Boolean
    }
}
</script>

<style>

</style>