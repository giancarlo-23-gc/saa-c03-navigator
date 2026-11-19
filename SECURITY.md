# Segurança

## Relatar um problema

Não publique vulnerabilidades, tokens, credenciais, arquivos de progresso ou dados pessoais em issues públicas. Use o [formulário privado de vulnerabilidade do GitHub](https://github.com/giancarlo-23-gc/saa-c03-navigator/security/advisories/new), habilitado na distribuição oficial. É necessário entrar em uma conta GitHub.

Informe a versão do aplicativo, o navegador e os passos mínimos para reproduzir, sem segredos nem dados reais de terceiros. O relato fica privado para avaliação do mantenedor; a publicação de detalhes deve aguardar a correção coordenada. Não há prazo de resposta garantido.

Erros de enunciado, gabarito ou explicação continuam no botão **Reportar problema** da questão; não use uma issue pública para uma falha de segurança.

## Modelo de segurança

- O aplicativo é estático e não recebe senhas, pagamentos ou dados pessoais.
- Histórico, respostas e sessões ficam no armazenamento local do navegador.
- O código executado no navegador não contém credenciais.
- A publicação passa por validação de conteúdo, testes e build reproduzível.
- Dependências de GitHub Actions são fixadas por hash de commit.
- O repositório exige hashes completos para ações externas. Checkouts de validação não persistem o token Git, e a chave de distribuição é limitada ao repositório público.
- O endurecimento de novembro de 2026 inclui CSP no HTML compilado, scanner do histórico e isolamento temporário da chave SSH. A disponibilidade no site depende da conclusão dos controles de publicação; consulte o relatório da revisão.
- Os arquivos de conteúdo publicados possuem hashes SHA-256 em `public/content/latest.json`.

## Limites

Links externos para documentação são operados pelos respectivos sites. O projeto não controla disponibilidade, políticas ou conteúdo carregado fora do aplicativo.

Aplicativos em pastas diferentes do mesmo domínio GitHub Pages compartilham a origem do navegador. Identidades PWA e escopos exclusivos evitam confusão de instalação, mas não são uma fronteira de segurança entre códigos da mesma origem. Todos os aplicativos publicados nessa conta precisam ser confiáveis. Um backup exportado contém histórico e respostas: compartilhe-o apenas com pessoas de confiança.

A CSP de produção permite scripts somente da própria origem e estilos inline necessários à interface. Ela é uma defesa adicional; não substitui a revisão do código da mesma origem. Uma política em meta tag não permite impor `frame-ancestors`. O servidor de desenvolvimento é restrito a loopback e não deve ser exposto na rede ou usado como hospedagem pública.

A auditoria completa inclui ferramentas de desenvolvimento. Alertas sem versão corrigida continuam visíveis e podem bloquear uma nova publicação mesmo quando o pacote não integra o JavaScript entregue aos usuários. Não há garantia de ausência absoluta de vulnerabilidades.
