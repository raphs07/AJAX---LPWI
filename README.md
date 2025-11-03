AJAX---LPWI
============
*Atividade sobre AJAX | Grupo: Anna Beatriz Pereira, Raphaela Pereira de Sousa e Vitória de Sousa Melo.*

Pesquisa Comparativa: XMLHttpRequest vs Fetch vs Promises vs Async/Await
---------
### **1. Introdução**
No desenvolvimento web, a comunicação com servidores para enviar ou receber dados é essencial. Com o tempo, diferentes formas foram criadas para facilitar esse processo:

- *XMLHttpRequest (XHR)* – Método mais antigo.

- *Fetch API* – Substituto moderno e mais simples.

- *Promises* – Forma de lidar com operações assíncronas.

- *async/await* – Sintaxe mais legível para Promises.

### **2. Comparação Geral**


| Método | Ano de surgimento | Estilo de código |Facilidade de uso |Suporte a Promises | Legibilidade | Tratamento de erros |
| --------------:| -----------------:| ----------------:| -----------------:| ------------------:| ------------: |-------------------:|
| XMLHttpRequest | 1999 | Callback | ❌ Baixa | ❌ Não nativo | ❌ Difícil | *Manual (if/else)*|
| Fetch API | 2015 | Promise | ✅ Média | ✅ Sim | ✅ Boa | *.catch()*|
| Promises | 2015 | Promise | ✅ Média | ✅ Sim | ✅ Boa | *.then().catch()* |
| async/await | 2017 | Estilo síncrono | ✅✅ Alta | ✅ Sim | ✅✅ Excelente | *try/catch* |

### **3. Exemplos de cada método**
#### 3.1 XMLHttpRequest

```javascript
const xhr = new XMLHttpRequest();
xhr.open("GET", "https://api.exemplo.com/dados", true);

xhr.onload = function () {
  if (xhr.status === 200) {
    console.log("Resposta:", xhr.responseText);
  }
};

xhr.onerror = function () {
  console.error("Erro na requisição");
};

xhr.send();
```
***Prós:***

- Compatível com todos os navegadores.

***Contras:***

- Verboso, difícil de ler.
- Uso de callbacks (Callback Hell).
- Tratamento de erro manual.

#### 3.2 Fetch API

```javascript
fetch("https://api.exemplo.com/dados")
  .then(response => response.json())
  .then(data => console.log("Resposta:", data))
  .catch(error => console.error("Erro:", error));
```
***Prós:***

- Sintaxe mais simples.
- uporte nativo a Promises.

***Contras:***

- Não rejeita erro para status HTTP 404/500.
- Precisa verificar manualmente com response.ok.

#### 3.3 Promises

```javascript
const obterDados = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve("Dados recebidos"), 1000);
  });
};

obterDados()
  .then(result => console.log(result))
  .catch(error => console.error(error));
```
***Prós:***

- Resolve o problema de callback hell.
- Permite encadeamento.

***Contras:***

- Ainda pode ficar verboso com muitos .then().

#### 3.4 Async/Await

```javascript
async function buscarDados() {
  try {
    const response = await fetch("https://api.exemplo.com/dados");
    const data = await response.json();
    console.log("Resposta:", data);
  } catch (error) {
    console.error("Erro:", error);
  }
}

buscarDados();
```
***Prós:***

- Código mais limpo e organizado.
- Facilita tratamento de erros (try/catch).
- Parece código síncrono.

***Contras:***

- Requer ambiente moderno.
- Precisa de múltiplos await para várias requisições.
