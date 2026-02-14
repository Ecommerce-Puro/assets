# Ecommerce Puro — Assets

Repositório de assets visuais do ecossistema Ecommerce Puro. Serve como CDN estática via GitHub para logos, favicons, ícones e demais recursos que precisam de URLs públicas permanentes.

## Estrutura

```
├── _inbox/          → Upload de novos assets (ponto de entrada)
├── global/          → Assets compartilhados entre todos os projetos
│   ├── logo/dark/
│   ├── logo/light/
│   ├── logo/monochrome/
│   ├── favicon/
│   ├── icons/
│   ├── banners/
│   ├── social/
│   └── email/
├── projects/        → Assets específicos por projeto
│   └── <projeto>/   → Mesma sub-estrutura do global
└── logs/            → Log de movimentações
```

## Assets Disponíveis

### Global

#### Logo — Dark (para fundos escuros)
| Arquivo | Formato | URL |
|---------|---------|-----|
| logo-ecommerce-puro-white.svg | SVG | [Link](https://raw.githubusercontent.com/Ecommerce-Puro/assets/main/global/logo/dark/logo-ecommerce-puro-white.svg) |
| logo-ecommerce-puro-white.png | PNG | [Link](https://raw.githubusercontent.com/Ecommerce-Puro/assets/main/global/logo/dark/logo-ecommerce-puro-white.png) |

#### Logo — Light (para fundos claros)
| Arquivo | Formato | URL |
|---------|---------|-----|
| logo-ecommerce-puro-color.svg | SVG | [Link](https://raw.githubusercontent.com/Ecommerce-Puro/assets/main/global/logo/light/logo-ecommerce-puro-color.svg) |
| logo-ecommerce-puro-color.png | PNG | [Link](https://raw.githubusercontent.com/Ecommerce-Puro/assets/main/global/logo/light/logo-ecommerce-puro-color.png) |

#### Favicon
| Arquivo | Formato | Descrição | URL |
|---------|---------|-----------|-----|
| favicon.webp | WEBP | Fundo escuro, letra clara | [Link](https://raw.githubusercontent.com/Ecommerce-Puro/assets/main/global/favicon/favicon.webp) |
| favicon-light.webp | WEBP | Fundo claro, letra escura | [Link](https://raw.githubusercontent.com/Ecommerce-Puro/assets/main/global/favicon/favicon-light.webp) |

## Como Usar

Cada asset tem uma URL pública permanente no formato:

```
https://raw.githubusercontent.com/Ecommerce-Puro/assets/main/<caminho-do-arquivo>
```

Use diretamente em HTML, CSS, emails, ou qualquer contexto web:

```html
<img src="https://raw.githubusercontent.com/Ecommerce-Puro/assets/main/global/logo/dark/logo-ecommerce-puro-white.svg" alt="Ecommerce Puro" />
```

## Adicionando Assets

1. Coloque o arquivo na pasta `_inbox/`
2. O gerenciador (Claude) analisa visualmente, renomeia e move para o destino correto
3. Cada movimentação é registrada em `logs/movements.md`
4. A URL pública fica disponível imediatamente após o push
