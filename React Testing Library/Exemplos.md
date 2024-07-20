# Exemplos de Testes Unitários no React

## Exemplo 1: Formulário

Dada um componente de formulário:

```typescript
import { useRef, useState } from "react"
import { useAdicionarParticipante } from "../state/hook/useAdicionarParticipante"
import { useMensagemDeErro } from "../state/hook/useMensagemDeErro"
import './Formulario.css'

const Formulario = () => {

    const [nome, setNome] = useState('')

    const inputRef = useRef<HTMLInputElement>(null)

    const adicionarNaLista = useAdicionarParticipante()

    const mensagemDeErro = useMensagemDeErro()

    const adicionarParticipante = (evento: React.FormEvent<HTMLFormElement>) => {
        evento.preventDefault()
        adicionarNaLista(nome)
        setNome('')
        inputRef.current?.focus()
    }

    return (<form onSubmit={adicionarParticipante}>
        <div className="grupo-input-btn">
            <input
                ref={inputRef}
                value={nome}
                onChange={evento => setNome(evento.target.value)}
                type="text"
                placeholder="Insira os nomes dos participantes"
            />
            <button disabled={!nome}>Adicionar</button>
        </div>
        {mensagemDeErro && <p className="alerta erro" role="alert">{mensagemDeErro}</p>}
    </form>)
}

export default Formulario
```

Podemos testá-la com:

```typescript
import { fireEvent, render, screen } from "@testing-library/react";
import { RecoilRoot } from "recoil";
import Formulario from "./Formulario";
import { useAdicionarParticipante } from "../state/hook/useAdicionarParticipante";

jest.mock("../state/hook/useAdicionarParticipante");
const mockedUseAdicionarParticipante = useAdicionarParticipante as jest.Mock;

describe('Comportamento Formulário', () => {
   
    beforeEach(() => {
        mockedUseAdicionarParticipante.mockClear();
    });
    
    test('dado um formulário, quando o input não for preenchido, o botão deve estar desabilitado', () => {
        
        render(
            <RecoilRoot>
                <Formulario/>
            </RecoilRoot>
        )

        const input = screen.getByPlaceholderText("Insira os nomes dos participantes");
        const button = screen.getByRole('button');

        expect(input).toBeInTheDocument();
        expect(button).toBeDisabled();
    })

    test('dado um formulário, quando o input for preenchido, o botão deve estar habilitado', () => {
        render(
            <RecoilRoot>
                <Formulario/>
            </RecoilRoot>
        )

        const input = screen.getByPlaceholderText("Insira os nomes dos participantes");
        const button = screen.getByRole('button');

        fireEvent.change(input, {
            target: {
                value: 'Victor Silva'
            }
        })

        expect(input).toBeInTheDocument();
        expect(button).toBeEnabled();
    })   

    test('dado um formulário, quando o input for preenchido e o botão pressionado, o método de submit deve ser executado', () => {
        const adicionarNaListaMock = jest.fn();
        mockedUseAdicionarParticipante.mockReturnValue(adicionarNaListaMock);
        
        render(
            <RecoilRoot>
                <Formulario/>
            </RecoilRoot>
        )

        const input = screen.getByPlaceholderText("Insira os nomes dos participantes");
        const button = screen.getByRole('button');

        fireEvent.change(input, {
            target: {
                value: 'Victor Silva'
            }
        })

        fireEvent.click(button);
        
        expect(input).toHaveFocus();
        expect(input).toHaveValue("") ;
        expect(adicionarNaListaMock).toHaveBeenCalled();
    })   
})
```

## Exemplo 2: Rodapé

Dado um componente de rodapé: 

```typescript
import { useNavigate } from "react-router-dom"
import { useListaDeParticipantes } from "../state/hook/useListaDeParticipantes"
import { useSorteador } from "../state/hook/useSorteador"

import './Rodape.css'

const Rodape = () => {

    const participantes = useListaDeParticipantes()

    const navegarPara = useNavigate()

    const sortear = useSorteador()
    
    const iniciar = () => {
        sortear()
        navegarPara('/sorteio')
    }

    return (<footer className="rodape-configuracoes">
        <button className="botao" disabled={participantes.length < 3} onClick={iniciar}>Iniciar brincadeira</button>
        <img src="/imagens/sacolas.png" alt="Sacolas de compras" />
    </footer>)
}

export default Rodape
```

