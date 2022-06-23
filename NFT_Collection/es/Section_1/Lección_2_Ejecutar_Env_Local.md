## 📚 Un pequeño manual de blockchain
Antes que nada, necesitaremos que nuestra red Ethereum local funcione. ¡Así es como podemos compilar y probar nuestro código de contrato inteligente! ¿Sabes cómo necesitas hacer girar un entorno local para trabajar? ¡Es lo mismo trato aquí!

Por ahora, todo lo que necesita saber es que un contrato inteligente es un fragmento de código que vive en la cadena de bloques. La cadena de bloques es un lugar público donde cualquiera puede leer y escribir datos de forma segura por una tarifa. Piensa en AWS o Heroku, ¡excepto que nadie lo posee en realidad! Está dirigido por miles de personas al azar conocidas como "mineros".

La gran imagen aquí es:

1 -- Vamos a escribir un contrato inteligente. Ese contrato tiene toda la lógica en torno a nuestros NFT.

2 -- Nuestro contrato inteligente se implementará en la blockchain. De esta manera, cualquier persona en el mundo podrá acceder y ejecutar nuestro contrato inteligente, ¡y les permitiremos mintear NFT!

3 -- Vamos a crear un sitio web para el cliente que permitirá a las personas mintear fácilmente NFT de nuestra colección.

Recomiendo también leer [estos](https://ethereum.org/en/developers/docs/intro-to-ethereum/) documentos cuando puedas para divertirte. En mi opinión, ¡estas son las mejores guías en Internet para comprender cómo funciona Ethereum!

## ⚙️ Configurar herramientas locales

Usaremos mucho una herramienta llamada **Hardhat** que nos permitirá compilar rápidamente contratos inteligentes y probarlos localmente. Primero necesitará obtener node/npm. Si no lo tiene, diríjase [aquí](https://hardhat.org/tutorial/setting-up-the-environment.html).

*Nota: Estoy usando Node 16. Sé que algunas personas han recibido "errores de out of memory" en versiones anteriores del nodo, así que si eso sucede, ¡obtén Node 16!*

```bash
mkdir epic-nfts
cd epic-nfts
npm init -y
npm install --save-dev hardhat
```
Es posible que vea un mensaje sobre vulnerabilidades después de ejecutar el último comando e instalar Hardhat. Cada vez que instala algo de NPM, se realiza una verificación de seguridad para ver si alguno de los paquetes de la biblioteca que está instalando tiene alguna vulnerabilidad informada. ¡Esto es más una advertencia para que estés al tanto! ¡Busca un poco en Google sobre estas vulnerabilidades si quieres saber más!

## 🔨 Haz que el proyecto de muestra funcione

Genial, ahora deberíamos tener hardhat. Vamos a poner en marcha un proyecto de muestra.

```
npx hardhat
```

*Nota: si está en Windows y usa Git Bash para instalar hardhat, es posible que encuentre un error en este paso (HH1). Puede intentar usar Windows CMD para realizar la instalación de HardHat si tiene problemas. Se puede encontrar información adicional [aquí](https://github.com/nomiclabs/hardhat/issues/1400#issuecomment-824097242).*

Elija la opción para crear un proyecto de muestra básico. Di sí a todo.

El proyecto de muestra le pedirá que instale `hardhat-waffle` y `hardhat-ethers`. Estas son otras cosas que usaremos más adelante.

Continúe e instale estas otras dependencias en caso de que no lo haga automáticamente.

```bash
npm install --save-dev @nomiclabs/hardhat-waffle ethereum-waffle chai @nomiclabs/hardhat-ethers ethers
```

También querrá instalar algo llamado **OpenZeppelin**, que es otra biblioteca que se usa mucho para desarrollar contratos inteligentes seguros. Aprenderemos más sobre esto más adelante. Por ahora, solo instálalo :).

```bash
npm install @openzeppelin/contracts
```

Después ejecuta:

```bash
npx hardhat run scripts/sample-script.js
```

Debería ver algo como esto:

![Untitled](https://i.imgur.com/LIYT9tf.png)

Boom! Si ves esto, significa que su entorno local está configurado **y** también ejecutó/implementó un contrato inteligente en una blockchain local.

Esto es bastante épico. Entraremos más en esto, pero básicamente lo que está sucediendo aquí paso a paso es:

1. Hardhat compila su contrato inteligente desde solidity a bytecode.
2. Hardhat activará una "blockchain local" en su computadora. ¡Es como una mini versión de prueba de Ethereum que se ejecuta en su computadora para ayudarlo a probar cosas rápidamente!
3. Hardhat luego "implementará" su contrato compilado en su blockchain local. Esa es la dirección que ves al final. Es nuestro contrato implementado, en nuestra versión mini de Ethereum.

Si tienes curiosidad, no dudes en mirar el código dentro del proyecto para ver cómo funciona. Específicamente, consulte `Greeter.sol`, que es el contrato inteligente, y `sample-script.js`, que en realidad ejecuta el contrato.

Una vez que haya terminado de explorar, pasemos a la siguiente sección y comencemos nuestro propio contrato NFT.

## 🚨 Informe de progreso!

Publica una captura de pantalla de su terminal con el resultado de `sample-script.js` en #progress :).
