# React

## Extensiones

**Broser:**
- React Developer Tools
- Redux DevTools

**VS Code**
- ES7 React/Redux: rcc

## Generar App
- `npx create-react-app my-app` Generar una app
- `npm start` Ejecutar la app
- `npm run build` Hacer el deploy, genera un carpeta build

- `create-react-app NAME --template typescript` Generar una app con TypeScript

- `npm install node-sass --save` usar sass

## General
- Jsx extiende js para facilitar escribir componentes
- `<div className="App"></div>` Es traducido a `React.createElement('div', { className: 'App'})`
- `const titulo = <h2>Hola</h2>;` Jsx se puede asignar a una variable

## Componentes
- `state` Define la data interna del componente
  - `this.setState({ clicked: true })` Para actulizar el valor del state
- `static propTypes = {}` Declarar los tipos de props de `import PropTypes from 'prop-types';`
  - PropTypes.array
  - PropTypes.bool
  - PropTypes.func
  - PropTypes.number
  - PropTypes.object
  - PropTypes.string
  - PropTypes.symbol
  - PropTypes.any
  - PropTypes.oneOfType([])
  - `.isRequired` Para declararlo obligatorio
- `static defaultProps = {}` Declarara los datos default de las props
- `this.props.children` Donde se listan los componentes hijes


```js
import React, { Component } from 'react';
import PropTypes from 'prop-types';

export default class App extends Component {
    
  static propTypes = { texto: PropTypes.string.isRequired }
  static defaultProps = { texto: 'jaja' }

  state = { }

  render() { 
    return (
      <div className="App" style={{ color: 'red' }}>
        {this.props.texto}
      </div>
    )
  }

}
```

## Jsx
- `{variable}` Interpolacion, imprimir contenido
- `{variable ? <h1>true</h1> : <h1>false</h1>}` Condicional corto
- `style={{ name: value }}` Inline style, tambien se pueden pasar mediante variables
- `{/* a comment */}` Comentario
- `{' '}` Esto representa un espacio. `{' '}Palabra` Esto representa un enter
- `{'\u00A9 2017'}` Para poner entities usar las de js
- `class` pasa a ser `className`
- `for` pasa a ser `htmlFor`
- Como jsx es js, se puede usar todas las funciones como `map(item => {})`, `foreach(item => {})`
- `src={item.img}` Para pasar datos no se usa `=""`, se usa `={}`
- `<React.Fragment>` Es para no usar un parent en el return. Tambien es `<></>`
- Eventos: onClick, onScroll, onLoad, onSelect, onDoubleClick, onChange, onSubmit, etc.
  - Reciben una funcion `onClick={this.onShow.bind(this, var)}`. 
  - Para no tener que bindear, se puede asignar un arrow funcion `onShow = (var, event) => { }`
- `React.createContext()` Permite usar el state compartido con los hijos
  - `<Context.Provider value={this.state}>{this.props.children}<Context.Provider>` 
  - Hace como un hook con los props para ejecutar metodos
- `<input value={nombre} name="nombre" onChange={onChange}/>`
  - `onChange = e => this.setState({ [e.target.name] : e.target.value })`
- `<input defaultValue={nombre} ref={this.nombreInput} />` Referenciar y passar valor default
  - `this.nombreInput = React.createRef();` 
  

# React Native






