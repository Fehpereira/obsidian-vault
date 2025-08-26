## # F7 CSS Modules

Para utilizar o CSS Modules é necessário criar um arquivo css com a extensão '.modules.css', depois importar no ==componente== que deseja utilizar essa estilização e por fim colocar a classe que estará dentro do objeto ==style==, por exemplo:

![[Pasted image 20250515210221.png]]

## # F23 Entendendo a Key

![[Pasted image 20250520203449.png]]

---

## # F34 Styled Components

![[Pasted image 20250528215550.png]]

## # F36 Tipagem de temas

![[Pasted image 20250613171030.png]]
![[Pasted image 20250613180059.png]]

---

## # F37 Estilos globais



---

## # F38 Cores e fontes

![[Pasted image 20250613181523.png]]
![[Pasted image 20250613181537.png]]

---

## # F39 Configurando ESLint

![[Pasted image 20250613183154.png]]

---

## # F40 React Router DOM

`npm i react-router-dom`
![[Pasted image 20250616162721.png]]

---

## # F41 Layout de rotas

![[Pasted image 20250616163714.png]]
![[Pasted image 20250616163828.png]]
![[Pasted image 20250616163929.png]]

---

## # F42 Header & Layout

![[Pasted image 20250616170104.png]]

---

## # F43 Página Home

Code.

---

## # F45 Aprimorando os inputs

![[Pasted image 20250616185523.png]]
![[Pasted image 20250616185525.png]]

---

## # F47 Components Status

![[Pasted image 20250618102408.png]]
![[Pasted image 20250618103019.png]]
![[Pasted image 20250618103130.png]]
![[Pasted image 20250618103158.png]]
![[Pasted image 20250618103306.png]]

---

## # F48 Controlled vs Uncontrolled

Sim, trabalhar com **inputs controlados** em React (mesmo com o Next.js mais atual, como o 14 ou superior) **pode impactar a performance** se for um formulário grande, **especialmente** se você tiver muitos campos e re-renderizações constantes a cada digitação.

### 🔍 O que são inputs controlados?

Inputs controlados são aqueles cujo valor é gerenciado via estado React:

```tsx
const [name, setName] = useState("");

<input value={name} onChange={(e) => setName(e.target.value)} />
```

Cada alteração de valor dispara uma atualização de estado, que causa **re-renderização do componente**.

---

### 💥 Potenciais problemas de performance em grandes formulários:

1. **Muitos estados**: Cada campo pode criar e atualizar seu próprio estado, tornando o componente "inchado".
    
2. **Re-renderizações desnecessárias**: Mesmo que um campo seja alterado, o componente inteiro (ou parte grande dele) pode ser re-renderizado.
    
3. **Latência na digitação**: Em formulários com dezenas ou centenas de campos, o tempo entre digitar e ver o texto no campo pode aumentar (lag).
    

---

### ✅ O que mudou nas versões mais recentes (React 18/19, Next 13/14)?

1. **React 18 introduziu o Concurrent Mode e transições** (com `startTransition`), que ajudam em alguns casos de performance, mas **não resolvem o problema de excesso de re-renderizações causadas por inputs controlados**.
    
2. **React 19 (em beta)** adiciona **`useFormStatus`, `useFormState`, `useActionState`** e outras APIs para lidar com formulários em apps Server Components (como no Next 14+). Mas essas APIs são **voltadas mais para formulários do tipo `useFormAction()`**, submissão e feedback, e não para digitação em tempo real.
    

---

### 🚀 Boas práticas para evitar problemas:

1. **Use `useMemo`, `React.memo` ou `useCallback`** para evitar re-renderizações desnecessárias.
    
2. **Evite `input` controlado se não precisar dele**. Use `ref` com `uncontrolled input` se só precisar do valor no submit:
    
    ```tsx
    const inputRef = useRef();
    <input ref={inputRef} />
    ```
    
3. **Divida o formulário** em subcomponentes menores que se re-renderizem separadamente.
    
