# Projeto ImageTransform

O projeto consiste em uma plataforma web para aplicar filtros em imagens

## Como executar

Você irá precisar ter instalado em sua maquina, o git e o docker.

- [clone este repositório](https://github.com/mauriciobenjamin700/image-transform.git)
- [clone o repositório da api](https://github.com/mauriciobenjamin700/image-transform-api.git)
- [clone o repositório da web](https://github.com/mauriciobenjamin700/image-transform-web.git)

Dentro deste repositório, use o comando `docker compose up -d --build`

A aplicação web estará [neste link](http://localhost:8080)
A documentação da api estará [neste link](http://localhost:8005)

## Rotas da API

- [Enviar imagem](http://localhost:8005/image/FILTRO_QUE_DESEJA_USAR) : Esta rota exige que o filtro usado seja passado via link, onde caso nao passe, a rota levantara erro.
- [Buscar imagem original](http://localhost:8005/{origin_url}) : Esta rota exige que voce coloque o valor origin_url enviado pela API para retornar a imagem
- [Buscar imagem filtrada](http://localhost:8005/{filtered_url}) : Esta rota exige que voce coloque o valor filtered_url enviado pela API para retornar a imagem

Remenda-se o uso do [postman](https://www.postman.com/) para testar a API e entender as rotas. Tendo o postman instalado, carregue os exemplos salvos no [arquivo de exemplos](/docs/ImageTransform.postman_collection.json)

## Filtros Válidos

Envie sempre os filtros em letras minusculas

```python
    GRAY = "gray"
    BLUR = "blur"
    DETAIL = "detail"
    EDGE_ENHANCE = "edge_enhance"
    EMBOSS = "emboss"
    SHARPEN = "sharpen"
    SMOOTH = "smooth"
```
