# **Themes e Tokens no React:**

Themes e tokens são fundamentais para o gerenciamento de estilos em aplicativos React. 

1. **O que são Themes e Tokens?**

   - **Themes:** Um theme é um conjunto de valores que define a aparência de um aplicativo, como cores, tipografia, espaçamento e outros estilos.

   - **Tokens:** Tokens são variáveis que representam os valores do theme, como `primaryColor`, `fontSizeLarge`, `spacingUnit`.

2. **Definindo Tokens:**

   - Crie um arquivo de tokens que contém as variáveis representando os valores do seu theme. Por exemplo:

   ```typescript
   // tokens.ts
   const tokens = {
     primaryColor: '#0070f3',
     fontSizeLarge: '24px',
     spacingUnit: '8px',
   };

   export default tokens;
   ```

   É uma boa prática agrupar os tokens por tipo, como nos exemplos a seguir.

   ```typescript
    const borderRadius = {
      none: "0",
      sm: "8px",
      md: "16px",
      lg: "24px",
    };
  
    export default borderRadius;
    ```

   ```typescript
    const breakpoints = {
      desktop: "(max-width: 1200px)",
      tablet: "(max-width: 768px)",
      phone: "(max-width: 375px)",

    };
    export default breakpoints;
   ```

   ```typescript
    const colors = {
      Transparent: "transparent",
      white: "#FFF",
      black: "#000000",
    };
    
    export default colors;
   ```

   ```typescript
    const fonts = {
      fontPrimary: "Poppins, sans-serif",
      fontSecondary: "Inter, sans-serif",
    };
   ```

   ```typescript
    const fontSize = {
      xs: "0.75rem",
      sm: "0.875rem",
      base: "1.6rem",
      lg: "1.125rem",
      xl: "1.5rem",
      "2xl": "2rem",
      "3xl": "2.5rem",
      "4xl": "3rem",
    };
    
    export default fontSize;
   ```

   ```typescript
    const fontWeight = {
      normal: 400,
      bold: 700,
    };
  
    export default fontWeight;
   ```

   ```typescript
    const letterSpacing = {
      trackingTight: "0rem",
      trackingNormal: "0.02rem"
    }

    export default letterSpacing;
   ```

   ```typescript
    const lineHeight = {
      base: "1em",
      tight: "1.2em",
      normal: "1.5em",
      relaxed: "1.7em",
    };
    
    export default lineHeight;
   ```

    ```typescript
    const spacing = {
      xxs: "4px",
      xs: "8px",
      m: "16px",
      xm: "24px",
      xxm: "32px",
      l: "48px",
      xl: "64px",
    };
    
    export default spacing;
    ```

3. **Definindo Index:**

    Em seguida é uma boa prática reunir todos estes tokens em um arquivo index, para que eles possam ser importados de um mesmo arquivo.

    ```typescript
    import FONTSIZE from "./fontSize"
    import COLORS from "./colors"
    import BREAKPOINTS from "./breakpoints";
    import BORDERRADIUS from "./borderRadius";
    import FONTWEIGHT from "./fontWeight"
    import LETTERSPACING from "./letterSpacing"
    import LINEHEIGHT from "./lineHeight";
    import FONTFAMILY from "./fontFamily"
    import HEADLINE from "./headline"
    import SPACING from "./spacing"
    import TEXT from "./text"


    export {FONTSIZE, COLORS, BREAKPOINTS, BORDERRADIUS, FONTWEIGHT, LETTERSPACING, FONTFAMILY, LINEHEIGHT, HEADLINE, TEXT, SPACING}
    ```

4. **Criando Tokens que utilizam outros Tokens:**

    Também é possível criar tokens que utilizam outros tokens:

    ```typescript
    import {
        FONTFAMILY,
        FONTSIZE,
        FONTWEIGHT,
        LETTERSPACING,
        LINEHEIGHT
    } from "./index";
    
    const headline = {
        "4xl": {
          fontFamily: FONTFAMILY.fontPrimary,
          fontWeight: FONTWEIGHT.bold,
          fontSize: FONTSIZE["4xl"],
          letterSpacing: LETTERSPACING.trackingTight,
          lineHeight: LINEHEIGHT.normal,
        },
        "3xl": {
          fontFamily: FONTFAMILY.fontPrimary,
          fontWeight: FONTWEIGHT.bold,
          fontSize: FONTSIZE["3xl"],
          letterSpacing: LETTERSPACING.trackingTight,
          lineHeight: LINEHEIGHT.normal,
        },
        "2xl": {
          fontFamily: FONTFAMILY.fontPrimary,
          fontWeight: FONTWEIGHT.bold,
          fontSize: FONTSIZE["2xl"],
          letterSpacing: LETTERSPACING.trackingTight,
          lineHeight: LINEHEIGHT.normal,
        },
    };
    
    export default headline;
    ```

    ```typescript
    import {
      FONTFAMILY,
      FONTSIZE,
      FONTWEIGHT,
      LETTERSPACING,
      LINEHEIGHT
   
    } from "./index";
    
    const headline = {
        xl: {
          fontFamily: FONTFAMILY.fontPrimary,
          fontWeight: FONTWEIGHT.normal,
          fontSize: FONTSIZE.xl,
          letterSpacing: LETTERSPACING.trackingTight,
          lineHeight: LINEHEIGHT.normal,
        },
        lg: {
          fontFamily: FONTFAMILY.fontPrimary,
          fontWeight: FONTWEIGHT.normal,
          fontSize: FONTSIZE.lg,
          letterSpacing: LETTERSPACING.trackingTight,
          lineHeight: LINEHEIGHT.normal,
        },
        base: {
          fontFamily: FONTFAMILY.fontPrimary,
          fontWeight: FONTWEIGHT.normal,
          fontSize: FONTSIZE.base,
          letterSpacing: LETTERSPACING.trackingTight,
          lineHeight: LINEHEIGHT.normal,
        },
        sm: {
          fontFamily: FONTFAMILY.fontPrimary,
          fontWeight: FONTWEIGHT.normal,
          fontSize: FONTSIZE.sm,
          letterSpacing: LETTERSPACING.trackingTight,
          lineHeight: LINEHEIGHT.normal,
        },
        xs: {
          fontFamily: FONTFAMILY.fontPrimary,
          fontWeight: FONTWEIGHT.normal,
          fontSize: FONTSIZE.xs,
          letterSpacing: LETTERSPACING.trackingTight,
          lineHeight: LINEHEIGHT.normal,
        },
    };
    
    export default headline;
    ```

