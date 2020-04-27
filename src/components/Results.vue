
// <template>
  <div class="results">
    <h1>
      Top Movies from the 20
      <sup>th</sup> Century
    </h1>

    <p class="search-meta">
      <span class="current-page">
        <b>Current Page:</b>{{ page }}
      </span>

      <span class="total-pages">
        <b>Total Pages:</b>{{ total_pages }}
      </span>

      <span class="total-results">
        <b>Count:</b>{{ total_results }}
      </span>

    </p>

    <ul>
      <li class="movie-item" v-for="result in results" :key="result.title">

         <img 
          src="https://image.tmdb.org/t/p/w150_and_h225_bestv2/p64TtbZGCElxQHpAMWmDHkWJlH2.jpg"
          alt="Title of Movie Poster"
          class="poster-image"
        />

        <!-- TODO: Combine base URL with poster_path value in data to make the image src URL (Hint: Use v-bind.). -->

        <h2 class="title">
          <a href="https://www.themoviedb.org/movie/78">{{ result.title }}</a>
        </h2>

        <!-- TODO: Combine base URL with movie ID value in data to make the link href URL (Hint: Use v-bind.). -->
        
        
        <div class="ratings"> 
          <span class="rating-category critics-choice" v-if="result.vote_average >=8">Critic's Choice</span>
          

          <span class="rating-category well-liked" v-else-if="result.vote_average >=7 || result.vote_average <8">Well Liked</span>

          <span class="rating-category stinker" v-else>Stinker</span>
          

          <span class="vote-average">{{ result.vote_average }}</span> with
          <span class="vote-count">{{ result.vote_count }}</span> votes
          
        </div>

        <p class="overview">{{ result.overview }}</p>

        <p class="release-date">{{ result.release_date }}</p>
       

        <ul class="genre-list">
          <li v-for="genre in results.genres" v-bind:class="genre" v-bind:key="genre">{{ genres }}
          
          <li>{{ result.genres }}</li>
         
        </ul>
      </li>
    </ul>
  </div>
</template>

<script>
import apiresults from "../assets/apiresults.js";
export default {
  data() {
    return apiresults;
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  margin: 0 0 1rem 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
.search-meta {
  text-align: right;
}
.movie-item {
  margin: 10px 0;
  padding: 2rem;
  box-shadow: 4px 4px 10px rgba(0, 0, 0, 0.2);
}
.movie-item img {
  float: left;
  margin-right: 1rem;
}
.release-date {
  font-weight: 600;
  font-size: 12px;
  color: #333;
}
.rating-category {
  font-size: 12px;
  color: #fff;
  font-weight: 800;
  background: #ccc;
  padding: 0.5rem;
  border-radius: 4px;
}
.rating-category.critics-choice {
  background: goldenrod;
}
.rating-category.well-liked {
  background: green;
}
.rating-category.stinker {
  background: brown;
}
.genre-list li {
  border-radius: 4px;
  background: #666;
  color: #fff;
  font-weight: 800;
  font-size: 12px;
  padding: 0.5rem;
  display: inline-block;
  margin-right: 10px;
}
a {
  color: #42b983;
}
</style>