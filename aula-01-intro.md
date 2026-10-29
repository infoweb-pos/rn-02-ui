# Aula 01 - Introdução ao React Native e UI com NativeWind

## Informações gerais

- Duração: 60 min de exposição + 30 min de desafio
- Stack do projeto: Expo + TypeScript + NativeWind
- Competências:
  - Entender a árvore de componentes.
  - Aplicar estilos utilizando classes utilitárias.
- Conceitos abordados:
  - View
  - Text
  - Image
  - Pressable
  - Diferenças entre CSS e NativeWind
  - Classes Tailwind no React Native

---

## 1. Objetivo da aula

Nesta aula, vamos introduzir os conceitos básicos da interface do usuário no React Native e mostrar como criar uma tela de perfil usando componentes nativos e classes utilitárias do NativeWind. O foco é entender como a interface é montada a partir de uma árvore de componentes e como o estilo pode ser aplicado de forma rápida e consistente.

Ao final da aula, o aluno deve ser capaz de:

- reconhecer os principais componentes da interface em React Native;
- compreender a hierarquia de componentes em uma tela;
- utilizar classes utilitárias para criar layouts e estilos;
- criar uma tela simples de perfil com Expo + TypeScript + NativeWind.

---

## 2. Cronograma sugerido

### Parte 1 — Exposição (60 min)

1. Introdução ao React Native e ao Expo (10 min)
2. Árvore de componentes e renderização (15 min)
3. View, Text, Image e Pressable (15 min)
4. CSS vs NativeWind no React Native (10 min)
5. Classes Tailwind no React Native (10 min)

### Parte 2 — Desafio (30 min)

- Criar uma tela de perfil com:
  - avatar;
  - nome;
  - bio;
  - informações de contato;
  - botão de ação;
  - cards de estatísticas ou detalhes.

---

## 3. O que é React Native?

React Native é uma biblioteca para construir interfaces móveis com JavaScript/TypeScript, usando componentes que representam elementos visuais nativos do sistema operacional.

Em vez de escrever HTML e CSS para a web, escrevemos componentes como `View`, `Text`, `Image` e `Pressable`, que são convertidos em elementos nativos da plataforma.

### Exemplo rápido

```tsx
import { View, Text } from 'react-native';

export default function App() {
  return (
    <View className="flex-1 items-center justify-center bg-slate-100">
      <Text className="text-xl font-bold text-slate-900">Olá, React Native!</Text>
    </View>
  );
}
```

Neste exemplo:

- `View` representa um container;
- `Text` renderiza texto;
- `className` aplica estilos utilitários vindos do NativeWind.

---

## 4. Árvore de componentes

Uma interface em React Native é montada como uma árvore de componentes. A árvore começa com um componente principal e vai aninhando outros componentes dentro dele.

### Exemplo de árvore

```tsx
<View>
  <View>
    <Image />
    <Text>Nome do usuário</Text>
  </View>

  <Pressable>
    <Text>Editar perfil</Text>
  </Pressable>
</View>
```

Essa estrutura pode ser vista como:

```text
App
└── View (container principal)
    ├── View (cabecalho)
    │   ├── Image (avatar)
    │   └── Text (nome)
    └── Pressable (botão)
        └── Text (label do botão)
```

### Por que isso importa?

Porque o layout e a lógica funcional se organizam melhor quando entendemos a hierarquia. Cada componente tem uma responsabilidade:

- `View`: organiza e containeriza outros elementos;
- `Text`: exibe textos;
- `Image`: carrega imagens;
- `Pressable`: permite interação (clique, toque, ação).

---

## 5. Componentes básicos

### 5.1 `View`

`View` é o bloco de construção principal da interface. Ele pode agir como `div` em React web, mas em React Native ele é o container mais usado.

```tsx
import { View } from 'react-native';

export default function Card() {
  return <View className="rounded-xl bg-white p-4 shadow-sm" />;
}
```

### 5.2 `Text`

`Text` é usado para exibir texto. Ele deve conter toda a escrita da tela.

```tsx
import { Text } from 'react-native';

export default function Nome() {
  return <Text className="text-lg font-bold text-slate-900">Leonardo Minora</Text>;
}
```

