# vue-boolflix

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Lints and fixes files

```
npm run lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

All'interno di che ciclo vitale devo prendere l'api visto che mi serve modificato in base alla ricerca dell'utente?

Capire se per fare il ciclo nelle serie tv e nei film bisogna fare due cicli for differenti o se basta fare:

```javascript
v-for="(element,index) in array1 || array2"
```

Pushare nell'array generale l'api dei film e quello delle serie tv??

Si possono fare due get in axios??

Posso passare le infomrazioni di un componente figlio ad un componente padre ma usare il suo html all'interno di un altro figlio del padre??