É possível testá-lo com: 

```typescript
import { fireEvent, render, screen } from "@testing-library/react";
import { RecoilRoot } from "recoil";
import { useListaDeParticipantes } from "../state/hook/useListaDeParticipantes";
import Rodape from "./Rodape";
import { useNavigate } from "react-router-dom";
import { useSorteador } from "../state/hook/useSorteador";

jest.mock('../state/hook/useListaDeParticipantes');
const mockedUseListaDeParticipantes = useListaDeParticipantes as jest.Mock;

jest.mock('react-router-dom');
const mockedUseNavigate = useNavigate as jest.Mock;

jest.mock('../state/hook/useSorteador');
const mockedUseSorteador = useSorteador as jest.Mock;

describe('Comportamento Rodapé', () => {

    beforeEach(() => {
        mockedUseListaDeParticipantes.mockClear();
        mockedUseNavigate.mockClear();
    })

    test('dada uma lista de participantes, quando a lista for menor que 3, a partida não pode ser inicializada', () => {
        const listaDeParticipantes = ['Victor', 'Geovana'];
        mockedUseListaDeParticipantes.mockReturnValue(listaDeParticipantes)

        render(
            <RecoilRoot>
                <Rodape />
            </RecoilRoot>
        )

        const button = screen.getByRole('button');
        expect(button).toBeDisabled();
    })

    test('dada uma lista de participantes, quando a lista for maior ou igual a 3, o botão deve estar habilitado', () => {
        const listaDeParticipantes = ['Victor', 'Geovana', 'Abgail'];
        mockedUseListaDeParticipantes.mockReturnValue(listaDeParticipantes)

        render(
            <RecoilRoot>
                <Rodape />
            </RecoilRoot>
        )

        const button = screen.getByRole('button');
        expect(button).toBeEnabled();
    })

    test('dada uma lista de participantes, quando a lista for maior ou igual a 3 e o botão for clicado, a partida deve iniciar', () => {
        const listaDeParticipantes = ['Victor', 'Geovana', 'Abgail'];
        mockedUseListaDeParticipantes.mockReturnValue(listaDeParticipantes)

        const navegarParaMock = jest.fn();
        mockedUseNavigate.mockReturnValue(navegarParaMock);

        const sortearMock = jest.fn();
        mockedUseSorteador.mockReturnValue(sortearMock);

        render(
            <RecoilRoot>
                <Rodape />
            </RecoilRoot>
        )

        const button = screen.getByRole('button');
        expect(button).toBeEnabled();

        fireEvent.click(button);

        expect(sortearMock).toHaveBeenCalled();
        expect(navegarParaMock).toHaveBeenCalledWith('/sorteio')
    })

})
```

## Exemplo 3: Hook Contador

Dado Atom do Recoil:

```typescript
import { atom } from 'recoil';

export const counterState = atom<number>({
    key: 'counterState',
    default: 0
})
```

E um hook que incrementa e decrementa o estado deste atom:

```typescript
const useCounter = () => {
    const [count, setCount] = useRecoilState(counterState);

    const increment = () => {
        setCount(count + 1);
    }

    const decrement = () => {
        setCount(count - 1);
    }

    return {
        count,
        increment,
        decrement
    }
}

export default useCounter;
```

Podemos testá-lo com:

```typescript
import { RecoilRoot } from "recoil";
import useCounter from "./useCounter"
import { renderHook } from "@testing-library/react";
import { act } from "react";

describe('counterHook test', () => {

    test('given a counter, when I increment the state, the count must be incremented', () => {
        const { result } = renderHook(() => useCounter(), {
            wrapper: RecoilRoot
        });

        expect(result.current.count).toBe(0);
        act(() => {
            result.current.increment();
        });
        expect(result.current.count).toBe(1);
    })

    test('given a counter, when I decrement the state, the count must be decremented', () => {
        const { result } = renderHook(() => useCounter(), {
            wrapper: RecoilRoot
        });

        expect(result.current.count).toBe(0);
        act(() => {
            result.current.decrement();
        });
        expect(result.current.count).toBe(-1);
    })

})
```