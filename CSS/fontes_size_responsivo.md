# CONFIGURANDO TAMANHO DE FONTES RESPONSIVOS E ACESSIVEIS

Para deixar o tamanho de fonte mais responsível e com melhor acessibilidade,
podemos trabalhar com medidas em rem, que tem como base o tamanho da fonte-size da tag html,
e fazer as alterações em porcentagem para cada tamanho do dispositive, assim as fontes irão variar conforme o tamanho da tela do dispositive e também responder ao zoom aplicado pelo usuário.

### Exemplo de estilização com responsividade e acessibilidade.

```css
body,
input,
textarea,
select,
button {
  font: 400 1rem "Roboto", sans-serif;
}

@media (max-width: 1080px) {
  html {
    font-size: 93.75%; //15px
  }
}

@media (max-width: 720px) {
  html {
    font-size: 87.5%; //14px
  }
}
```
