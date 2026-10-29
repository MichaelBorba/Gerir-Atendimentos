# Sistema de Atendimento — demonstração

Sistema web para o dia a dia de unidades de assistência social : registro de atendimentos, agenda de entrevistas domiciliares, relatórios e gestão da equipe.

> **Esta é uma versão de demonstração.** Todos os dados (pessoas, CPFs, endereços, equipe) são **fictícios** e gerados no navegador. Não há login, servidor nem banco de dados: o que você cadastrar ou excluir fica só na memória da aba e **some ao recarregar a página**.


## O que o sistema faz

- **Atendimentos:** cadastro com validação de CPF, histórico, busca por nome/CPF, edição, exclusão e detecção de duplicidade.
- **Visitas domiciliares (Agenda ED):** calendário com visitas urgentes e reagendadas, histórico de reagendamentos, status por etapa e vínculo com entrevistadores.
- **Relatórios:** totais por motivo, gênero, unidade e dia, com impressão e exportação para PDF e Excel.
- **Usuários e níveis de acesso:** administrador, coordenador e atendente, com escopo por unidade e indicador de quem está online.
- **Cadernos por setor:** acompanhamento do andamento de cada caderno e histórico de movimentações.
- **Mensagens do plantão:** avisos da coordenação para toda a equipe ou para atendentes específicos.
- **Fila de envio (Outbox):** registros feitos sem internet ficam guardados e são enviados quando a conexão volta.
- **Segurança de uso:** desconexão por inatividade e limpeza dos dados locais ao sair.

## Como a demonstração funciona

O sistema original usa PostgreSQL com autenticação (via Supabase). Nesta versão, a biblioteca do Supabase foi substituída por um **banco simulado em memória**, embutido no próprio `index.html`, que responde às mesmas chamadas (`from`, `select`, `insert`, `update`, `delete`, filtros, ordenação, paginação e presença online). Por isso o restante do código roda exatamente como na versão real, sem saber que os dados são simulados.

- Nenhuma credencial, URL de servidor ou dado real está no repositório.
- O login é automático, com um usuário administrador fictício.
- As datas dos registros acompanham o dia em que a página é aberta, então a agenda e os relatórios sempre parecem atuais.
- Funções que dependem de servidor (criar usuário, gerar logins, trocar senha) ficam desativadas e mostram um aviso.

## Tecnologias

HTML, CSS e JavaScript puros em um único arquivo, sem etapa de build. Bibliotecas carregadas sob demanda: SheetJS (Excel) e jsPDF com AutoTable (PDF). Consulta de CEP pela API pública ViaCEP.

## Como executar

Abra o `index.html` no navegador, ou publique a pasta no GitHub Pages (**Settings → Pages → Deploy from a branch**).

Também funciona localmente com qualquer servidor estático:

```bash
python3 -m http.server 8000
# abra http://localhost:8000
```

## Capturas de tela

_(adicione aqui imagens do painel, da agenda de visitas e dos relatórios)_

## Aviso

Projeto de portfólio. Qualquer semelhança dos dados exibidos com pessoas reais é coincidência.
