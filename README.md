# Octógono de Esquisitice

Coleção interativa de perfis de personalidade plotados num octógono de 8 eixos. Cada pessoa vira uma "mancha" orgânica suspensa em formol. Site estático, sem build, sem dependências — é só HTML.

## Estrutura

```
octogono-esquisitice/
├── index.html          ← o app inteiro (HTML + CSS + JS)
├── data/
│   ├── people.json     ← AS PESSOAS (a fonte de verdade — edite aqui)
│   └── sources.json    ← lista de arquivos de dados a carregar
└── README.md
```

## Como publicar no GitHub Pages

1. Crie um repositório e suba estes arquivos (mantendo a pasta `data/`).
2. No GitHub: **Settings → Pages**.
3. Em *Source*, escolha **Deploy from a branch**, branch `main` e pasta `/ (root)`.
4. Salve. Em ~1 min o site fica no ar em `https://SEU-USUARIO.github.io/NOME-DO-REPO/`.

## Como adicionar pessoas

### Opção A — editar `data/people.json` (mais simples)

Abra `data/people.json` e adicione um objeto novo na lista. Depois é só subir o arquivo atualizado pro GitHub (pode arrastar o arquivo em **Add file → Upload files** e dar commit). Modelo:

```json
{
  "id": 11,
  "name": "Nome da Pessoa",
  "role": "Profissão",
  "stats": {
    "Excentricidade": 80,
    "Emotividade": 40,
    "Inconveniência": 60,
    "Dialética": 50,
    "Lucidez": 70,
    "Desleixo": 30,
    "Impulsividade": 90,
    "Desassossego": 55
  }
}
```

### Opção B — subir um arquivo novo (sem mexer no que já existe)

1. Crie um arquivo, ex. `data/turma2.json`, com a mesma estrutura (uma lista de pessoas).
2. Adicione o nome dele em `data/sources.json`:

```json
[
  "people.json",
  "turma2.json"
]
```

O app carrega todos os arquivos da lista e junta tudo. Se dois tiverem o mesmo `id`, vence o último.

## Regras dos dados (importante)

- **Valores de 0 a 100** em cada eixo.
- **Os 8 eixos são definidos pela primeira pessoa do arquivo.** Use sempre os mesmos nomes de eixo nas demais. Hoje são: Excentricidade, Emotividade, Inconveniência, Dialética, Lucidez, Desleixo, Impulsividade, Desassossego.
- O leitor é **tolerante**: aceita vírgula sobrando no fim da lista/objeto e não liga pra maiúscula/minúscula nos nomes dos eixos (`Impulsividade` = `impulsividade`).
- `id` e `role` são opcionais (mas recomendados). `color` é ignorado na galeria.

## O que dá pra fazer no app

- **Galeria** com o octógono de cada pessoa; clique pra abrir o detalhe (eixos, classificação e a "leitura do espécime").
- **Ordenar** por índice geral, por qualquer eixo, ou por nome.
- **Comparar** até 4 pessoas com as formas sobrepostas.
- **Arrastar um .json** pra dentro da página pra carregar na hora (ótimo pra testar antes de subir).

## Rodando localmente

Abrir o `index.html` com dois cliques funciona, mas o navegador bloqueia a leitura de `data/` via `file://` — nesse caso o app mostra **dados de demonstração**. Para ver seus dados locais, rode um servidor simples na pasta:

```bash
python3 -m http.server 8000
# abra http://localhost:8000
```

Ou simplesmente arraste seu `people.json` pra dentro da página.

---

*Aferição não-homologada. Não constitui diagnóstico.*
