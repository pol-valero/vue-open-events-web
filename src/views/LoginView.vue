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
    padding: 30px;    
    width: 300px;
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

.icon_message {
    background: url(src/assets/icon_lock.svg) no-repeat scroll left;
    background-size: 20px;
    padding-left:30px;
    background-color: white;
    border-radius: 10px;
    margin-bottom: 7px;
    margin-top: 15px;
    padding-block: 7px;
    padding-inline: 30px;
}

.icon_lock {
    background: url(src/assets/icon_message.svg) no-repeat scroll;
    background-size: 20px;
    background-position: 0px;
    padding-left:30px;
    background-color: white;
    border-radius: 10px;
    margin-bottom: 5px;
    padding-block: 7px;
    padding-inline: 30px;
}

#image-box{
    display: flex;
    justify-content:center;
    margin-top: 130px;
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

</style>
<template>
    <body>
        <main>
            <div id="image-box">
                <img id="logo-image" src="src/assets/logo_wildframe.svg">
            </div>

            <div id="main-login-box">
                <div class="login-box">
                    <form action="">
                        <h1>Login</h1>
                            <input class="icon_message" type="text" name="email" id="email" required placeholder="abc@email.com">        
                            <input class="icon_lock" type="text" name="password" id="password" required placeholder="Your password">        
                        <div>
                            <input id="button-sign-in" type="submit" value="Sign In">        
                        </div>
                        <div>
                            <label>¿Not registered? </label>
                            <!-- TEMPORAL -->
                            <a id="nav-signup" href="/">Signup</a>
                            <!-- TEMPORAL -->
                        </div>
                    </form>
                </div>
            </div>

        </main>
    </body>
</template>