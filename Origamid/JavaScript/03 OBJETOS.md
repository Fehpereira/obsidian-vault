## # F0476 Constructor function 1

![[Pasted image 20250409165650.png]]
![[Pasted image 20250409165926.png]]
![[Pasted image 20250409170223.png]]

---

## # F0477 Constructor function 2

![[Pasted image 20250409094607.png]]
![[Pasted image 20250409095317.png]]

![[Pasted image 20250409095831.png]]![[Pasted image 20250409095921.png]]
![[Pasted image 20250409100107.png]]![[Pasted image 20250409100221.png]]
![[Pasted image 20250409100253.png]]
![[Pasted image 20250409101401.png]]

---

## # F0478 Prototype 1

![[Pasted image 20250409103955.png]]
![[Pasted image 20250409104216.png]]
![[Pasted image 20250409104355.png]]
![[Pasted image 20250409104630.png]]![[Pasted image 20250409104823.png]]
![[Pasted image 20250409104843.png]]
Em JavaScript, a diferença entre adicionar um método diretamente no construtor de uma função e adicioná-lo ao prototype da função é fundamental para entender como a herança e a otimização de memória funcionam na linguagem.

**Adicionando um método no construtor:**

- **Cada instância tem sua própria cópia:** Quando você define um método dentro do construtor, cada objeto criado a partir dessa função construtora terá sua própria cópia desse método. Isso significa que, se você criar 1000 objetos, terá 1000 cópias do mesmo método na memória.
- **Uso de memória:** Isso pode levar a um uso ineficiente de memória, especialmente se você tiver muitos objetos.
- **Escopo:** O método tem acesso ao escopo da função construtora, o que pode ser útil se ele precisar acessar propriedades específicas da instância.

**Adicionando um método ao prototype:**

- **Compartilhamento entre instâncias:** O prototype é um objeto compartilhado por todas as instâncias de uma função construtora. Quando você adiciona um método ao prototype, todas as instâncias podem acessar esse método sem precisar ter sua própria cópia.
- **Otimização de memória:** Isso economiza memória, pois você tem apenas uma cópia do método compartilhada por todos os objetos.
- **Herança:** O prototype é a base da herança prototípica em JavaScript. Quando você acessa uma propriedade ou método em um objeto, o JavaScript primeiro verifica se a propriedade ou método existe no próprio objeto. Se não existir, ele procura no prototype do objeto e, em seguida, no prototype do prototype, e assim por diante.
- **Desempenho:** Por não precisar criar várias copias de um mesmo método, o uso do prototype otimiza o desempenho do código.

**Em resumo:**

- Se você precisa que cada instância tenha seu próprio método exclusivo, adicione-o ao construtor.
- Se você deseja compartilhar um método entre todas as instâncias e otimizar o uso de memória, adicione-o ao prototype.

**Exemplo:**

JavaScript

```
function Pessoa(nome) {
  this.nome = nome;
  // Método no construtor (cada instância tem sua própria cópia)
  this.apresentar1 = function() {
    console.log("Meu nome é " + this.nome);
  };
}

// Método no prototype (compartilhado por todas as instâncias)
Pessoa.prototype.apresentar2 = function() {
  console.log("Meu nome é " + this.nome);
};

const pessoa1 = new Pessoa("Alice");
const pessoa2 = new Pessoa("Bob");

pessoa1.apresentar1(); // Saída: Meu nome é Alice
pessoa1.apresentar2(); // Saída: Meu nome é Alice
pessoa2.apresentar1(); // Saída: Meu nome é Bob
pessoa2.apresentar2(); // Saída: Meu nome é Bob
```

Neste exemplo, `apresentar1` é definido no construtor e `apresentar2` é definido no prototype. Ambas as instâncias podem acessar ambos os métodos, mas `apresentar2` é compartilhado entre elas, economizando memória.

Aqui estão os principais benefícios de usar o prototype:

- **Economia de memória:**
    - Como mencionado, ao adicionar um método ao prototype, você evita a criação de cópias duplicadas desse método para cada instância do objeto. Isso é especialmente importante quando você tem muitos objetos, pois pode economizar uma quantidade significativa de memória.
