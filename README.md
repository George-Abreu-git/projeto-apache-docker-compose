# 🐳 Desafio: Página HTML Estática em Container Apache

Projeto desenvolvido como desafio prático de containerização, com o objetivo de servir uma página HTML estática personalizada utilizando **Apache HTTP Server** dentro de um container **Docker**, orquestrado via **Docker Compose**.

---

## 📋 Descrição do Projeto

A aplicação consiste em uma página de perfil pessoal desenvolvida com **HTML5 e CSS3 puros**, sem dependências externas de JavaScript. A página conta com:

- Banner personalizável no topo
- Card de perfil com foto e nome
- Seção de descrição do projeto
- Grid de tecnologias utilizadas
- Layout responsivo para dispositivos móveis

O servidor Apache serve os arquivos estáticos diretamente a partir do diretório `/usr/local/apache2/htdocs/`, seguindo a configuração padrão da imagem oficial `httpd:2.4`.

---

## ✅ Pré-requisitos

Antes de começar, certifique-se de ter instalado em sua máquina:

- [Docker](https://docs.docker.com/get-docker/) `>= 20.x`
- [Docker Compose](https://docs.docker.com/compose/install/) `>= 2.x`

Para verificar as versões instaladas:

````````bash
docker --version
docker compose version
` `` (remova os espaços)

---

## 🚀 Como Executar

**1. Clone o repositório:**

```````bash
git clone https://github.com/seu-usuario/seu-repositorio.git
cd seu-repositorio
` ``

**2. Suba o container:**

``````bash
docker compose up -d
` ``

**3. Acesse no navegador:**

``````
http://localhost
` ``

**4. Para parar o container:**

``````bash
docker compose down
` ``

---

## 📁 Estrutura de Arquivos

``````
.
├── docker-compose.yml       # Orquestração do container Apache
└── html/
    ├── index.html           # Página principal
    ├── banner.jpg           # Imagem do banner (substituível)
    └── foto.jpg             # Foto de perfil (substituível)
` ``

---

## ⚙️ Configuração do Docker Compose

``````yaml
services:
  web:
    image: httpd:2.4
    ports:
      - "80:80"
    volumes:
      - ./html:/usr/local/apache2/htdocs/
` ``

O mapeamento de volume `./html:/usr/local/apache2/htdocs/` garante que qualquer alteração nos arquivos locais seja refletida **instantaneamente** no servidor, sem necessidade de reiniciar o container.

---

## 🎨 Como Personalizar a Página

### Trocar o Banner

Coloque sua imagem na pasta `html/` e edite o CSS em `index.html`:

`````css
.banner {
  background-image: url('banner.jpg');
  background-size: cover;
  background-position: center;
}
` ``

### Trocar a Foto de Perfil

Substitua o placeholder no HTML pelo caminho da sua imagem:

````html
<!-- Antes -->
<div class="avatar-placeholder">Sua foto aqui</div>

<!-- Depois -->
<img class="avatar" src="foto.jpg" alt="Seu Nome" />
` ``

### Editar o Texto do Projeto

Localize a seção `.project-box` no `index.html` e edite os parágrafos `<p>` com o conteúdo desejado.

### Personalizar Cores

As cores estão centralizadas em variáveis CSS no início do `<style>`:

```css
:root {
  --bg:           #0b0f14;   /* cor de fundo */
  --accent:       #e8c87a;   /* cor de destaque (dourado) */
  --text-primary: #f0ebe0;   /* texto principal */
  --text-muted:   #8b94a3;   /* texto secundário */
}
` ``

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Função |
|---|---|
| HTML5 | Estrutura da página |
| CSS3 | Estilização e responsividade |
| Docker | Containerização da aplicação |
| Apache HTTP Server | Servidor web (`httpd:2.4`) |
| Docker Compose | Orquestração do container |

---

## 👤 Autor

**George Abreu de Siqueira**

---

*Desafio concluído com sucesso — aplicação HTML estática servida via container Apache com Docker Compose.*
```

> ⚠️ Os ` `` ` com espaços são só para não quebrar a formatação aqui no chat — no seu arquivo use ` ``` ` normalmente.
