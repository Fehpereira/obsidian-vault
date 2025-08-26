let a = document.getElementById('area')

  

function clicar (){

    a.innerText = 'Clicou!'

    a.style.backgroundColor = 'blue'

    a.style.color= 'red'

}

function entrar (){

    a.innerText = 'Olá, mundo!!'

    a.style.backgroundColor = 'red'

    a.style.color = 'white'

}

function sair (){

    a.innerText = 'Tchau, mundo!!'

    a.style.backgroundColor= 'green'

    a.style.color = 'white'

}

a.addEventListener('click', clicar)

a.addEventListener('mouseenter', entrar)

a.addEventListener('mouseout', sair)