### 5.3 `Image`

`Image` exibe imagens locais ou remotas. Ele pode receber uma URL ou uma imagem local.

```tsx
import { Image } from 'react-native';

export default function Avatar() {
  return (
    <Image
      source={{ uri: 'https://images.unsplash.com/...' }}
      className="h-24 w-24 rounded-full"
    />
  );
}
```

### 5.4 `Pressable`

`Pressable` é o componente de interação. Ele envolve áreas clicáveis e pode disparar eventos como `onPress`.

```tsx
import { Pressable, Text } from 'react-native';

export default function Botao() {
  return (
    <Pressable
      onPress={() => console.log('Botão pressionado')}
      className="rounded-xl bg-indigo-600 px-4 py-3"
    >
      <Text className="text-center font-semibold text-white">Salvar</Text>
    </Pressable>
  );
}
```

---

## 6. Diferenças entre CSS e NativeWind

### CSS (web)

No desenvolvimento web, normalmente escrevemos CSS em arquivos separados ou em blocos embutidos, por exemplo:

```css
.card {
  background: #fff;
  border-radius: 12px;
  padding: 16px;
}
```

Vantagens:

- enorme compatibilidade com a web;
- suporte a pseudo-classes como `:hover`, `:focus`;
- linguagem rica e tradicional da estilização web.

Desvantagens:

- não é diretamente aplicável ao React Native;
- depende de um browser e de regras do CSS da web;
- muitos conceitos do CSS não existem da mesma forma no ambiente mobile.

### NativeWind

NativeWind permite usar classes utilitárias, como as do Tailwind, em componentes React Native.

Exemplo:

```tsx
<View className="bg-white p-4 rounded-xl shadow-sm" />
```

Em vez de escrever:

```tsx
<View style={{ backgroundColor: '#fff', borderRadius: 12, padding: 16 }} />
```

o NativeWind transforma essas classes em estilos nativos. Isso deixa o código mais rápido, legível e consistente com a ideia do Tailwind.

### Principais diferenças

| Conceito | CSS Web | NativeWind / React Native |
|---|---|---|
| Seletores | `:hover`, `:focus`, etc. | Menos seletividade; foco em componentes e estados |
| Unidade | px, rem, %, vw, vh | px e proporções para dimensões; layout responsivo |
| Layout | Fluxo da web | Flexbox com comportamento mobile |
| Sintaxe | `class` ou arquivo CSS | `className` em componentes React Native |
| Cascata | CSS cascata e herança | Sem cascata como na web; composição por componentes |

---

## 7. Classes Tailwind no React Native

Tailwind é uma abordagem de estilos baseada em classes utilitárias. Em vez de escrever CSS manualmente, você combina classes como:

- `flex`
- `items-center`
- `justify-between`
- `bg-slate-100`
- `text-lg`
- `font-bold`
- `rounded-xl`
- `p-4`

### Exemplos comuns

```tsx
<View className="flex-1 bg-slate-100 p-6">
  <Text className="text-2xl font-bold text-slate-900">Perfil</Text>
</View>
```

### O que essas classes fazem?

- `flex-1`: ocupa o espaço disponível;
- `bg-slate-100`: define a cor de fundo;
- `p-6`: padding;
- `text-2xl`: tamanho do texto;
- `font-bold`: negrito;
- `text-slate-900`: cor do texto;
- `rounded-xl`: bordas arredondadas.

### Observações importantes

- Classes Tailwind no React Native funcionam através do NativeWind.
- Nem todas as classes do CSS web existem exatamente do mesmo jeito no React Native.
- O uso de `className` é uma conveniência para escrever estilos em formato utilitário.

---

## 8. Setup do projeto com Expo + TypeScript + NativeWind

### Passo 1 — criar o projeto

```bash
npx create-expo-app perfil-app --template blank-typescript
cd perfil-app
```

### Passo 2 — instalar o NativeWind

```bash
npm install nativewind
npm install -D tailwindcss
```

### Passo 3 — configurar o NativeWind

No arquivo `babel.config.js`:

```js
module.exports = function (api) {
  api.cache(true);
  return {
    presets: ['babel-preset-expo'],
    plugins: ['nativewind/babel'],
  };
};
```

