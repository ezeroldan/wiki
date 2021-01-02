# React

## General
- Jsx extiende js para facilitar escribir componentes
- `<div className="App"></div>` Es traducido a `React.createElement('div', { className: 'App'})`
- `const titulo = <h2>Hola</h2>;` Jsx se puede asignar a una variable
- 

## Extensiones

**Broser:**
- React Developer Tools
- Redux DevTools

**VS Code**
- ES7 React/Redux: rcc

## Generar App
- `sudo npm install -g create-react-app` Instalar generador de apps
- `create-react-app NAME` Generar una app
- `npm start` Ejecutar la app
- `npm run build` Hacer el deploy, genera un carpeta build


## Componentes




```js
import React, { Component } from 'react';

export default class App extends Component {
    render(){ 
        return (
            <div className="App"></div>
        )
    }
}
```

### Jsx
- `{variable}` Interpolacion, imprimir contenido
- `{variable ? <h1>true</h1> : <h1>false</h1>}` Condicional corto
- 