- **Herança prototípica:**
    - O prototype é a base da herança em JavaScript. Quando você acessa uma propriedade ou método em um objeto, o JavaScript primeiro verifica se essa propriedade ou método existe no próprio objeto. Se não existir, ele 1 procura no prototype do objeto e, em seguida, no prototype do prototype, e assim por diante. Isso permite que você crie hierarquias de objetos e compartilhe funcionalidades entre eles.  
        
        [
        
        1. creapardesenvolvimento.com.br
        
        ](https://creapardesenvolvimento.com.br/glossario/o-que-e-object-prototype-tecnologia/)
        
        [
        
        creapardesenvolvimento.com.br
        
        ](https://creapardesenvolvimento.com.br/glossario/o-que-e-object-prototype-tecnologia/)
        
- **Desempenho:**
    - Ao evitar a criação de cópias duplicadas de métodos, você também melhora o desempenho do seu código. A pesquisa de propriedades e métodos no prototype é geralmente mais rápida do que a pesquisa em objetos individuais.
- **Reutilização de código:**
    - O protótipo permite que você compartilhe métodos e propriedades entre vários objetos, promovendo a reutilização de código e tornando seu código mais organizado e fácil de manter.

Em resumo, embora a economia de memória seja uma vantagem importante, o prototype é uma ferramenta fundamental para a herança e a organização do código em JavaScript.

---

## # F0479 Prototype 2

![[Pasted image 20250409152416.png]]
![[Pasted image 20250409152740.png]]
![[Pasted image 20250409153255.png]]![[Pasted image 20250409153533.png]]
![[Pasted image 20250409153547.png]]
![[Pasted image 20250409154012.png]]

---

## # F0480 Prototype 3

![[Pasted image 20250409154315.png]]
![[Pasted image 20250409160239.png]]

---

## # F0481 Native, Host e User 1

![[Pasted image 20250409170659.png]]
![[Pasted image 20250409171048.png]]
![[Pasted image 20250409171106.png]]
![[Pasted image 20250409171124.png]]
![[Pasted image 20250409171250.png]]
![[Pasted image 20250409171500.png]]
![[Pasted image 20250409171623.png]]
![[Pasted image 20250409171836.png]]

---

## # F0482 Native, Host e User 2

![[Pasted image 20250409172108.png]]

---

## # F0483 String 1

![[Pasted image 20250409215314.png]]
![[Pasted image 20250409215436.png]]
![[Pasted image 20250409215535.png]]
![[Pasted image 20250409215636.png]]![[Pasted image 20250409215723.png]]
![[Pasted image 20250409215851.png]]
![[Pasted image 20250409215945.png]]
![[Pasted image 20250409220108.png]]
![[Pasted image 20250409220148.png]]
![[Pasted image 20250409220248.png]]

---

## # F0484 String 2

![[Pasted image 20250409220724.png]]
![[Pasted image 20250409221722.png]]
![[Pasted image 20250409222025.png]]
![[Pasted image 20250409222509.png]]
![[Pasted image 20250409222637.png]]

---

## # F0485 String 3

EXERCÍCIOS

---
## # F0486 Number e Math 1

![[Pasted image 20250410084511.png]]
![[Pasted image 20250410084533.png]]
![[Pasted image 20250410084649.png]]
![[Pasted image 20250410085112.png]]![[Pasted image 20250410085317.png]]
![[Pasted image 20250410085445.png]]
![[Pasted image 20250410085540.png]]
![[Pasted image 20250410085819.png]]

 ---
## # F0487 Number e Math 2


![[Pasted image 20250410090251.png]]

---

## # F0488 Array 1

![[Pasted image 20250410095940.png]]
![[Pasted image 20250410100011.png]]
![[Pasted image 20250410100209.png]]
![[Pasted image 20250410100413.png]]
![[Pasted image 20250410100428.png]]
![[Pasted image 20250410100637.png]]
![[Pasted image 20250410100619.png]]
![[Pasted image 20250410100827.png]]
![[Pasted image 20250410100935.png]]
![[Pasted image 20250410101005.png]]

---

## # F0489 Array 2


![[Pasted image 20250410102403.png]]
![[Pasted image 20250410102642.png]]![[Pasted image 20250410102958.png]]
![[Pasted image 20250410103043.png]]![[Pasted image 20250410103208.png]]
  ![[Pasted image 20250410103320.png]]
  ![[Pasted image 20250410103501.png]]

---

## # F0490 Array 3

EXERCICES

---

## # F0491 Array e iteração 1

![[Pasted image 20250410114832.png]]
![[Pasted image 20250410115050.png]]
![[Pasted image 20250410115154.png]]
![[Pasted image 20250410115211.png]]
![[Pasted image 20250410115453.png]]
![[Pasted image 20250410115510.png]]
![[Pasted image 20250410115525.png]]
![[Pasted image 20250410115835.png]]
![[Pasted image 20250410120256.png]]![[Pasted image 20250410120305.png]]
![[Pasted image 20250410120342.png]]
![[Pasted image 20250410120408.png]]

---

## # F0492 Array e iteração 2

==reduce==
![[Pasted image 20250410121917.png]]
![[Pasted image 20250410122250.png]]
![[Pasted image 20250410122326.png]]![[Pasted image 20250410122516.png]]

---

## # F0493 Array e iteração 3

![[Pasted image 20250410122859.png]]
![[Pasted image 20250410123101.png]]

---

## # F0494 Array e iteração 4

Exercices

---
## # F0495 Function 1

![[Pasted image 20250411123428.png]]
![[Pasted image 20250411123517.png]]
![[Pasted image 20250411123627.png]]
![[Pasted image 20250411123942.png]]
![[Pasted image 20250411124059.png]]
![[Pasted image 20250411124939.png]]
![[Pasted image 20250411125106.png]]![[Pasted image 20250411125241.png]]

---

## # F0496 Function 2

![[Pasted image 20250411130428.png]]
![[Pasted image 20250411130559.png]]![[Pasted image 20250411130637.png]]
![[Pasted image 20250411130940.png]]![[Pasted image 20250411130952.png]]
![[Pasted image 20250411131146.png]]

---
## # F0497 Function 3

Exercices

---
## # F0498 Object 1

![[Pasted image 20250411145051.png]]
![[Pasted image 20250411145151.png]]
![[Pasted image 20250411145724.png]]![[Pasted image 20250411145916.png]]
![[Pasted image 20250411150216.png]]

---

## # F0499 Object 2

![[Pasted image 20250411151522.png]]![[Pasted image 20250411151731.png]]
![[Pasted image 20250411151748.png]]
![[Pasted image 20250411151927.png]]![[Pasted image 20250411152038.png]]
![[Pasted image 20250411152254.png]]

---

## # F500 Object 3

![[Pasted image 20250411152645.png]]
![[Pasted image 20250411152702.png]]
![[Pasted image 20250411152837.png]]
![[Pasted image 20250411154507.png]]

---

## # F501 Object 4

Exercices

---

