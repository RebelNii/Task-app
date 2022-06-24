<template>
    <div class="footer">
        <footer>
            <div class="f1">
                <input id="news" type="text" name="Newsletter" placeholder="Newsletter"><br>
                <button>Register</button>
            </div>
            <div class="f2">
                <input id="sign" type="text" name="footer" placeholder="Sign up">
                <button>Sign-up</button>
            </div>
            <div class="f3">
                <p><router-link to="/home">Home</router-link></p>
                <p><router-link to="/about">About</router-link></p>
                <p><a href="/contact">Contact Us</a></p>
            </div>
        </footer>
    </div>
</template>

<script>
export default{
    name: 'app-footer',
    data() {
        return {

        }
    }
}

</script>


<style scoped>
    .footer footer{
        display: grid;
        grid-template-columns: repeat(3,1fr);
        padding: 10px;
        gap: 20px;
        overflow: hidden;
        margin: 0 10px;
    }

    .footer footer .f1{
        justify-content: center;
        align-content: center;
    }

    .footer footer .f1 #news{
        width: 100%;
        border-radius: 1px 1px;
        padding: 10px;
        margin: 10px 0;
        outline: none;
    }

    .footer footer .f1 button{
        width: 100%;
        color: #fff;
        background: #333;
        cursor: pointer;
        border: none;
        padding: 10px;
        margin: 10px 0;
        border-radius: 3px;
    }

    .footer footer .f2 #sign{
        width: 100%;
        border-radius: 1px 1px;
        padding: 10px;
        margin: 10px 0;
        outline: none;
    }

    .footer footer .f2 button{
        width: 100%;
        color: #fff;
        background: #333;
        cursor: pointer;
        border: none;
        padding: 10px;
        margin: 10px 0;
        border-radius: 3px;
    }

    .footer footer .f3 p {
        margin: 3px;
        padding: 5px; 
    }

    .footer footer .f3 p a{
        text-decoration: none;
        color: #333;
        text-transform:uppercase;
    }
</style>