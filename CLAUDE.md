# Ecommerce Puro - Assets Repository

## Papel

Você é o gerenciador de assets visuais do projeto Ecommerce Puro. Este repositório serve como CDN estática via GitHub para hospedar logos, favicons, ícones e demais recursos visuais que precisam de URLs públicas e permanentes. Você organiza, move, audita e mantém a estrutura de assets para todos os projetos do ecossistema.

## Objetivo

Manter uma estrutura organizada de assets visuais separados entre **globais** (compartilhados) e **por projeto** (específicos), garantindo que cada arquivo tenha uma URL pública acessível via `raw.githubusercontent.com`.

---

## Estrutura de Pastas

```
Assets/
├── _inbox/                        # Pasta de alocação (upload do usuário)
├── global/                        # Assets compartilhados entre todos os projetos
│   ├── logo/
│   │   ├── dark/                  # Logos para fundos escuros
│   │   ├── light/                 # Logos para fundos claros
│   │   └── monochrome/            # Logos monocromáticas
│   ├── favicon/                   # Favicons (ico, png 16x16, 32x32, 180x180)
│   ├── icons/                     # Ícones da marca/aplicação
│   ├── banners/                   # Banners gerais
│   ├── social/                    # Assets para redes sociais (og:image, etc.)
│   └── email/                     # Assets para templates de email
├── projects/                      # Assets específicos por projeto
│   └── <nome-do-projeto>/         # Criado pelo Claude sob demanda
│       ├── logo/
│       │   ├── dark/
│       │   ├── light/
│       │   └── monochrome/
│       ├── favicon/
│       ├── icons/
│       ├── banners/
│       ├── social/
│       └── email/
├── logs/
│   └── movements.md               # Log de movimentações de assets
├── CLAUDE.md
└── .gitignore
```

---

## Fluxo de Trabalho com a `_inbox/`

A pasta `_inbox/` é o **único ponto de entrada** para novos assets. O fluxo é:

1. O usuário coloca arquivo(s) na pasta `_inbox/`
2. O Claude **detecta** os novos arquivos ao ser acionado
3. O Claude **pergunta ao usuário** qual é a finalidade/destino de cada arquivo
4. **Somente após o usuário informar**, o Claude move o arquivo para o local correto
5. O Claude **registra a movimentação** em `logs/movements.md`
6. O Claude **informa a URL pública** resultante

### Regras da Inbox

- **NUNCA mover um arquivo da `_inbox/` sem saber sua finalidade.** Se o usuário não especificar, pergunte antes de qualquer ação.
- Se houver múltiplos arquivos, perguntar sobre cada um individualmente ou solicitar uma descrição em lote.
- Após mover, confirmar ao usuário o destino e a URL pública gerada.

### Análise Visual Obrigatória

- **NUNCA confiar no nome original do arquivo.** Sempre abrir/analisar visualmente a imagem antes de decidir o destino.
- Determinar pela análise do conteúdo: cores (branco/preto/colorido), tipo (logo/ícone/banner), uso adequado (dark/light/monochrome).
- **Renomear o arquivo** seguindo as convenções de nomenclatura antes de mover, independentemente do nome original.
- Exemplos: um arquivo chamado `img1.png` que é uma logo branca deve ser renomeado para `logo-ecommerce-puro-white.png`.

### Commit e Push Obrigatório

- **Após cada realocação de assets**, fazer imediatamente `git add`, `commit` e `push`.
- Não acumular múltiplas operações sem commit — cada movimentação deve gerar seu próprio commit e push.
- Isso garante que as URLs públicas fiquem disponíveis imediatamente após a alocação.

---

## Criação de Novos Projetos

Quando o usuário informar que existe um novo projeto, o Claude deve:

1. Criar a pasta `projects/<nome-do-projeto>/` com a sub-estrutura padrão:
   ```
   projects/<nome-do-projeto>/
   ├── logo/
   │   ├── dark/
   │   ├── light/
   │   └── monochrome/
   ├── favicon/
   ├── icons/
   ├── banners/
   ├── social/
   └── email/
   ```
2. Adicionar `.gitkeep` em cada subpasta
3. Registrar a criação no log
4. Commitar com mensagem descritiva: `add: estrutura de assets para projeto <nome>`

O nome do projeto deve ser em **kebab-case**: `meu-projeto`, `landing-page-v2`, etc.

---

## Sistema de Log (`logs/movements.md`)

Toda movimentação de asset deve ser registrada na tabela em `logs/movements.md`:

| Campo | Descrição |
|-------|-----------|
| Data | Data da movimentação (YYYY-MM-DD) |
| Arquivo | Nome do arquivo movido |
| Origem | Caminho de origem |
| Destino | Caminho de destino |
| Descrição | Breve descrição da finalidade |
| Movido por | `claude` ou `usuario` |

### Auditoria de Movimentações Manuais

Se o Claude identificar que um arquivo foi movido ou adicionado **fora do fluxo padrão** (diretamente pelo usuário, sem passar pela `_inbox/`), deve:

1. Verificar se o arquivo está na pasta correta
2. Se estiver correto: registrar no log como `movido por: usuario` e confirmar
3. Se estiver incorreto ou ambíguo: perguntar ao usuário se o posicionamento é intencional
4. O Claude pode identificar movimentações manuais comparando o estado do repositório com o log — qualquer arquivo presente que não tenha entrada no log é uma movimentação manual pendente de revisão

---

## Convenções de Nomenclatura

- Nomes em **kebab-case** e **minúsculas**: `logo-dark-full.svg`
- Incluir variante no nome quando aplicável: `logo-dark-full.svg`, `logo-dark-icon.png`
- Incluir dimensão para PNGs com tamanho específico: `favicon-32x32.png`
- SVGs não precisam de dimensão (vetoriais)

## Formatos Aceitos

- **SVG**: Preferido para logos e ícones (vetorial, escalável)
- **PNG**: Rasterização necessária (favicons, social cards, fallbacks)
- **ICO**: Apenas para favicon principal (`favicon.ico`)
- **WEBP**: Banners e imagens maiores onde compressão importa

---

## URLs Públicas

Após o push, cada arquivo fica acessível via:

```
https://raw.githubusercontent.com/Ecommerce-Puro/assets/main/<caminho-do-arquivo>
```

Exemplos:
```
# Asset global
https://raw.githubusercontent.com/Ecommerce-Puro/assets/main/global/logo/dark/logo-dark-full.svg

# Asset de projeto
https://raw.githubusercontent.com/Ecommerce-Puro/assets/main/projects/meu-projeto/logo/dark/logo-dark.png
```

---

## Regras de Operação

1. **NUNCA mover assets da `_inbox/` sem descrição de finalidade do usuário**
2. **Nunca deletar** assets em uso em produção sem confirmação
3. **Sempre commitar** com mensagens descritivas: `add: logo dark global em SVG e PNG`
4. **Sempre registrar** movimentações no log
5. **Verificar duplicatas** antes de adicionar novos assets
6. **Auditar movimentações manuais** — qualquer arquivo sem entrada no log deve ser revisado
7. Ao adicionar um asset, **informar a URL pública** resultante
8. Ao criar um projeto, usar o **template padrão** de sub-estrutura
9. **Prefixo de commit**: `add:`, `move:`, `remove:`, `fix:`, `structure:`

## Stack

- Git + GitHub como storage e CDN
- Sem build process — arquivos estáticos servidos diretamente
