# Internacionalização

## Internacionalização (i18n):

A Internacionalização (i18n) é um processo vital no desenvolvimento de software, que visa adaptar uma aplicação para diferentes idiomas e regiões, permitindo que usuários de diferentes países possam a utilizar.

## Configuração Inicial:

Instale as bibliotecas necessárias via npm:

```bash
npm install react-i18next i18next --save
```

Crie a pasta `/lib` dentro de `./src` e adicione o arquivo `i18n.ts`:

```typescript
// i18n.ts
import i18next from "i18next";
import { initReactI18next } from "react-i18next";

i18next.use(initReactI18next).init({ 
  resources: {
    en: {},
    pt: {},
    ru: {}
  },
  lng: 'en'
});
```
`lng`: Representa o idioma inicial que será carregado.

## Arquivos de Tradução:

Crie o diretório `/locale` e os arquivos de tradução `pt.json` e `en.json`:

**pt.json:**
```json
{
  "translation": {
    "title": "Internacionalização Fácil",
    "description": "O conteúdo da minha página internacional.",
    "select-label": "Selecione o idioma"
  }
}
```

**en.json:**
```json
{
  "translation": {
    "title": "Easy Internationalization",
    "description": "The content of my international page.",
    "select-label": "Choose the language."
  }
}
```

**ru.json:**
```json
{
  "translation": {
    "title": "Легкая интернационализация",
    "description": "Содержание моей международной страницы.",
    "select-label": "Выберите язык."
  }
}
```

## Atualização do Arquivo `i18n.ts`:

Modifique o arquivo `i18n.ts` para incorporar as traduções:

```typescript
// i18n.ts
import i18next from "i18next";
import { initReactI18next } from "react-i18next";
import enTranslations from "../locale/en.json";
import ptTranslations from "../locale/pt.json";
import ruTranslations from "../locale/ru.json";

i18next.use(initReactI18next).init({ 
  resources: {
    en: { ...enTranslations },
    pt: { ...ptTranslations },
    ru: { ..ruTranslations }
  },
  lng: 'en'
});
```

## Utilizando a Biblioteca no React:

1. Importe o arquivo `i18n.ts` no `main.tsx`:

```typescript
// main.tsx
import './lib/i18n';
```

2. Exemplo de uso no componente App.tsx do React:

```typescript
import React, { useState } from 'react';
import { useTranslation } from 'react-i18next';
import './App.css';

function App() {
  const { t, i18n: { changeLanguage, language } } = useTranslation();
  const [currentLanguage, setCurrentLanguage] = useState(language);

  const handleChangeLanguage = (event) => {
    const newLanguage = event.target.value;
    changeLanguage(newLanguage);
    setCurrentLanguage(newLanguage);
  };

  return (
    <>
      <div className="header">
        <h1>{t('translation.title')}</h1>
      </div>
      <div className="main">
        <p>{t('translation.description')}</p>
        <label htmlFor="languageSelect">{t('translation.select-label')}</label>
        <select
          id="languageSelect"
          value={currentLanguage}
          onChange={handleChangeLanguage}
        >
          <option value="en">English</option>
          <option value="pt">Português</option>
          <option value="ru">Русский</option>
        </select>
      </div>
    </>
  );
}

export default App;

```

## Outros Conceitos Relevantes:

1. **Formatação de Data e Números:**
   - Utilize bibliotecas como `date-fns` ou `intl` para formatação de datas e números de acordo com a localização.

Lembre-se de consultar a documentação oficial das bibliotecas utilizadas para obter informações detalhadas sobre recursos adicionais e melhores práticas.
