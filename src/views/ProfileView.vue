<style>
#profile-main{
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: row;
    display: block;
}

#profile-title{
    margin-bottom: 20px;
}

#statistics-title{
    margin-bottom: 20px;
    margin-top: 20px;
}

#profile-img{
    width: 250px;
    height: 250px;
}

.main-container {
    display: flex;
    flex-direction: row;
}

.info-container{
    padding-left: 50px;
}
.info-title{
    padding-bottom: 20px;
    padding-top: 20px;
}



.statistics-container{
    display: flex;
    flex-direction: row;

    justify-content:space-around;
    padding: 20px;
}

.button-container{
    display: flex;
    flex-direction: row;

    justify-content:space-evenly;
    padding: 7px;
}

.edit-button{
    padding: 10px;
}   


.logout-button{
    padding: 10px;
    background-color: black;
    color:aliceblue;
}   

.info-component{
    text-align:center; 
}

.info-component h2{

}

.info-component h3{
    font-size: 15px;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}

#container-full-profile{
    margin: 20px;
}


</style>

<template>
    <div id="profile-main">
        <section id="container-full-profile">

            <h1 id="profile-title">
                Profile
            </h1>

            <div class="main-container">
                <div class="profile-info">
                    <img id="profile-img" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAOEAAADhCAMAAAAJbSJIAAAAHlBMVEX09PTh4eH19fXg4ODk5OTw8PDs7Ozq6uru7u7n5+dZKxXMAAAELUlEQVR4nO2dWXKtMAwFwQMX9r/hB9RNMOARhCTyTv/kIxVQl4kHYZmuAwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADgAsZ03o9eA6OfwyH360bXWz30kyd2HHvbq8LaibQdJ2V+C7Yf6RSdQsEZOxApGqWCsyJNK5qPVsEZCsHOS1tksBNFI2rsZTY8gaG0QxaCRjRj0ITS4/wvW0judguaKbjaID1f+xLEZG8/psZtV6OeKF3GbH2DHW9fbDN0WgTn/j0wvBtVYEjSM9MAwxZgKAMMW4ChDLyGxoQ/eGA0NMYPk3O9c9PH80nyGZo1A/e9l3WEiZM8DxmeZm3GH/Ib1jFNXZna0AzntTFZcigPj2E8f2M/HIoshqkEFYsih+Fu7b9XZOhvWNow4bdw85YVMBjmkqg0Kb4sHG2YaUKaFF+W5w3zefDnO5vnR/wwPxXh8YwOw1Oaz4Pbmzct8ryhLxhe+EdsivRxw/RgePW2821a/uZ5w8ILt/auZp7Ct8Qqb9g6/17XKA3BKnhK227yswirjvZtPc22yqwN912jxW6bQGW87xrx93mCuoBfNWs7JkKqIuaYeWcf04brn3ey1ITMsXrK7F9oWD1Ft+pUxPyeFXB8L1I5aJYsRnKbTcM9E5utyleQzUTVz2eSu8mKYb8km5jbLleI+xUZ4cJ+wHzgr8jqFzY85iNnfPe0vJn5uVff8mamuKMzGzrn27Xu9+3a4Bu2JddsWc3Erv4NaeWe3HTw6t9yV246Tkev3bB6V3UyfOWGDdvGU/HrNmzbFx8X0GzYvPE/asA14l+hubIhqqC4DS+UbsQc9Bpeq005S2g1vFx8c7LQani5uuikIWhohnR5wI3yqaOHnOG8ZLQpxVv1YYd1p5jhuiZOKN4sgNsrShl+F/0xxfsVfjtFoRE/yGqcfkdQwhgqyrRhmLY5tiJJjWbwvkfEcJeXOjyoNEWoVrYND4m3UJGqyla2DU+ZxUCRqoxY1DCWOv3pbsjqpCUNo4LfVqQrBBc0jAquioaylF/OMCG4KlKW8j9vmBjxk4LUSLUhm6CUIZ+gkCGjoIwhp6CIIaughCGvoIAhsyC/Ibcg+4jPLsjdhvyCzIYCgryGEoK8hoV93u83lDn+i9VQ4iGFIQwrDN2fN/z7bQhDGMIQhjCEYdnwvxrxPyKnljIadn6QgNOwMxKwGgoDwxZgKAMMW4ChDE/N2kiCoyA4eYTgPO/t/PPluyc6COrICc5kDybZ1jodhPP+u4LFg1qkofjXyR9jIgzFaaKl84Rkoen9FDci1Tmb0h5JqM6gNFo7m2R5zgVFbd8kW5nHZzJOx0MowNqhHHiL4+h2H7ARZvl4HvUHAtfD1yfpycyX6TPSfwCxE8o+JXhADwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAs/ANyGFT0fw3sTAAAAABJRU5ErkJggg==" alt="logo">
                </div>


                <div class="info-container">
                    <h2 class="info-title">Name</h2>
                    <p class="user-name">Firstname Lastname</p>
                    <h2 class="info-title">Email</h2>
                    <p class="user-name">email@email.com</p>
                </div>

            </div>
        </section>

        <section id="container-full-profile">
            <h1 id="statistics-title">
                Statistics
            </h1>
            
            <div class="statistics-container">
                <div class="info-component">
                    <h2>7.5</h2>
                    <h3>rating</h3>
                </div>
                <div class="info-component">
                    <h2>201</h2>
                    <h3>comments</h3>
                </div>
                <div class="info-component">
                    <h2>38%</h2>
                    <h3>of users behind you</h3>
                </div>
            </div>
        </section>

        <section id="container-full-profile">
            <RouterLink to="/timeline">View timeline</RouterLink>
        </section>


        <section id="container-full-profile">
            <div class="button-container">
                <button class="logout-button">LOGOUT</button>
                <button class="edit-button">EDIT</button>
            </div>
        </section>

    </div>
</template>