Angular2 Quickstart!
===================


Breve guia de instalação do **Angular 2** .

----------


Intalação
-------------

1. Faça clone do repositótio **quickstart** 
```
git clone https://github.com/angular/quickstart.git quickstart 
```
2. Entrar na pasta do repositório clonado e criar dois arquivos:
```
cd quickstart  
touch index.html  
touch app.es6 
```
> **Nota:**

> - A extensão **.es6** significa que o arquivo usa a sintaxe do ES6, caso o editor não suporte utilizar **.js**.
> 

----------


Componentes
-------------------

Abrir arquivo **app.es6** e iniciar com o seguinte código:
```
import {Component, Template, bootstrap} from 'angular2/angular2'; 
```
> **Nota:**
> - Há 3 módulos sendo importados (Component, Template, boostrap) do Angular2.

Definição de componente:
```
// Annotation section
@Component({
  selector: 'meu-app'
})
@Template({
  inline: '<h1>Hello {{ name }}</h1>'
})
// Component controller
class MyAppComponent {  
  constructor() {
    this.name = 'Nágila';
  }
}
```

> **Nota:**
A UI é representada e estruturada por componentes, um componente consiste de 2 partes:
> - Annotation section,
> - Component controller.

----------


Component Annotation
-------------

Component annotation fornece metadados sobre o componente. São identificados pelo sinal de arroba **(@)**.

O @Component annotation define a tag de HTML para o componente especificando o selector de CSS do componente.
```
@Component({
  selector: 'meu-app' // Define a tag <meu-app></meu-app>
})
```
A *@Template annotation* define o HTML que representa o componente.
```
@Template({
  inline: '<h1>Hello {{ name }}</h1>' // Define um template inline para o  componente
})
```

----------


Template e component controller
--------------------

O *component controller*, é o suporte do *template*. Um *component controller* usa sintaxe de class do ES6.
```
class MyAppComponent {  
  constructor() {
    this.name = 'Bruno';
  }
}
```


### Inicialização

Na parte inferior do ***app.es6***, chamar a função ***bootstrap()*** para carregar o componente na página:
```
bootstrap(MyAppComponent); 
```
*A função **bootstrap()** pega o component como um parâmetro, habilitando o component (assim como qualquer component filho) para renderizar.*

### Declarar o HTML
Dentro da tag head do index.html, inclua o arquivo *es6-shim.js*. (O código do *es6-shim* deve carregar antes de qualquer código do aplicativo.) Em seguida, instanciar o componente **meu-app** no body.

```
<!-- index.html -->  
<html>  
  <head>
    <title>Angular 2 Quickstart</title>
    <script src="dist/es6-shim.js"></script>
  </head>
  <body>
    <h1>Angular 2 Quickstart</h1>
    <!-- O component criado em app.es6 -->
    <meu-app></meu-app>

  </body>
</html>   
```

### Carregando *component*

```
    <script>
      // Sobrescreva os caminhos para carregar os arquivos
      System.paths = {
        'angular2/*':'/angular2/*.js', // Angular
        'rtts_assert/*': '/rtts_assert/*.js', //Runtime assertions
        'app': 'app.es6' // O meu-app component
      };

      // Pontapé inicial
      System.import('app');
    </script>  
```

>**system.js**
> **System** é uma biblioteca de terceiro de código aberto que adiciona a funcionalidade de carregamento de módulos ES6 para navegadores.
