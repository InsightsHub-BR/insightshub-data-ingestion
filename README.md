# Inserção de dados no Insights Hub via Postman

Bem-vindo! 👋
Este repositório reúne exemplos práticos e tutoriais para enviar dados de séries temporais (time series) ao Insights Hub utilizando o Postman.
O objetivo é facilitar a integração de sensores simulados, aplicações e scripts com a plataforma, ajudando desenvolvedores e equipes a testar rapidamente fluxos de ingestão de dados.

Aqui você vai encontrar:

✅ Exemplos prontos de JSON para envio de dados.

✅ Explicações sobre autenticação e headers necessários.

✅ Boas práticas para estruturar assets, aspects e propriedades.

✅ Passo a passo para visualizar os dados no Monitor do Insights Hub.

Este guia foi criado para ser simples e direto, servindo tanto para iniciantes quanto para quem já tem experiência com a plataforma e deseja acelerar a prototipagem de integrações.

**Objetivo:  Obter as credenciais de acesso para autenticação via API. Utilizando developer cockpit**

Passos:
Acesse o Launchpad do Insights Hub (necessário possuir acesso ao Developer Cockpit)

Vá em Settings → Applications.

Clique em “Create App”.

Preencha as informações básicas (nome, descrição etc.) Após isto clique em Role Configure.

![image.png](image.png)

Após salvar, vá até App Credentials, gere um novo acesso clicando em issue access, copie os dados gerados de Client ID e Client Secret. Em seguida clique em Download App Credentials Postman Collection with Examples. (**Guarde as informações apropriadamente, você não irá poder visualiza-las novamente**).

![image.png](image%201.png)

**Objetivo: Inserir os dados no Postman para fazer o envio de dados**

Na tela inicial do Postman selecione import e selecione o arquivo Postman collection. Em seguida selecione a opção Generate App Credential para gerar o access token, copie o Token.

![image.png](image%202.png)

O próximo passo é copiar o assetId do Asset a qual iremos fazer o envio de dados, você consegue visualiza-lo na URL do navegador

![image.png](image%203.png)

Ou se preferir pode utilizar o Get assets of existing tenant

![image.png](image%204.png)

Com essas informações podemos realizar o PUT de dados para o asset desejado. Após o assetId é necessário colocar o aspectname utilziado naquele asset, como no exemplo abaixo.

**PUT:** https://gateway.eu1.mindsphere.io/api/iottimeseries/v3/timeseries/{assetId}/{aspectName}

![image.png](image%205.png)

Configure agora o Authorization, selecione Bearer Token e cole o token previamente gerado.

![image.png](image%206.png)

Após termos o ambiente devidamente configurado, podemos fazer o envio de dados via JSON de duas formas: A primeira é indo até raw e colando o JSON manualmente como no exemplo abaixo: Será necessário usar o seguinte formato personalizado para as células de **timestamp: aaaa-mm-dd"T"hh:mm:ss"Z”**

![image.png](image%207.png)

Após o envio, os dados ficam gravados no asset selecionado dentro do Insights Hub e podem ser acompanhados diretamente pelo Monitor.

![image.png](image%208.png)

O segundo caminho é enviar um arquivo JSON com os dados, para isso selecione binary e escolha o arquivo a ser enviado.

![image.png](image%209.png)