4. Use bibliotecas otimizadas como:
    
    - [`react-hook-form`](https://react-hook-form.com/): mantém performance alta mesmo com muitos inputs.
        
    - `Formik` ou `Final Form` (menos performáticas que react-hook-form).
        

---

### 📌 Conclusão

Sim, **inputs controlados ainda podem causar gargalos de performance** em formulários grandes, mesmo nas versões modernas do React e Next.js. Mas com boas práticas e bibliotecas adequadas, você consegue **mitigar ou evitar completamente esses problemas**.

Se quiser, posso te mostrar um exemplo comparando input controlado vs. `react-hook-form` ou com `ref` não-controlado. Deseja isso?

---

## # F49 React Hook Form

`npm i react-hook-form`

![[Pasted image 20250618112146.png]]
![[Pasted image 20250618112200.png]]

---

## # F50 Validando formulários

`npm i zod`
`npm i @hookform/resolvers`

![[Pasted image 20250618121511.png]]
![[Pasted image 20250618121529.png]]

---

## # F51 TypeScript no formulário

![[Pasted image 20250618130940.png]]

---

## # F52 Resetando formulário

![[Pasted image 20250618131701.png]]

Limpa os formulários com o valor inicial definido no zod.

---

## # F53 Iniciando novo ciclo

---

## # F54 Criando CountDown

``` tsx
const Home = () => {

  const [cycles, setCycles] = useState<Cycle[]>([])

  const [activeCycleId, setActiveCycleId] = useState<string | null>(null)

  const [amountSecondsPassed, setAmountSecondsPassed] = useState(0)

  

  const { register, handleSubmit, watch, reset } = useForm({

    resolver: zodResolver(newCycleSchemaValidationSchema),

    defaultValues: {

      task: '',

      minutesAmount: 0,

    },

  })

  

  function handleCreateNewCycle(data: NewCycleFormData) {

    const id = String(new Date().getTime())

    const newCycle: Cycle = {

      id,

      task: data.task,

      minutesAmount: data.minutesAmount,

    }

  

    setCycles((state) => [...state, newCycle])

    setActiveCycleId(id)

  

    reset()

  }

  

  const activeCycle = cycles.find((cycle) => cycle.id === activeCycleId)

  

  const totalSeconds = activeCycle ? activeCycle.minutesAmount * 60 : 0

  const currentSeconds = activeCycle ? totalSeconds - amountSecondsPassed : 0

  

  const minutesAmount = Math.floor(currentSeconds / 60)

  const secondsAmount = currentSeconds % 60

  

  const minutes = String(minutesAmount).padStart(2, '0')

  const seconds = String(secondsAmount).padStart(2, '0')

  

  const task = watch('task')

  const isSubmitDisabled = !task

  

  return (

    <HomeContainer>

      <form onSubmit={handleSubmit(handleCreateNewCycle)}>

        <FormContainer>

          <label htmlFor="task">Vou trabalhar em</label>

          <TaskInput

            id="task"

            type="text"

            list="task-suggestions"

            placeholder="Dê um nome para o seu projeto"

            {...register('task')}

          />

  

          <datalist id="task-suggestions">

            <option value="Projeto 1" />

            <option value="Projeto 2" />

            <option value="Projeto 3" />

            <option value="Banana" />

          </datalist>

  

          <label htmlFor="minutesAmount">durante</label>

          <MinutesAmountInput

            id="minutesAmount"

            type="number"

            placeholder="00"

            step={5}

            min={5}

            max={60}

            required

            {...register('minutesAmount', { valueAsNumber: true })}

          />

  

          <span>minutos.</span>

        </FormContainer>

  

        <CountdownContainer>

          <span>{minutes[0]}</span>

          <span>{minutes[1]}</span>

          <Separator>:</Separator>

          <span>{seconds[0]}</span>

          <span>{seconds[1]}</span>

        </CountdownContainer>

  

        <StartCountdownButton disabled={isSubmitDisabled} type="submit">

          <Play size={24} />

          Começar

        </StartCountdownButton>

      </form>

    </HomeContainer>

  )

}

  

export default Home
```

---

## # F55 Hook useEffect

**Por quê?**

1. **Menor quantidade de renders e lógica reativa**:
    
    - No **Código 1**, `items.find()` é feito uma vez por render. O React apenas reavalia o componente se `items` mudar **por fora** (via contexto).
        
    - No **Código 2**, o `useEffect` **força** um `setState` (`setShowItem`) sempre que `idItem` ou `items` mudarem, o que **dispara uma re-renderização adicional** do componente.
        
2. **Evita estado desnecessário**:
    
    - No **Código 1**, não há estado local ou compartilhado desnecessário. Apenas calcula o item dinamicamente e exibe.
        
    - No **Código 2**, o item é salvo no contexto com `setShowItem`, o que adiciona **mais complexidade e custo de memória**.
        
3. **Menos complexidade na montagem e desmontagem**:
    
    - O **Código 2** precisa de um `cleanup` para limpar `showItem`, o que **não traz benefício real aqui** e adiciona mais lógica para manter.


---

## # F58 Interromper Ciclo

![[Pasted image 20250620135152.png]]

---

## # F59 Ciclo Completo

![[Pasted image 20250620140842.png]]

---

## # F60 Separando componentes

Ok

---

## # F61 Prop Drilling no React

![[Pasted image 20250620145741.png]]
![[Pasted image 20250620145813.png]]

---

## # F63 Convertendo para contexto

Ok

---

## # F64 Contexto no formulário

Ok

---

## # F65 Contexto entre rotas

Ok

---

## # F66 Reset do formulário

![[Pasted image 20250623122032.png]]

---

## # F67 Listagem do histórico

![[Pasted image 20250623122854.png]]

---

## # F68 Formatação de data

![[Pasted image 20250623123448.png]]
![[Pasted image 20250623123503.png]]

---

## # F69 Criando reducer de ciclos

![[Pasted image 20250624114810.png]]
![[Pasted image 20250624114958.png]]

---
## # F70 Salvando um objeto no Reducer

![[Pasted image 20250624122453.png]]

---

## # F71 Marcando ciclo como finalizado

![[Pasted image 20250624123110.png]]

---

## # F72 Separando Action Types

![[Pasted image 20250624172518.png]]

---

## # F73 Separando Actions

![[Pasted image 20250624174632.png]]

---

## # F74 Utilizando immer

![[Pasted image 20250626103422.png]]
![[Pasted image 20250626105752.png]]
![[Pasted image 20250626105820.png]]

---

## # F75 Salvando estado no storage

![[Pasted image 20250626120408.png]]

---

## # F76 Corrigindo listagem de histórico

![[Pasted image 20250626120940.png]]

---


