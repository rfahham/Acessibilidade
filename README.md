# 📘 Especificação de Requisitos – Acessibilidade

### 🧩 Visão Geral

Este documento descreve os requisitos mínimos de acessibilidade que devem ser considerados no desenvolvimento da aplicação, visando garantir inclusão digital, usabilidade e conformidade com padrões como WCAG 2.1.

---

### ✅ Requisitos Funcionais de Acessibilidade

#### 1. **Navegação**

* A estrutura da interface deve permitir navegação sequencial:

  * **Horizontal:** Da esquerda para a direita
  * **Vertical:** De cima para baixo
* Compatibilidade com navegação via teclado (Tab, Shift+Tab, Enter).

#### 2. **Tipografia**

* **Fonte padrão:** Sans Serif (ex: Arial, Helvetica, Roboto)
* **Tamanho base:** 16px
* **Escalonamento de texto:** Deve oferecer ao usuário pelo menos 3 níveis de ajuste de tamanho (ex: pequeno, médio, grande).

#### 3. **Imagens e Gráficos**

* Todas as imagens, ícones e gráficos devem conter **texto alternativo (alt)** que descreva seu conteúdo ou função.
* Gráficos complexos devem possuir descrição detalhada ou equivalente textual.

#### 4. **Botões e Elementos Interativos**

* Todos os elementos clicáveis devem ter:

  * **`alt`**, **`aria-label`** ou **`aria-labelledby`** devidamente preenchidos
  * Indicação visual clara de foco (outline)

#### 5. **Contraste de Cores**

* O design deve manter uma **taxa de contraste mínima de 4.5:1** entre o texto e o fundo (padrão WCAG AA).
* Verificar contraste em estados diferentes (ativo, hover, foco).

#### 6. **Modo Escuro (Dark Mode)**

* A aplicação deve oferecer suporte ao modo escuro, com:

  * Contraste apropriado no novo esquema de cores
  * Mesma funcionalidade do modo claro

#### 7. **Integração com VLibras**

* A aplicação deve permitir a integração com a ferramenta **VLibras**, garantindo tradução do conteúdo textual para Libras (Língua Brasileira de Sinais).
* A extensão VLibras deve ser ativável pelo usuário.

#### 8. **Ambiente de Desenvolvimento (VS Code)**

* Recomendado o uso de **extensões de acessibilidade no Visual Studio Code**, como:

  * ESLint com regras para acessibilidade
  * Plugins de verificação de contraste
  * Emuladores de leitores de tela

---

### 📝 Observações Finais

* Todos os critérios acima devem ser considerados no momento do design e desenvolvimento.
* Testes com ferramentas como Lighthouse, axe ou NVDA são fortemente recomendados.


Abaixo estão **exemplos práticos de código** para cada item dos requisitos de acessibilidade que mencionamos. Os exemplos são escritos em HTML/CSS/JS onde aplicável, com comentários para facilitar a compreensão da equipe técnica.

---

## 💻 Exemplos de Código – Acessibilidade

---

### 1. **Navegação (estrutura semântica e ordem lógica)**

```html
<!-- Navegação semântica -->
<nav>
  <ul>
    <li><a href="#inicio">Início</a></li>
    <li><a href="#servicos">Serviços</a></li>
    <li><a href="#contato">Contato</a></li>
  </ul>
</nav>

<!-- Ordem lógica: esquerda → direita, cima → baixo -->
<main>
  <section id="inicio">...</section>
  <section id="servicos">...</section>
  <section id="contato">...</section>
</main>
```

---

### 2. **Tipografia (tamanho ajustável, sans-serif)**

```html
<!-- Fonte padrão e ajuste em CSS -->
<style>
  body {
    font-family: Arial, sans-serif;
    font-size: 16px;
  }

  .font-pequena { font-size: 14px; }
  .font-media   { font-size: 16px; }
  .font-grande  { font-size: 20px; }
</style>

<!-- Controles de ajuste -->
<button onclick="ajustarFonte('pequena')">A-</button>
<button onclick="ajustarFonte('media')">A</button>
<button onclick="ajustarFonte('grande')">A+</button>

<script>
function ajustarFonte(tamanho) {
  document.body.className = 'font-' + tamanho;
}
</script>
```

---

### 3. **Imagens e Gráficos (texto alternativo)**

```html
<!-- Imagem com texto alternativo -->
<img src="logo.png" alt="Logotipo da empresa XPTO">

<!-- Gráfico com descrição -->
<figure>
  <img src="grafico-vendas.png" alt="Gráfico de barras mostrando o crescimento de vendas em 2025">
  <figcaption>Vendas por trimestre - 2025</figcaption>
</figure>
```

---

### 4. **Botões e Elementos Interativos (aria e foco)**

```html
<!-- Botão com descrição para leitores de tela -->
<button aria-label="Abrir menu de navegação">☰</button>

<!-- Link com aria-labelledby -->
<a href="#contato" id="linkContato" aria-labelledby="descContato">Fale conosco</a>
<span id="descContato" hidden>Ir para a seção de contato no fim da página</span>

<!-- Indicação de foco em CSS -->
<style>
  button:focus, a:focus {
    outline: 3px solid #00f;
  }
</style>
```

---

### 5. **Contraste (bom contraste entre texto e fundo)**

```html
<!-- Exemplo com bom contraste -->
<style>
  body {
    background-color: #ffffff;
    color: #000000; /* Contraste 21:1 */
  }

  .botao {
    background-color: #000000;
    color: #ffffff; /* Texto branco sobre fundo preto = alto contraste */
    padding: 10px;
  }
</style>

<button class="botao">Enviar</button>
```

---

### 6. **Modo Escuro (Dark Mode)**

```html
<!-- Tema com alternância clara/escura -->
<style>
  body {
    background-color: #fff;
    color: #000;
    transition: all 0.3s;
  }

  body.dark-mode {
    background-color: #121212;
    color: #e0e0e0;
  }
</style>

<button onclick="document.body.classList.toggle('dark-mode')">
  Alternar Dark Mode
</button>
```

---

### 7. **VLibras (integração com acessibilidade em Libras)**

```html
<!-- Script oficial do VLibras -->
<div vw class="enabled">
  <div vw-access-button class="active"></div>
  <div vw-plugin-wrapper>
    <div class="vw-plugin-top-wrapper"></div>
  </div>
</div>

<script src="https://vlibras.gov.br/app/vlibras-plugin.js"></script>
<script>
  new window.VLibras.Widget('https://vlibras.gov.br/app');
</script>
```

---

### 8. **Extensões e boas práticas no VS Code**

> Não é um código, mas aqui estão extensões recomendadas com links:

* **[axe Accessibility Linter](https://marketplace.visualstudio.com/items?itemName=deque-systems.vscode-axe-linter)** – Avaliação automática de acessibilidade
* **[Color Contrast Checker](https://marketplace.visualstudio.com/items?itemName=akamud.vscode-theme-onedark)** – Verificador de contraste
* **[HTMLHint](https://marketplace.visualstudio.com/items?itemName=mkaufman.HTMLHint)** – Valida práticas acessíveis em HTML
* **[eslint-plugin-jsx-a11y](https://github.com/jsx-eslint/eslint-plugin-jsx-a11y)** – Para projetos React


