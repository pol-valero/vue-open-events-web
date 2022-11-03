<style>
.login-box{
    display: flex;
    padding: 30px;    
    width: 300px;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    
    text-align: center;
    background-color: rgb(203, 208, 206);
    border-radius: 10px;
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
    margin-bottom: 5px;
}

.icon_lock {
    background: url(src/assets/icon_message.svg) no-repeat scroll;
    background-size: contain;
    padding-left:30px;
    background-color: white;
    border-radius: 10px;
    margin-bottom: 5px;
}

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

</style>

<template>
    <body>
        <main>
            <div class="login-box">
                <form action="">
                    <h1>Login</h1>
                        <input class="icon_message" type="text" name="email" id="email" required placeholder="abc@email.com">        
                        <input class="icon_lock" type="text" name="password" id="password" required placeholder="Your password">        
                    <div>
                        <input type="submit" value="Sign In">        
                    </div>
                    <div>
                        <label>¿Not registered? </label>
                        <a id="nav-signup" href="/signup">Signup</a>
                    </div>
                </form>
            </div>
        </main>
    </body>
</template>