5. **Criando o Theme:**

   - Crie um objeto de theme que utiliza os tokens. O theme pode ser um objeto que contém todas as variáveis de estilo ou um conjunto de objetos temáticos para diferentes partes do aplicativo.

   ```typescript
    import {COLORS, FONTSIZE, BREAKPOINTS, BORDERRADIUS, FONTWEIGHT, LETTERSPACING, FONTFAMILY, LINEHEIGHT, HEADLINE, TEXT, SPACING} from "../tokens"

    export const defaultTheme = {
        FONTSIZE,
        COLORS,
        BREAKPOINTS,
        BORDERRADIUS,
        FONTWEIGHT,
        LETTERSPACING,
        FONTFAMILY,
        LINEHEIGHT,
        HEADLINE,
        TEXT,
        SPACING
    } as const;
   ```

6. **Configurando o Theme Provider:**

   - Use o `ThemeProvider` do Styled-Components para disponibilizar o tema para componentes do aplicativo.

   ```tsx
   // App.tsx
   import React from 'react';
   import { ThemeProvider } from 'styled-components';
   import theme from './theme';

   function App() {
     return (
       <ThemeProvider theme={defaultTheme}>
         {/* Seus componentes aqui */}
       </ThemeProvider>
     );
   }

   export default App;
   ```

7. **Acessando o Theme em Componentes:**

   - Para acessar as variáveis do tema, utilize o Styled-Components com o método `props.theme`.

   ```tsx
   // Component.tsx
   import styled from 'styled-components';

   const StyledComponent = styled.div`
     color: ${(props) => props.theme.colors.primary};
     font-size: ${(props) => props.theme.typography.fontSize};
   `;

   function MyComponent() {
     return (
       <StyledComponent>
         Conteúdo com base no theme
       </StyledComponent>
     );
   }
   ```

8. **Substituição de Themes:**

   - É possível substituir ou alternar entre temas em tempo de execução. Você pode ter diferentes arquivos de tokens e temas para temas claros e escuros, por exemplo.

   ```typescript
   // darkTheme.ts
   const darkTokens = {
     primaryColor: '#ff9900',
     fontSizeLarge: '24px',
     spacingUnit: '8px',
   };

   const darkTheme = {
     colors: {
       primary: darkTokens.primaryColor,
     },
     typography: {
       fontSize: darkTokens.fontSizeLarge,
     },
     spacing: {
       unit: darkTokens.spacingUnit,
     },
   };

   export default darkTheme;
   ```

   ```tsx
   // ToggleThemeButton.tsx
   import React from 'react';
   import { ThemeProvider } from 'styled-components';
   import theme from './theme';
   import darkTheme from './darkTheme';

   function ToggleThemeButton() {
     const [currentTheme, setCurrentTheme] = React.useState(theme);

     const toggleTheme = () => {
       if (currentTheme === theme) {
         setCurrentTheme(darkTheme);
       } else {
         setCurrentTheme(theme);
       }
     };

     return (
       <ThemeProvider theme={currentTheme}>
         <button onClick={toggleTheme}>Toggle Theme</button>
       </ThemeProvider>
     );
   }

   export default ToggleThemeButton;
   ```

9. **Personalização do Theme:**

   - Você pode estender e personalizar seu tema definindo novas variáveis e estilos específicos.

   ```typescript
   // customTheme.ts
   import theme from './theme';

   const customTokens = {
     ...theme.tokens,
     customColor: '#ff5500',
   };

   const customTheme = {
     ...theme,
     colors: {
       ...theme.colors,
       custom: customTokens.customColor,
     },
   };

   export default customTheme;
   ```