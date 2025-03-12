Extraigo las propiedades que me interesan de un objeto

```js
let person = {name: "Peter", age: 30, sex: "M"};

// en una función
let printPerson = ({name, age}) => console.log(`Name: ${name}, Age: ${age}`);
printPerson(person);

// en variables
let {name, age} = person;
```