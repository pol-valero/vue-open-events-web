<template>
    <div id="image-box">
        <img id="logo-image" src="src/assets/logo_image.png">
    </div>

    <div id="main-register-box">
        <div class="register-box">
            <form action="">
                <h1>Signup</h1>
                <input class="input-user-name" type="text" name="name" id="name" required placeholder="Name">            
                <input class="input-user-lastname" type="text" name="last-name" id="last-name" required placeholder="Last Name">            
                <input class="input-user-email input-margin" type="text" name="email" id="email" required placeholder="abc@email.com">            
                <input class="input-password input-margin" type="password" name="password" id="password" required placeholder="Password">            
                <input class="input-confirm-password input-margin" type="password" name="confirm-password" id="confirm-password" required placeholder="Confirm Password">            
                <input class="input-birth-date input-margin" type="text" name="birth-date" id="birth-date" required placeholder="Birth date">            
                <input class="input-profile-picture input-margin" type="text" name="profile-picture" id="profile-picture" required placeholder="Profile picture">            
                
                <div>
                    <input id="button-sign-up" type="submit" value="Register">        
                </div>
                <div>
                    <label>Already registered? </label>
                    <RouterLink id="nav-signup" to="/login">Login</RouterLink>
                </div>
            </form>
        </div>
    </div>
</template>

<style scoped>

.input-margin{
    margin: 10px;
}
.register-box{
    display: flex;
    padding: 30px;    
    width: 500px;
    justify-content:center;
    text-align: center;
    background-color: rgb(203, 208, 206);
    border-radius: 10px;
    margin-top: 100px;
    margin-bottom: 100px;
}

#main-register-box{
    display: flex;
    justify-content:center;
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

#button-sign-up{
    background-color: black;
    color: white;
    border-radius: 10px;
    height: 30px;
    width: 170px;
    margin: 10px;
    
}

#button-sign-up:hover {
    background-color: #5a5a5a;
    transition: 0.4s;
}


#nav-signup{
    border: none;
    background: none;
    text-decoration: none;
    color: #25d366;
}

#nav-signup:hover {
    color: black;
    transition: 0.4s;
    cursor: pointer;
}



@media (max-width: 530px) {
    .input-user-name {
        margin-right: 0px;
    }

    .register-box{
        width: 220px;
    }
    
    #image-box{
        padding-bottom: 0px;
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