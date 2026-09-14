# Ambiente de teste — Sistema de Atendimento ADUSEPS

Este branch é a área de trabalho para atualizar e reestruturar o sistema de atendimento.

## Regra principal

O ambiente deve usar somente o projeto Firebase de demonstração `demo-aduseps-atendimento` e os emuladores locais. Nunca informe as credenciais nem o identificador do projeto de produção neste branch.

## Separação dos ambientes

| Ambiente | Branch | Dados |
| --- | --- | --- |
| Produção atual | repositório e branch atuais da aplicação | Firebase real |
| Reestruturação | `teste-reestruturacao` | somente dados fictícios |
| Validação futura | branch derivada de `teste-reestruturacao` | projeto Firebase separado de homologação |

## Inicialização prevista

1. Colocar a cópia do código analisado neste branch.
2. Copiar `.env.test.example` para `.env.local`.
3. Instalar as dependências com `npm ci`.
4. Iniciar Auth e Firestore locais com `npx firebase-tools emulators:start --config firebase.test.json --project demo-aduseps-atendimento`.
5. Em outro terminal, iniciar a aplicação com `npm run dev`.
6. Usar apenas contas e registros fictícios.

## Proteções obrigatórias

- Exibir “AMBIENTE DE TESTE” com cor visível em todas as páginas.
- Bloquear envio real de e-mail.
- Conectar Auth principal e Auth secundário ao emulador.
- Não aceitar configuração ausente voltando silenciosamente para produção.
- Manter dados dos emuladores em `.firebase-test-data/`, ignorados pelo Git.
- Fazer backup antes de qualquer migração de dados reais.
- Corrigir e testar cada fluxo em branch própria derivada deste ambiente.
- Nunca mesclar automaticamente este branch em produção.

## Primeira sequência de trabalho

1. Importar a versão exata do ZIP revisado.
2. Confirmar que build, tipos e lint executam no branch.
3. Criar dados fictícios repetíveis.
4. Corrigir autenticação, permissões e envio de e-mail.
5. Corrigir concorrência e integridade da fila.
6. Reestruturar Pessoas e Atendimentos.
7. Padronizar visual e navegação.
8. Revisar relatórios e escala.
9. Homologar cada perfil antes de qualquer publicação.

## Critério de segurança

Se os emuladores não estiverem ativos ou `NEXT_PUBLIC_APP_ENV` não for `test`, a aplicação de testes deve interromper a inicialização e explicar a configuração ausente.
