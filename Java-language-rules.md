## 2.1 Java language rules

### 2.1.1 No ignore excepciones

Nunca debes hacer lo siguiente:

```java
void setServerPort(String value) {
    try {
        serverPort = Integer.parseInt(value);
    } catch (NumberFormatException e) { }
}
```

_Mientras puede pensar que su código nunca encontrará esta condición de error o que no es importante manejarlo, ignorar excepciones como las anteriores crea minas en su código con las que quizá otra persona se tope algún día. Debe manejar cada excepción en su código de alguna manera basada en principios. El manejo específico varía según el caso ._ - ([Android code style guidelines](https://source.android.com/source/code-style.html))

Mire alternativas [aquí](https://source.android.com/source/code-style.html#dont-ignore-exceptions).

### 2.1.2 No capture excepciones genéricas

No debes hacer esto:

```java
try {
    someComplicatedIOFunction();        // may throw IOException
    someComplicatedParsingFunction();   // may throw ParsingException
    someComplicatedSecurityFunction();  // may throw SecurityException
    // phew, made it all the way
} catch (Exception e) {                 // I'll just catch all exceptions
    handleError();                      // with one generic handler!
}
```

Vea el motivo y algunas alternativas [aquí](https://source.android.com/source/code-style.html#dont-catch-generic-exception)

### 2.1.3 No use finalize en el manejo de excepciones

_No usamos finalizadores. No hay garantías de cuándo se llamará un finalizador, o incluso si se llamará en absoluto. En la mayoría de los casos, puede hacer lo que necesita de un finalizador con un buen manejo de excepciones. Si realmente lo necesita, defina un método `close ()` (o similar) y documente exactamente cuándo se debe invocar ese método. Ver `InputStream` para un ejemplo. En este caso, es apropiado pero no obligatorio imprimir un breve mensaje de registro desde el finalizador, siempre que se prevea que no inunde los logs. - ([Android code style guidelines](https://source.android.com/source/code-style.html#dont-use-finalizers))


### 2.1.4 Calificar completamente las importaciones

Malo :( : `import foo.*;`

Bueno :) : `import foo.Bar;`

Mira más información [aquí](https://source.android.com/source/code-style.html#fully-qualify-imports)