# Estudos de Python

Repositório criado pra documentar, de forma pública, todo o meu processo de aprendizado de Python — com foco em aplicação na área de cibersegurança.

A ideia é registrar cada tópico estudado em um documento próprio, com explicações em linguagem simples, exemplos práticos e um resumo do que foi aprendido. Serve tanto como material de consulta futura quanto como portfólio do progresso.

---

## Trilha de estudos

Os estudos seguem um plano dividido em módulos, começando pelos fundamentos da linguagem e avançando pra aplicações voltadas a cibersegurança (redes, automação ofensiva, forense e criptografia).

```mermaid
flowchart LR
    subgraph M1["Módulo 1 — Fundamentos"]
        D01["Dia 01 · Números, textos e listas"]
        D02["Próximo doc..."]
    end
    subgraph M2["Módulo 2 — Scripts"]
        D03["..."]
    end
    subgraph M3["Módulo 3 — Redes"]
        D04["..."]
    end
    subgraph M4["Módulo 4 — Automação ofensiva"]
        D05["..."]
    end
    subgraph M5["Módulo 5 — Forense"]
        D06["..."]
    end
    subgraph M6["Módulo 6 — Criptografia"]
        D07["..."]
    end

    D01 --> D02 --> D03 --> D04 --> D05 --> D06 --> D07

    click D01 "./dia-01-introducao-python-numeros-textos-listas.md" "Abrir documento"
```

> O grafo acima cresce conforme os estudos avançam. Cada nó é um documento novo, e as setas indicam a ordem de progressão.

---

## Índice de documentos

| # | Tópico | Módulo | Status |
|---|---|---|---|
| 01 | [Introdução ao Python: números, textos e listas](./dia-01-introducao-python-numeros-textos-listas.md) | Fundamentos | ✅ Concluído |

---

## Estrutura do repositório

```
.
├── README.md
├── dia-01-introducao-python-numeros-textos-listas.md
└── ...
```

Cada arquivo segue o padrão de nome `dia-XX-titulo-do-topico.md`, contendo:

- Fonte de estudo utilizada
- Explicação didática do conteúdo
- Exemplos de código
- Resumo em tabela
- Próximos passos

---

## Objetivo final

Consolidar o aprendizado em um projeto prático aplicado a cibersegurança (ex: ferramenta de OSINT, scanner de vulnerabilidades ou análise de logs), usando como base tudo o que for documentado ao longo da trilha.

---

## Sobre

Estudos conduzidos e documentados por @ewrson_dev, desenvolvedor fullstack e criador de conteúdo educativo sobre desenvolvimento web.