# Projeto ImageTransform

O projeto consiste em uma plataforma web para aplicar filtros em imagens

## Como executar

Você irá precisar ter instalado em sua maquina, o git e o docker.

- [clone este repositório](https://github.com/mauriciobenjamin700/image-transform.git)

Agora, dentro do repositório `image-transform` faça:

- [Clone o repositório da api](https://github.com/mauriciobenjamin700/image-transform-api.git)
- [Clone o repositório da web](https://github.com/mauriciobenjamin700/image-transform-web.git)

Antes de executar o docker, deve ir na pasta da API **image-transform-api** apagar a pasta **image-transform.db** que tem dentro dela e criar um arquivo chamado `image-transform.db`, depois no terminal dê um `docker compose down`, `docker logs image-transform-ap`, `docker rm -f image-transform-api`

Dentro deste repositório (image-transform), use o comando `docker compose up -d --build`

A aplicação web estará [neste link](http://localhost:8080)

A api estará [neste link](http://localhost:8005)

## Rotas da API

- [Enviar imagem](http://localhost:8005/image/FILTRO_QUE_DESEJA_USAR) : Esta rota exige que o filtro usado seja passado via link, onde caso nao passe, a rota levantara erro.
- [Buscar imagem original](http://localhost:8005/{origin_url}) : Esta rota exige que voce coloque o valor origin_url enviado pela API para retornar a imagem
- [Buscar imagem filtrada](http://localhost:8005/{filtered_url}) : Esta rota exige que voce coloque o valor filtered_url enviado pela API para retornar a imagem

Remenda-se o uso do [postman](https://www.postman.com/) para testar a API e entender as rotas. Tendo o postman instalado, carregue os exemplos salvos no [arquivo de exemplos](/docs/ImageTransform.postman_collection.json)

## Filtros Válidos

Envie sempre os filtros em letras minusculas.

```python
    GRAY = "gray"
    BLUR = "blur"
```

## Navegação das telas

Primeiramente, acesse o site pelo link [neste link](http://localhost:8080) para poder acessar a tela inicial, onde nela tem uma mensagem de boas-vindas e um botão **Adicionar Filtro** que navegara para a tela principal.

### Tela inicial

![tela inicial](./docs/tela%20inicial.jpg)

### Tela principal

Na tela principal, tem dois botões para poder aplicar o filtro na imaguem, onde o primeiro botão é **Tirar foto** para utilizar a camera para tirar uma foto e aplicar filtro nela e o segundo é um botão **Abrir galeria** para utilizar o explorador de arquivo do seu computador para poder selecionar uma foto para aplicar filtro.

![tela principal](/docs/tela%20principal.png)

### Tela tirar foto

Ao clicar no botão **Tirar foto**, é direcionado para uma tela com uma camera para o usuário poder capturar uma foto.

![tela tirar foto](/docs/tela%20tirar%20foto.jpg)

Caso a foto tirada não tiver ficado boa, o usuário terá a opção de tirar novamente outra foto, e se tiver ficado boa, basta clicar no botão confirmar para poder prossegir para a tela de seleção-camera.

![tela foto tirada](/docs/tela%20foto%20tirada.jpg)

### Tela de seleção-camera

Depois da foto tirada e apertar no botão de confirmar, o usuário é direcionado para tela de seleção-camera onde irar selecionar um filtro para aplicar na sua foto. Depois de escolher o filtro, o usuário aperta no botão de salvar onde será direcionado para tela de de resultados.

![Aplicar filtro camera](/docs/aplicar%20filtro%20camera.jpg)

### Tela resultado da foto tirado na câmera

Logo após escolher o filtro e aplicar na foto, a tela de resultado é mostrada com a imagem original e a imagem com o filtro aplicada para o usuário poder visualizar, caso seja o filtro desejado, ele poderá salvar a imaguem no banco de dados, caso ao contrário, ele poderal vltar a tela anterior e escolher outro filtro.

![tela resultado câmera](/docs/resultado%20camera.jpg)

### Tela de selecionar filtro em uma imagem da galeria

Não muito diferente da opção de utilizar a camera, quando o usuário escolhe a opção de abrir imagem da galeria, a tela de selecionar filtro é acessada para o usuário pode escolher uma imagem que está salva no seu computador e aplicar um filtro deseja. Logo após clicar em salvar, o usuário é direcionado para tela de resultado para poder visualizar a imagem original e a com filtro onde ele poderá salvar ou voltar para aplicar outro filtro.

![aplicar filtro na imagem da galeria](/docs/tela%20de%20selecionar%20filtro%20galeria.jpg)

### Tela resultado da imagem da galeria do computador

![tela resultados da imagem da galeria](/docs/tela%20resultado.png)

## Onde encontrar os dados após a execução

Após salvar as imagens com o filtro aplicado, na branch `image-transform`, navegue até a pasta `image-transform-api`, dentro dela deverá acessar as pastas e arquivo:

- Pasta **upload**: Nela é possivel visualizas às imagens originais e dentro dela tem outra pasta chamada **filtered** que é onde as imagens com filtros aplicados são salvas.
- Arquivo `image-transform.db`: nesse arquivo é possival acessar o banco de dados e visualizar o id, nome, url da imagem original, url da imagem com filtro, filtro aplicado, data e hora das imagens que foram aplicado os filtros.