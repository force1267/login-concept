<script>
    export let user = null

    let loggingIn = false
    let str = ""

    function handleInput(e) {
        let val = e.target.value.split('').map((v, i) => str[i] || v).join('')
        
        let userpass = val.split(' ')
        
        let user = userpass.shift()
        let pass = userpass.join(' ')

        if(e.target.value.endsWith(' ') && !pass) {
            return
        }

        let tpass = pass.split('').map(l => '*').join('')
        let tval = user + (tpass ? ' ' + tpass : '')

        e.target.value = tval
        str = val
    }

    async function login(e) {
        if(e.key !== 'Enter') {return}

        loggingIn = true
        let userpass = str.split(' ')
        
        let u = userpass.shift()
        let p = userpass.join(' ')
        if(!u || !p) {
            alert("Enter username and password")
            loggingIn = false
            return
        }
        try {
            let res = await fetch('/login').then(r=>r.json())
            await new Promise(r=>setTimeout(r, 1500))
            user = res.user
            str = ""
        } catch (err) {
            // alert("Couldn't Login")
            //debug
            user = { name: str.split(' ')[0] }; str=""
        } finally {
            loggingIn = false
        }
    }

</script>

<input type="text" class:str placeholder="username password" on:input={handleInput} on:keypress={login} disabled={loggingIn}>
<span class:str>Press Enter</span>

<style>
    input {
        width: 35rem;
        height: 5rem;
        font-size: x-large;
        padding: 0 3rem;
        text-align: center;
    }
    input.str {
        text-align: left;
    }
    span {
        display: none;
    }
    span.str {
        display: block;
        font-size: 2rem;
        color: rgb(104, 112, 112);
    }
</style>