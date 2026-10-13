# Apuração GRESP 2026-2027

Sistema de lançamento, totalização e divulgação dos resultados das **Eleições do Grêmio Estudantil 2026-2027** da **EE Abílio Raposo Ferraz Júnior**, Zona 903ª.

O pacote mantém integralmente os dados do **1º turno** e disponibiliza uma área independente para lançamento e acompanhamento do **2º turno**.

## Arquivos do sistema

- `admin_apuracao.html`: área administrativa, com abas do 1º turno, 2º turno e orientações de publicação.
- `resultado_publico.html`: página destinada à visualização pública dos resultados.
- `resultados.json`: arquivo que reúne os dados do 1º e do 2º turno.
- `aplicacao.js`: funções de cálculo, armazenamento, importação e exportação dos dados.
- `estilo.css`: aparência e formatação das páginas.
- `README.md`: instruções de uso e publicação.

## Como abrir o sistema

1. Extraia todos os arquivos do ZIP para uma única pasta.
2. Não altere a estrutura da pasta e não separe os arquivos.
3. Abra o arquivo `admin_apuracao.html` no Google Chrome ou no Microsoft Edge.
4. Utilize as abas disponíveis para consultar o 1º turno ou lançar o 2º turno.

## Primeiro turno

Os resultados do primeiro turno permanecem preservados no sistema. O preenchimento, a limpeza ou a atualização do segundo turno não deve alterar os dados históricos do primeiro turno.

### Dados preservados

- Eleitores aptos: **746**
- Votantes: **587**
- Votos válidos: **552**
- Votos em branco: **8**
- Votos nulos: **27**
- Ausentes: **159**

### Chapas classificadas para o segundo turno

- **Chapa 99 - Abílio Transforma**
- **Chapa 67 - Chapa da Toddy**

## Como lançar o segundo turno

1. Abra `admin_apuracao.html`.
2. Selecione a aba **2º turno**.
3. Informe a data da votação.
4. Lance, separadamente em cada urna:
   - votos da Chapa 99;
   - votos da Chapa 67;
   - votos em branco;
   - votos nulos.
5. Confira a totalização automática.
6. Clique em **Salvar 2º turno**.

Os dados são inicialmente guardados no armazenamento local do navegador utilizado. Por isso, recomenda-se utilizar sempre o mesmo computador e o mesmo navegador durante a apuração.

## Como manter o `resultados.json` atualizado

Depois de salvar ou corrigir os votos do segundo turno:

1. Clique em **Baixar resultados.json**.
2. Localize o novo arquivo na pasta `Downloads`.
3. Copie o arquivo baixado para a pasta do sistema.
4. Quando o Windows solicitar uma ação, escolha **Substituir o arquivo no destino**.
5. Mantenha uma cópia de segurança do JSON mais recente.

> **Importante:** não limpe os dados do navegador antes de baixar o `resultados.json` atualizado. Os lançamentos feitos na área administrativa permanecem no armazenamento local até serem exportados.

## Importação de um JSON salvo

Para recuperar dados anteriormente exportados:

1. Abra `admin_apuracao.html`.
2. Acesse a aba **Arquivos e publicação**.
3. Selecione o arquivo `resultados.json` mais recente.
4. Aguarde a mensagem de confirmação.
5. Confira os dados do primeiro e do segundo turno antes de continuar.

## Página pública

Para abrir a página pública no mesmo computador, use o arquivo:

```text
resultado_publico.html
```

Um endereço iniciado por `file:///C:/` funciona apenas no computador em que os arquivos estão salvos. Para compartilhar a página com outras pessoas, todos os arquivos do sistema precisam ser publicados em um serviço de hospedagem, como o GitHub Pages.

## Publicação no GitHub Pages

Publique juntos, na raiz do mesmo repositório:

```text
admin_apuracao.html
resultado_publico.html
resultados.json
aplicacao.js
estilo.css
README.md
```

O endereço público terá formato semelhante a:

```text
https://NOME-DO-USUARIO.github.io/NOME-DO-REPOSITORIO/resultado_publico.html
```

Após cada atualização da apuração:

1. Gere um novo `resultados.json` na área administrativa.
2. Substitua o arquivo `resultados.json` no repositório.
3. Confirme a alteração em **Commit changes**.
4. Aguarde a atualização do GitHub Pages.
5. Atualize a página pública com `Ctrl + F5` para evitar a exibição de uma versão armazenada em cache.

## Atenção sobre a atualização pública

Na versão atual do pacote, a área administrativa salva os votos no navegador e permite exportar o JSON. Entretanto, a página pública pode priorizar dados armazenados localmente no navegador em vez de carregar automaticamente o `resultados.json` publicado.

Para divulgação oficial em diferentes computadores, recomenda-se utilizar uma versão em que `resultado_publico.html` carregue automaticamente o arquivo `resultados.json` hospedado. Até que essa integração seja implementada, confira a página pública em outro navegador ou dispositivo antes de divulgar o link.

## Erro HTTP 403 no GitHub

O erro **HTTP 403** normalmente indica que a conta ou o token não possui permissão para gravar no repositório.

Se estiver utilizando um token fine-grained:

1. Autorize o repositório correto.
2. Conceda a permissão **Contents: Read and write**.
3. Verifique se o token não expirou.
4. Não salve o token dentro de arquivos HTML, JavaScript, JSON ou Markdown.

## Segurança e cópias de proteção

- Não compartilhe tokens pessoais do GitHub.
- Não grave senhas ou tokens dentro dos arquivos do sistema.
- Faça uma cópia de segurança do `resultados.json` após cada atualização.
- Antes de substituir um JSON, renomeie a cópia anterior com data e horário, por exemplo:

```text
resultados_backup_2026-10-13_0954.json
```

- Não utilize o botão de limpeza sem antes exportar uma cópia atualizada.
- O comando **Limpar somente o 2º turno** deve preservar o resultado do primeiro turno.

## Conferência antes da divulgação

Antes de publicar o resultado do segundo turno, confirme:

- data da votação;
- votos de cada chapa em cada urna;
- votos em branco e nulos;
- total de votantes;
- quantidade de ausentes;
- soma dos votos válidos;
- percentuais apresentados;
- identificação correta da chapa vencedora;
- preservação integral do resultado do primeiro turno.

## Suporte

Em caso de divergência, mantenha os arquivos existentes, não limpe o navegador e preserve o último `resultados.json` exportado. Esses arquivos permitem recuperar e conferir a apuração.
