# Regras de Desenvolvimento e Stack Tecnológico (AI Guidelines)

Este documento define a stack tecnológica e as regras de uso de bibliotecas para garantir a consistência, manutenibilidade e elegância do código no projeto ShareBox.

## 1. Stack Tecnológico

O ShareBox é construído com as seguintes tecnologias principais:

*   **Frontend:** React 18, TypeScript e Vite.
*   **UI/Design:** Tailwind CSS para estilização e shadcn/ui para componentes de interface.
*   **Roteamento:** React Router DOM para navegação.
*   **Gerenciamento de Dados:** Supabase (PostgreSQL, Auth, Storage) como backend completo.
*   **Cache/Server State:** React Query (@tanstack/react-query) para gerenciamento de dados assíncronos.
*   **Ícones:** Lucide React.
*   **Notificações:** `useToast` (shadcn/Radix) para feedback de ações.
*   **PWA:** Suporte a Progressive Web App (PWA) via `vite-plugin-pwa`.

## 2. Regras de Uso de Bibliotecas e Estrutura

### 2.1. Componentes UI e Estilização

1.  **Prioridade shadcn/ui:** Sempre utilize os componentes existentes em `src/components/ui/` (shadcn/ui) como base para a interface.
2.  **Customização:** Se for necessário criar um componente novo ou customizar um existente, crie-o em `src/components/`. **Nunca modifique** os arquivos dentro de `src/components/ui/`.
3.  **Estilização:** Utilize exclusivamente **Tailwind CSS** para todos os estilos. Garanta que todos os layouts sejam responsivos (mobile-first).

### 2.2. Dados e Backend

1.  **Supabase Client:** Todas as interações com o banco de dados, autenticação e storage devem ser feitas através do cliente Supabase importado de `@/integrations/supabase/client`.
2.  **Data Fetching:** Para operações complexas ou que se beneficiem de cache e retries, utilize o React Query. Para operações simples de CRUD ou autenticação, chamadas diretas ao `supabase` são aceitáveis (como visto nos componentes existentes).

### 2.3. Roteamento e Navegação

1.  **Roteamento:** Use React Router DOM.
2.  **Estrutura de Rotas:** Mantenha a definição de rotas centralizada em `src/App.tsx`.

### 2.4. Notificações

1.  **Feedback de Ação:** Use o hook `useToast` (importado de `@/hooks/use-toast`) para fornecer feedback ao usuário sobre o resultado de ações (sucesso, erro, validação de formulários).

### 2.5. Estrutura de Arquivos

Mantenha a seguinte convenção de diretórios:

*   Páginas (Rotas): `src/pages/`
*   Componentes Reutilizáveis: `src/components/`
*   Hooks Customizados: `src/hooks/`
*   Utilitários: `src/lib/`
*   Integrações de Terceiros: `src/integrations/` (ex: Supabase client).