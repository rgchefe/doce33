# Landing independente — GitHub Pages

Esta página usa HTML, CSS e JavaScript em um único index.html. Não precisa de Lovable, React, Node, npm ou processo de build.

## Publicar em um repositório novo

1. Crie um repositório público no GitHub, por exemplo acesso-bot.
2. Extraia o ZIP no computador.
3. No repositório, escolha Add file > Upload files.
4. Envie index.html e README.md diretamente para a raiz do repositório. Não envie o ZIP fechado nem coloque os arquivos dentro de outra pasta.
5. Salve com Commit changes.
6. Abra Settings > Pages.
7. Em Source, selecione Deploy from a branch.
8. Em Branch, escolha main e a pasta /(root), depois clique em Save.
9. Aguarde a publicação. A URL será exibida em Settings > Pages. Use a URL do site publicado nos anúncios, não a URL do repositório.

Documentação oficial: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

## Comportamento da landing

- Com ttclid não vazio na URL: carregamento de 1,5 segundo e botão Continuar.
- Sem ttclid ou com ttclid vazio: redirecionamento para uma receita aleatória do TudoGostoso.
- utm_source=tiktok sozinho não libera o botão.
- O botão usa https://paylume.fans/l/339ab47c?shk=fzaxdezw.
- O script da Shark fica antes de </body>, captura os parâmetros solicitados e os repassa ao botão. O shk original é preservado.
- O filtro usa somente o ttclid presente na URL atual; um ttclid antigo salvo não libera acesso direto.

O ttclid não é autenticação: qualquer pessoa com uma cópia do link completo também passa. Esta página estática não comprova que a pessoa viu ou clicou no anúncio. O script depende de JavaScript ativo. sessionStorage mantém os parâmetros na mesma sessão de navegador, mas não garante persistência ao trocar de navegador ou de contexto do aplicativo.

## Testar após publicar

Acesso normal, sem parâmetros: deve redirecionar para uma receita.

Teste somente da interface: acrescente ?ttclid=teste&utm_source=tiktok&utm_campaign=teste ao endereço publicado. Exemplo de formato (substitua usuário e repositório):
https://SEU-USUARIO.github.io/SEU-REPOSITORIO/?ttclid=teste&utm_source=tiktok&utm_campaign=teste

Esse identificador de teste não comprova um clique real ou atribuição. Para a validação final, clique em um anúncio real, confirme que ttclid chegou à landing e use o teste da Shark para verificar o repasse ao destino.

## Alterar o destino

Abra index.html e procure id="bot-link". Edite somente o href para trocar o link de saída. Mantenha as classes cta e button.

## Validação realizada

Sintaxe dos scripts, filtro com e sem ttclid, revelação do botão, preservação de shk e repasse de UTMs e click ID foram verificados. A confirmação dentro da Shark e a publicação do seu novo repositório dependem da configuração dessas plataformas.
