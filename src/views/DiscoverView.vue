<script>
export default {
  data(){
    return{
      usersSearched: [],
      searchbar: "",
    }
  }, 

  methods: {
    searchUsers(){
      const token = localStorage.getItem('token');
      const URL = 'http://puigmal.salle.url.edu/api/v2/users/search?s=' + this.searchbar;
      fetch(URL, {
        method: 'GET',
        headers:{
          'Authorization': 'Bearer ' + JSON.parse(token).accessToken,
          'Content-Type': 'application/json',
        },     
      })
      .then(res => res.json())
      .then(res=> {
        let response = JSON.stringify(res);
        if(response.length > 0) {
          this.usersSearched = res; //recorrer i transformar la imatge amb .map
          
          res.map((friend) => {
            if(this.checkURL(friend.image)){
              friend.image = friend.image;
            } else{
              friend.image = "src/assets/default_img.png";
            }  
          });



          /*res.map((friend) => {
            if(this.checkURL(friend.image)){
              friend.image = "src/assets/default_img.png";
            } else{
              friend.image = "src/assets/default_img.png";
            }  
          });*/

        }
      });
    },

    checkURL(url) {
      return(url.match(/\.(jpeg|jpg|gif|png)$/) != null);
    }

  },

  mounted(){
    this.searchUsers();
  }
  

}
</script>


<template>
  <!-- Main content -->
  <section id="discover-users-list-main">
    <!-- Users list header -->
    <h1 id="users-list-header">Users</h1>
    <!-- Searchbar -->
    <section id="users-searchbar" class="searchbar">
      <article id="users-searchbar-field" class="searchbar-field">
        <form action="">
          <!-- Bind input value to "searchbar" variable -->
          <input
          v-model="searchbar"
          v-on:input="searchUsers()"
          id="users-searchbar-placeholder"
          class="searchbar-placeholder"
          placeholder="Search"
          type="text">
        </form>
        <!--<button class="filters-show-button">Filters</button>-->
      </article>
    </section>
    <!-- Filters selector 
    <section id="users-filters-box" class="filters-box">
      <img
        src="../assets/filter-icon.svg"
        alt="Close filters"
        id="users-filters-close-button"
        class="filters-close-button"
      />
      <article class="filter">
        <p class="user-filter-text">Name</p>
      </article>
      <article class="filter">
        <p class="user-filter-text">Date</p>
      </article>
      <article class="filter">
        <p class="user-filter-text">Location</p>
      </article>
    </section>-->
    <!-- Users list -->
    <section id="users-list-section">
      <ul v-for="friend in usersSearched" v-bind:key="friend.id" v-on:click="this.$router.push('/profile/' + friend.id)">
        <li>
          <!-- v-on:click="this.$router.push('/vejeri/{friend.id}')" -->
          <article class="users-list-item"> 
            <img 
            onerror="this.src = 'src/assets/default_img.png'"
            class="users-list-item-picture" v-bind:src="friend.image" 
            alt="User's profile picture" />
            <h2 class="users-list-item-title">{{ friend.name + " " + friend.last_name }}</h2>
          </article>
        </li>
      </ul>
    </section>
  </section>
</template>

<style scoped>
#discover-users-list-main {
  padding: 20px 20px 40px 20px;
}

/* Searchbar */
#users-searchbar-field {
  min-width: 100%;
  flex-wrap: wrap;
  margin-bottom: 0px;
}

#users-searchbar-field > form,
button {
  margin-bottom: 10px;
}

/* Filters */
/* Will be hidden until "Filters" button is pressed
#users-filters-box {
  display: none;
}
*/

/* Users list */
#users-list-section {
  flex-wrap: wrap;
  display: flex;
  flex-direction: column;
  align-items: center;
}

/* Temporary style for ProfileView temporary link (will be done with JS later) */
#tmp-users-item-link {
  text-decoration: none;
  width: 85%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

#tmp-users-item-link > .users-list-item {
  width: 100%;
  color: #000;
}
/* End of temporary style */

.users-list-item {
  background: #fafafa;
  margin-top: 20px;
  margin-right: 10px;
  width: 380px;
  height: 80px;
  padding: 10px;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  border-radius: 12px;
  box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.1);
}

.users-list-item:hover {
  cursor: pointer;
  box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.3);
}

.users-list-item-picture {
  max-width: 15%;
  width: auto;
  height: fit-content;
  border-radius: 12px;
  margin-right: 15px;
}

.users-list-item-picture:empty {
  font-size: 1.2vmin;
}

.users-list-item-title {
  font-size: 3.5vmin;
}

/* Adapt to device */
@media (min-width: 768px) {
  #discover-users-list-main {
    padding-bottom: 50px;
    padding-right: 30px;
  }

  #users-searchbar-field {
    flex-wrap: nowrap;
    margin-bottom: 10px;
  }

  #users-searchbar-field > form,
  button {
    margin-bottom: 0px;
  }
}

@media (min-width: 882px) {
  #users-list-section {
    flex-direction: row;
    justify-content: space-between;
  }

  /* Temporary style for ProfileView temporary link (will be done with JS later) */
  #tmp-users-item-link {
    display: block;
    width: 45%;
  }
  /* End of temporary style */

  /*.users-list-item {
    width: 45%;
  }*/

  .users-list-item-title {
    font-size: 2vmin;
  }

  ul {
    list-style-type: none;
    padding: 0;
    margin: 0;
  }

}
</style>
