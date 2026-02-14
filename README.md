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

#### Logo (Dark)
| Arquivo | Formato | URL |
|---------|---------|-----|
| logo-ecommerce-puro-white.svg | SVG | [Link](https://raw.githubusercontent.com/Ecommerce-Puro/assets/main/global/logo/dark/logo-ecommerce-puro-white.svg) |
| logo-ecommerce-puro-white.png | PNG | [Link](https://raw.githubusercontent.com/Ecommerce-Puro/assets/main/global/logo/dark/logo-ecommerce-puro-white.png) |

#### Favicon
| Arquivo | Formato | URL |
|---------|---------|-----|
| favicon.webp | WEBP | [Link](https://raw.githubusercontent.com/Ecommerce-Puro/assets/main/global/favicon/favicon.webp) |

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