No arquivo `tailwind.config.js`:

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ['./App.tsx', './app/**/*.{js,ts,jsx,tsx}'],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

> Em projetos Expo mais recentes, a configuração pode variar ligeiramente, mas a ideia central é a mesma: incluir o NativeWind no processo de compilação e permitir o uso de `className`.

---

## 9. Hands-on do professor: criar uma tela de perfil

Vamos construir uma tela de perfil com:

- fundo claro;
- cabeçalho com avatar;
- nome e profissão;
- mini cards com informações;
- botão de ação;
- lista de informações pessoais.

### Estrutura da tela

```text
App
└── View (container principal)
    ├── View (capa / card principal)
    │   ├── Image (avatar)
    │   ├── Text (nome)
    │   ├── Text (profissão)
    │   ├── View (status)
    │   └── Pressable (botão)
    └── View (lista de detalhes)
```

### Código completo do exemplo

```tsx
import React from 'react';
import { Image, Pressable, ScrollView, Text, View } from 'react-native';

export default function App() {
  return (
    <View className="flex-1 bg-slate-100">
      <ScrollView contentContainerStyle={{ paddingBottom: 32 }}>
        <View className="bg-indigo-600 px-6 pb-20 pt-12">
          <Text className="text-2xl font-bold text-white">Perfil</Text>
        </View>

        <View className="-mt-14 px-4">
          <View className="rounded-3xl bg-white p-5 shadow-sm">
            <View className="items-center">
              <Image
                source={{
                  uri: 'https://images.unsplash.com/photo-1500648767791-00dcc994a43e?auto=format&fit=crop&w=400&q=80',
                }}
                className="h-28 w-28 rounded-full border-4 border-indigo-100"
              />
            </View>

            <View className="mt-4 items-center">
              <Text className="text-2xl font-bold text-slate-900">Ana Souza</Text>
              <Text className="mt-1 text-base text-slate-500">Designer UX/UI</Text>
            </View>

            <View className="mt-5 flex-row justify-between">
              <View className="flex-1 items-center rounded-2xl bg-indigo-50 p-3">
                <Text className="text-xl font-bold text-indigo-600">128</Text>
                <Text className="text-xs text-slate-500">Projetos</Text>
              </View>

              <View className="mx-2 flex-1 items-center rounded-2xl bg-emerald-50 p-3">
                <Text className="text-xl font-bold text-emerald-600">98%</Text>
                <Text className="text-xs text-slate-500">Concluídos</Text>
              </View>

              <View className="flex-1 items-center rounded-2xl bg-amber-50 p-3">
                <Text className="text-xl font-bold text-amber-600">4.9</Text>
                <Text className="text-xs text-slate-500">Avaliação</Text>
              </View>
            </View>

            <Pressable className="mt-6 rounded-2xl bg-indigo-600 px-4 py-3">
              <Text className="text-center text-base font-semibold text-white">
                Editar perfil
              </Text>
            </Pressable>
          </View>
        </View>

        <View className="mt-6 px-4">
          <Text className="mb-3 text-lg font-bold text-slate-900">Sobre</Text>
          <View className="rounded-2xl bg-white p-4 shadow-sm">
            <Text className="text-sm leading-6 text-slate-600">
              Sou designer focada em interfaces acessíveis, sistemas de design e
              experiências que unem estética e funcionalidade.
            </Text>
          </View>
        </View>

        <View className="mt-6 px-4">
          <Text className="mb-3 text-lg font-bold text-slate-900">Detalhes</Text>

          <View className="space-y-3 rounded-2xl bg-white p-4 shadow-sm">
            <View className="flex-row items-center justify-between border-b border-slate-200 pb-3">
              <Text className="text-slate-500">E-mail</Text>
              <Text className="font-medium text-slate-900">ana@email.com</Text>
            </View>

            <View className="flex-row items-center justify-between border-b border-slate-200 pb-3">
              <Text className="text-slate-500">Cidade</Text>
              <Text className="font-medium text-slate-900">Recife</Text>
            </View>

            <View className="flex-row items-center justify-between">
              <Text className="text-slate-500">Disponibilidade</Text>
              <Text className="font-medium text-emerald-600">Disponível</Text>
            </View>
          </View>
        </View>
      </ScrollView>
    </View>
  );
}
```

