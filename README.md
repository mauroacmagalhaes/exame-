# Filmoteca — Arquivo Digital de Películas

Aplicação web interativa que consome dados locais de forma assíncrona (`movies-250.json`) e permite pesquisar e filtrar filmes por ano e género.

Desenvolvido no âmbito do exercício **"Desenvolvimento Web com Filtros e Carga Assíncrona (JSON)"**.

---

## 📁 Estrutura do projeto

```
filmoteca/
 ├── index.html        → aplicação (HTML + CSS + JavaScript num único ficheiro)
 ├── movies-250.json    → base de dados dos filmes
 └── README.md          → este ficheiro
```

Os dois primeiros ficheiros **têm de estar na mesma pasta**, porque o `index.html` carrega o JSON pelo nome relativo `movies-250.json`.

---

## ⚙️ Funcionalidades

| Requisito | Implementação |
|---|---|
| Carga assíncrona | `fetch('movies-250.json')` com `async/await` dentro de um `try/catch` |
| Procura por ano | Campo de texto + botão "Procurar" (ou tecla Enter); filtra por correspondência exata ao ano |
| Filtro por género | `<select>` (dropdown) preenchido dinamicamente com os géneros existentes no JSON |
| Combinação de filtros | Ano e género podem ser aplicados em simultâneo |
| Cartões de detalhe | Título, Ano, Género, Realizador, Elenco, Sinopse, Póster e Pontuação IMDb |
| Estado vazio / erro | Mensagens dedicadas quando não há resultados ou o JSON falha a carregar |

---

## ▶️ Como executar

O `fetch()` só funciona a partir de um **servidor local** — abrir o `index.html` com duplo clique (protocolo `file://`) faz o browser bloquear o pedido ao JSON.

### Opção A — VS Code + Live Server (recomendado)
1. Instala o [Visual Studio Code](https://code.visualstudio.com/).
2. Abre a pasta do projeto (`File` → `Open Folder`).
3. Instala a extensão **Live Server** (autor: Ritwick Dey).
4. Botão direito sobre `index.html` → **"Open with Live Server"**.
5. Abre automaticamente em `http://127.0.0.1:5500`.

### Opção B — Terminal com Python
```bash
cd caminho/para/filmoteca
python3 -m http.server 8000
```
Depois abrir `http://localhost:8000` no browser.

### Opção C — Terminal com Node.js
```bash
npx serve .
```

---

## 🗂️ Estrutura do ficheiro `movies-250.json`

Cada filme segue este formato:

```json
{
  "id": 1,
  "title": "O Poderoso Chefão",
  "year": 1972,
  "genre": "Drama",
  "director": "Francis Ford Coppola",
  "actors": ["Marlon Brando", "Al Pacino", "James Caan"],
  "plot": "Sinopse do filme...",
  "imdb": 9.2,
  "poster": "URL da imagem do póster"
}
```

⚠️ **Nota:** o ficheiro incluído neste projeto contém 59 filmes reais criados como conjunto de dados de demonstração, já que o `movies-250.json` original do enunciado não foi fornecido. Para usar o ficheiro oficial da disciplina:
1. Substitui `movies-250.json` pelo ficheiro fornecido pelo professor (mantendo o mesmo nome).
2. Confirma que os nomes dos campos coincidem com a tabela acima — se forem diferentes (ex. `titulo` em vez de `title`), é necessário ajustar as referências no `<script>` dentro de `index.html` (função `cardTemplate` e `populateGenres`).

---

## 🎨 Notas de design

O visual segue uma linguagem de "catálogo de arquivo de cinema": fundo escuro, tipografia de marquise (Bebas Neue) para títulos, serifada (Playfair Display) para nomes de filmes, monospace (IBM Plex Mono) para metadados, e uma faixa decorativa com perfurações que evoca uma película de filme.

---

## 🛠️ Tecnologias

- HTML5, CSS3, JavaScript puro (vanilla) — sem frameworks nem dependências externas de build.
- Google Fonts (Bebas Neue, Playfair Display, IBM Plex Mono).
- Nenhuma biblioteca externa de JavaScript é necessária.
