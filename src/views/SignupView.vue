<style scooped>

aside{
    display: none
}

header{
    display: none
}

footer{
    display: none
}

body{
    border: 0px;
}

.login-box{
    display: flex;

    padding: 30px;    
    width: 500px;
    margin-top: 50px;
    text-align: center;
    background-color: rgb(203, 208, 206);
    border-radius: 10px;
}

#main-login-box{
    display: flex;
    justify-content:center;
}


body{
    background-color: rgb(255, 255, 255);
}

.input-user-name {
    background: url(src/assets/icon_user.svg) no-repeat scroll left;
    background-size: 20px;
    background-position: 8px;
    padding-left:30px;
    background-color: white;
    border-radius: 10px;
    margin-bottom: 7px;
    margin-top: 15px;
    padding-block: 7px;
    padding-inline: 40px;
    margin-right: 10px;
}

.input-user-lastname {
    background: url(src/assets/icon_user.svg) no-repeat scroll;
    background-size: 20px;
    background-position: 8px;
    background-color: white;
    border-radius: 10px;
    margin-bottom: 5px;
    padding-block: 7px;
    padding-inline: 40px;
}

.input-user-email {
    background: url(src/assets/icon_message.svg) no-repeat scroll;
    background-size: 20px;
    background-position: 8px;
    background-color: white;
    border-radius: 10px;
    margin-bottom: 5px;
    padding-block: 7px;
    width: 395px;
    padding-inline: 40px;
}

.input-password{
    background: url(src/assets/icon_lock.svg) no-repeat scroll;
    background-size: 20px;
    background-position: 8px;
    background-color: white;
    border-radius: 10px;
    margin-bottom: 5px;
    padding-block: 7px;
    width: 395px;
    padding-inline: 40px;
}

.input-confirm-password{
    background: url(src/assets/icon_lock.svg) no-repeat scroll;
    background-size: 20px;
    background-position: 8px;
    background-color: white;
    border-radius: 10px;
    margin-bottom: 5px;
    padding-block: 7px;
    width: 395px;
    padding-inline: 40px;
}

.input-birth-date{
    background: url(src/assets/icon_calendar.svg) no-repeat scroll;
    background-size: 20px;
    background-position: 8px;
    background-color: white;
    border-radius: 10px;
    margin-bottom: 5px;
    padding-block: 7px;
    width: 395px;
    padding-inline: 40px;
}

.input-profile-picture{
    background: url(src/assets/icon_image.svg) no-repeat scroll;
    background-size: 20px;
    background-position: 8px;
    background-color: white;
    border-radius: 10px;
    margin-bottom: 5px;
    padding-block: 7px;
    width: 395px;
    padding-inline: 40px;
}

#image-box{
    display: flex;
    justify-content:center;
    padding-top: 80px;
    padding-bottom: 20px;
}

#logo-image{
    width: 100px;
    height: 100px;
    scale: 2;
}

#button-sign-in{
    background-color: black;
    color: white;
    border-radius: 10px;
    height: 30px;
    width: 170px;
    margin: 10px;
}


#nav-signup{
  border: none;
  background: none;
  text-decoration: none;
  color: black;
}

#nav-login:hover {
  color: #25d366;
  transition: 0.4s;
  cursor: pointer;
}

#center-screen {
    padding-bottom: 0px;
}


#nav-login{
  border: none;
  background: none;
  text-decoration: none;
  color: black;
}

#nav-login:hover {
  color: #25d366;
  transition: 0.4s;
  cursor: pointer;
}

#center-screen {
    padding-bottom: 0px;
}

@media (max-width: 530px) {
    .input-user-name {
        margin-right: 0px;
    }

    .input-user-email ,
    .input-password ,
    .input-confirm-password ,
    .input-birth-date ,
    .input-profile-picture
    {
        width: 150px;
        padding-inline: 40px;
    }

}

</style>
<template>
    <body>
        <main>
            <div id="image-box">
                <a href="/">
                <!--TEMPORAL NAV -->
                    <img id="logo-image" src="src/assets/logo_image.png">
                </a>
            </div>

            <div id="main-login-box">
                <div class="login-box">
                    <form action="">
                        <h1>Signup</h1>
                        <input class="input-user-name" type="text" name="name" id="name" required placeholder="Name">            
                        <input class="input-user-lastname" type="text" name="last-name" id="last-name" required placeholder="Last Name">            
                        <input class="input-user-email" type="text" name="email" id="email" required placeholder="abc@email.com">            
                        <input class="input-password" type="text" name="password" id="password" required placeholder="Password">            
                        <input class="input-confirm-password" type="text" name="confirm-password" id="confirm-password" required placeholder="Confirm Password">            
                        <input class="input-birth-date" type="text" name="birth-date" id="birth-date" required placeholder="Birth date">            
                        <input class="input-profile-picture" type="text" name="profile-picture" id="profile-picture" required placeholder="Profile picture">            
                        <div>
                            <input id="button-sign-in" type="submit" value="Register">        
                        </div>
                        <div>
                            <label>¿Already registered? </label>
                            <a id="nav-login" href="/login">Login</a>
                        </div>
                    </form>
                </div>
            </div>

        </main>
    </body>
</template>