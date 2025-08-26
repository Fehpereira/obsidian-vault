Document Object Model

==Exemplo de Árvore DOM==

![[Pasted image 20250122220742.png]]

==Acessando o html pelo DOM==

document.getElementsByTagName('p')[0] // vou selecionar o primeiro parágrafo do meu HTML
document.getElementById() 
document.getElementsByName()[]
document.getElementsByClassName()[]
let dom = document.querySelector('div#msg') // posso omitir o 'div'

OBS: sempre que tiver ''Elements'' no plural desta forma, é necessário usar o colchetes para selecionar o/os elementos desejados por sua ordem.