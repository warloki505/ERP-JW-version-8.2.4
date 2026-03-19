# 📚 Índice da Documentação — ERP JW Finance v8.2.3

---

## Documentos Disponíveis

| Arquivo | Onde | O que contém |
|---------|------|--------------|
| `README.md` | raiz | Visão geral, funcionalidades, fórmulas, estrutura, como usar |
| `VERSION.md` | docs/ | Manifesto de versionamento institucional (fonte única + regras SemVer) |
| `CHANGELOG.md` | docs/changelog/ | Histórico completo de versões (v4.x → v8.2.3) |
| `DIARIO_TECNICO.md` | docs/technical/ | Decisões arquiteturais (DEC-001 a DEC-012), regressões (REG-001 a REG-006), checklist de release |
| `BASE_DE_DADOS.md` | docs/technical/ | Schema completo do localStorage (keys, tipos, campos, exemplos) |
| `VALIDACAO_v8.2.3.txt` | docs/validation/ | Checklist ativo — 62 itens de regressão para validação pré-release |
| `ANALISE_SISTEMA_v8.2.3.md` | docs/ | Relatório de qualidade: métricas, validações matemáticas e recomendações (auditável) |
| `archive/` | docs/validation/archive/ | Checklists arquivados de versões anteriores (referência histórica) |

---

## Leitura Recomendada por Perfil

### 🆕 Novo no projeto
1. `README.md` → entender o projeto, a arquitetura e como rodar
2. `VERSION.md` → entender governança de versão (fonte única)
3. `BASE_DE_DADOS.md` → entender como os dados são persistidos no localStorage
4. `CHANGELOG.md` → ver a evolução do projeto e decisões históricas

### 🔧 Vai modificar código
1. `DIARIO_TECNICO.md` → **leia antes de mudar qualquer coisa** — decisões já tomadas e por quê
2. `BASE_DE_DADOS.md` → schema do localStorage (para não quebrar dados existentes)
3. `VALIDACAO_v8.2.3.txt` → o que testar após a modificação

### 🐛 Algo quebrou
1. `DIARIO_TECNICO.md` → seção "Regressões Históricas" e "Checklist de Regressão"
2. `VALIDACAO_v8.2.3.txt` → rodar o checklist completo para isolar o problema
3. `CHANGELOG.md` → ver o que mudou entre versões próximas

---

## Histórico de Novidades

### v8.2.3 (2026-02-19)
- **Dashboard** simplificado: mantém apenas **Score do mês** em formato *pill* minimalista. KPIs individuais de saúde (Poupança, Endividamento, Despesas) removidos do painel visual — os cálculos internos permanecem inalterados.

### v8.2.2 (2026-02-19)
- **PWA/Service Worker** com `CACHE_NAME` sempre alinhado à versão do app — evita cache fantasma após atualização.
- **Gráfico de Evolução do Saldo** com fallback seguro: range inválido cai para mês ativo, sem tela em branco.
- Checklist `VALIDACAO_v8.2.0.txt` movido para `archive/`.

### v8.2.1 (2026-02-18)
- **Gráfico de Evolução do Saldo** respeita o filtro de período via `Core.period.iterateMonths()`.
- **Selects do Dashboard** não duplicam o placeholder "Selecione" após escolha.
- **Inputs de data** restritos ao mês ativo — impede lançamentos fora do período.
- **Tela de Metas** com navegação de mês no topo do card (Anterior / Mês Atual / Próximo).

### v8.2.0 (2026-02-18)
- Reorganização estrutural: `js/core/`, `js/features/`, `js/utils/`.
- Documentação técnica completa: README, CHANGELOG, DIARIO_TECNICO, BASE_DE_DADOS, VALIDACAO.

---

## Convenções do Projeto

| Convenção | Valor |
|-----------|-------|
| Versionamento | SemVer — MAJOR.MINOR.PATCH |
| Prefixo de keys do localStorage | `gf_erp_` |
| Formato de monthId | `YYYY-MM` (ex: `2026-02`) |
| Namespaces globais JS | `ERP_CONST`, `ERP_CFG`, `Core`, `ERP` |
| Tema CSS | Dark mode fixo (sem toggle) |
| Gráficos | Canvas 2D nativo — `SimpleCharts` (sem CDN) |