### Discussão da implementação

- `View` organiza o layout geral.
- `Image` exibe o avatar do perfil.
- `Text` mostra nome, profissão e textos de apoio.
- `Pressable` cria o botão de ação.
- `className` concentra a estilização sem escrever estilos inline complexos.

---

## 10. Como explicar a arquitetura da tela para os alunos

Ao apresentar a tela, o professor pode dizer:

1. `App` é o componente raiz.
2. Um `ScrollView` permite que o conteúdo exceda a altura da tela.
3. O primeiro bloco de `View` cria a área superior azul, que funciona como um cabeçalho.
4. O cartão central é um container que recebe o avatar, nome e estatísticas.
5. O botão `Pressable` adiciona interação.
6. As classes do Tailwind como `bg-indigo-600`, `rounded-2xl` e `text-slate-900` tornam o layout mais visual e organizado.

---

## 11. A importância de `className` em NativeWind

Em React Native puro, normalmente usamos `style` com objetos JavaScript. Isso funciona, mas pode ficar repetitivo e pouco legível.

Exemplo puro:

```tsx
<View style={{ flex: 1, backgroundColor: '#f8fafc', padding: 24 }} />
```

Com NativeWind:

```tsx
<View className="flex-1 bg-slate-100 p-6" />
```

Isso torna o código mais próximo do padrão web e mais rápido de escrever e manter.

---

## 12. Dicas de didática para a aula

### Sugestão de abordagem para o professor

- Comece mostrando uma simples tela com `View` e `Text`.
- Em seguida, introduza `Image` e explique como carregar uma imagem externa.
- Depois, mostre `Pressable` e explique a ideia de ação e interação.
- Finalize com a comparação entre CSS tradicional e NativeWind.
- A partir disso, apresente o exemplo final da tela de perfil.

### Perguntas orientadoras

- O que acontece se removermos um componente pai?
- Como a árvore de componentes influencia o layout?
- Por que `View` é tão importante em React Native?
- Qual a diferença entre escrever estilos com `style` e com `className`?

---

## 13. Desafio para os alunos (30 min)

Crie uma segunda tela simples de perfil com os seguintes requisitos:

- avatar grande;
- nome e profissão;
- descrição curta;
- 3 cards com informações;
- botão "Seguir" ou "Enviar mensagem";
- pelo menos um item com `Pressable`;
- uso de classes utilitárias do NativeWind.

### Critérios de avaliação

- estrutura clara de componentes;
- uso correto de `View`, `Text`, `Image` e `Pressable`;
- uso de classes utilitárias para estilos;
- organização visual e legibilidade;
- botão com interação.

---

## 14. Encerramento

Nesta aula, os alunos conhecem os blocos básicos para construir interfaces em React Native e aprendem a pensar em termos de árvore de componentes. Além disso, entendem como o NativeWind facilita o trabalho com estilos utilizando classes utilitárias, mantendo o código mais legível e produtivo.

O próximo passo será avançar para layouts mais complexos, navegação e componentes reutilizáveis.

---

## 15. Resumo rápido

- `View`: container
- `Text`: texto
- `Image`: imagem
- `Pressable`: interação
- CSS e NativeWind têm objetivos semelhantes, mas diferentes ambientes
- Tailwind no React Native é escrito com `className`
- NativeWind melhora produtividade e legibilidade

---

## 16. Referências rápidas

- Expo: https://expo.dev/
- React Native: https://reactnative.dev/
- NativeWind: https://www.nativewind.dev/
- Tailwind CSS: https://tailwindcss.com/

---

## 17. Mini checklist do professor

Antes de iniciar a aula, confirme se os alunos conseguem responder:

- [ ] O que é uma árvore de componentes?
- [ ] Quando usamos `View`?
- [ ] Quando usamos `Text`?
- [ ] Quando usamos `Image`?
- [ ] O que é `Pressable`?
- [ ] Qual a diferença entre CSS e NativeWind?
- [ ] Como aplicar classes Tailwind no React Native?

Se todas as respostas forem compreendidas, a aula está pronta para avançar para o desafio prático.
