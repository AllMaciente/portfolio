# AGENTS.md

Este arquivo serve como guia para agentes de codificação (incluindo IA) que trabalham neste repositório Astro.js.

## 🚀 Comandos de Desenvolvimento

### Comandos Essenciais
```bash
npm install              # Instala dependências
npm run dev             # Inicia servidor de desenvolvimento em localhost:4321
npm run build           # Build para produção em ./dist/
npm run preview         # Preview do build localmente
```

### Comandos Astro CLI
```bash
npm run astro check     # Verificação de tipos e erros
npm run astro add       # Adiciona integrações
npm run astro -- --help # Ajuda do Astro CLI
```

### Verificação de Tipos (Recomendado)
```bash
npx tsc --noEmit        # Verificação TypeScript sem emitir arquivos
```

### Setup Inicial de Linting (Se necessário)
```bash
npm install --save-dev eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint-plugin-astro
npm install --save-dev prettier prettier-plugin-astro
```

## 📋 Estrutura do Projeto

```
src/
├── assets/          # Imagens e recursos estáticos
├── components/      # Componentes Astro reutilizáveis
│   └── virtualCard/ # Componentes do cartão virtual
├── layouts/         # Layouts Astro
├── pages/           # Rotas/páginas Astro
└── styles/          # CSS global e Tailwind
```

## 🎨 Estilo de Código

### Convenções de Nomenclatura
- **Componentes Astro**: PascalCase (ex: `GitHubAvatar.astro`)
- **Variáveis e funções**: camelCase (ex: `contactItems`, `qrCodeSrc`)
- **Constantes**: SCREAMING_SNAKE_CASE para configurações globais
- **Classes CSS**: seguir convenções Tailwind, prefixo customizado quando necessário

### Importações
```astro
---
// 1. Dependências externas
import { Image } from 'astro:assets';
import { Mail, MapPin } from '@lucide/astro';

// 2. Componentes internos
import Layout from '../layouts/Layout.astro';
import ContactInfo from '../components/virtualCard/ContactInfo.astro';

// 3. Recursos locais
import oldPc from '../assets/oldPc.png';
---
```

### TypeScript e Tipos
- Usar strict mode (configurado)
- Definir interfaces para props de componente:
```astro
---
interface Props {
  title?: string;
  qrCodeSrc?: string;
}
const { title = "AllMaciente" } = Astro.props;
---
```

### Componentes Astro
- Front matter com `---` separado do template
- Props com valores padrão quando apropriado
- Comentários em português quando necessário

## 🎭 Padrões de UI

### Sistema de Cores (Tailwind Custom)
- `bg-bg-*`: Fundos escuros (100-900)
- `text-text`: Texto principal (#e9e8e4)
- `text-indigo-500`: Cor de destaque (#57386f)
- `font-jetbrains-mono`: Fonte principal

### Padrões de Layout
- Container principal com `max-w-md` para mobile-first
- Espaçamento consistente com `gap-*` e `p-*`
- Cards com bordas `border-bg-100` e fundos `bg-bg-*`

### Ícones (Lucide)
```astro
import { Mail, MapPin } from '@lucide/astro';
// Uso: <Icon class="w-4 h-4 text-text" />
```

### Imagens
- Usar `astro:assets` para otimização:
```astro
import { Image } from 'astro:assets';
<Image src={oldPc} alt="Descrição" class="w-full h-full object-cover" />
```

## ♿ Acessibilidade

### Atributos ARIA
- `<section aria-label="descrição">` para seções
- `<nav aria-label="navegação">` para navegação
- Descrições alt descritivas para imagens

### Links Externos
```astro
<a href="https://example.com" target="_blank" rel="noopener noreferrer">
```

### Semântica HTML
- `<main>` para conteúdo principal
- `<section>` para agrupar conteúdo relacionado
- `<h2>` para títulos de seção

## 🔧 Configurações Específicas

### TypeScript
- Configuração extends: `astro/tsconfigs/strict`
- Include: `.astro/types.d.ts`, `**/*`
- Exclude: `dist`

### Tailwind CSS v4
- Configurado via @tailwindcss/vite
- Tema customizado em `src/styles/global.css`

### VSCode
- Extensão recomendada: `astro-build.astro-vscode`
- Launch config para desenvolvimento

## 📝 Conteúdo e Idioma

### Idioma
- Português brasileiro para conteúdo
- Atributo `lang="pt-br"` no HTML
- Comentários em português quando necessário

### Padrões de Texto
- Títulos descritivos e claros
- Textos alternativos significativos
- Labels acessíveis para links

## 🧪 Testes (Sugestão)

Para implementar testes futuros:
```bash
npm install --save-dev @testing-library/dom @testing-library/jest-dom vitest jsdom
npm run test          # Rodar testes
npm run test:watch    # Testes no modo watch
```

## ⚡ Performance

### Boas Práticas
- Usar `astro:assets` para imagens
- Lazy loading para imagens grandes
- Mínimo de JavaScript necessário
- Build estático sempre que possível

### Otimização
- Componentes pequenos e reutilizáveis
- CSS scoped quando necessário
- Mínimo de dependências externas

## 🔄 Manutenção

### Antes de Commitar
```bash
npm run build         # Verificar se build funciona
npx tsc --noEmit      # Verificação de tipos
npm run astro check   # Verificação Astro
```

### Estrutura de Componentes
- Manter componentes pequenos e focados
- Props bem tipadas
- Comportamentos consistentes

## 🌳 Git Flow Básico

### Fluxo de Trabalho
```bash
# Criar nova branch para features
git checkout -b feature/nome-da-feature

# Commitar mudanças
git add .
git commit -m "feat: descricao concisa da mudança"

# Voltar para main e fazer merge
git checkout main
git merge feature/nome-da-feature

# Enviar para remoto
git push origin main
```

### Convenção de Commits
- `feat:` novas funcionalidades
- `fix:` correção de bugs
- `docs:` mudanças na documentação
- `style:` formatação, mudanças visuais
- `refactor:` refatoração de código
- `test:` adição ou correção de testes
- `chore:` manutenção, dependências

### Exemplos
```bash
git commit -m "feat: adicionar componente de cartão virtual"
git commit -m "fix: corrigir responsividade em dispositivos móveis"
git commit -m "docs: atualizar AGENTS.md com git flow"
```

## 🎯 Objetivo do Projeto

Este é um portfólio/cartão de virtual pessoal apresentando:
- Informações profissionais de Allan Gama Maciente
- Links para redes sociais
- Informações de contato
- Design clean e responsivo
- Foco em performance e acessibilidade

## 📚 Recursos Úteis

- [Documentação Astro](https://docs.astro.build)
- [Documentação Tailwind CSS v4](https://tailwindcss.com/docs)
- [Ícones Lucide](https://lucide.dev/icons/)
- [Tipos Astro](https://docs.astro.build/en/reference/typescript-reference/)