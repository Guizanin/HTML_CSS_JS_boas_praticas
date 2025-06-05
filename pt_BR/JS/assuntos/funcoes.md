# Funções, Métodos

## Funções, Métodos curtos e objetivos
Você já deve ter se deparado com aquelas funções GIGANTESCAS, que fazem de tudo, até fazem café 🤣. Além de dificultarem o entendimento do que fazem, para que existem, tornam o código muito amarrado, quase uma "caixa de Pandora".
Você como desenvolvedor vai notar quando precisa retirar um trecho do seu código e criar outra função com ele.

```js
function atualizaSalvaUsuario(dadosAtualizados, dadosAntigos){
  [...métodos de validação dos dados novos...]
  [...métodos de validação dos dados antigos...]
  [...atualiza objeto com dados novos...]
  [...salva o usuário com dados atualizados...]
  [...realiza alguma função com os dados salvos...]
}
```

Aqui temos um bom exemplo de uma função com muitas responsábilidades e acoplamento. Poderiamos quebrar em diversas funções para cada tipo de ação, e dentro da função principal com o nome de <i>salvaUsuário</i> somente rodar os métodos e ao final feliz somente salvar e o retorno enviar para alguma função para tratamento. 
```js
function validaDados(dados){
  valida dados e retorna
}
function encontraUsuario(dados){
  busca usuário e realiza validações
}
function atualizaUsuario(dados){
  atualiza o objeto usuário
}
function metodosUsuarioSalvo(dados){
  realiza ações com o usuário salvo
}

function salvaUsuario(dadosAtualizados, dadosAntigos){
  1- validaDados(dados)
  2- encontraUsuario(dados)
  3- atualizaUsuario(dados)
  4- metodosUsuarioSalvo(dados)
}
```
Podemos notar agora que a função <i>salvaUsuario</i> é responsável só por orquestrar as chamadas de outras funções que realizam uma série de tarefas que a <i>salvaUsuario</i> não conhece a implementação, ela só chama os responsáveis e no final salva o usuário. 

E agora com funções realizando pequenas tarefas podemos reutilizá-las caso precisemos em outra parte do desenvolvimento 😊.

- Mas como saber quando criar uma função a parte para realizar determinada tarefa?
- Será que irei reutilizá-la algum dia?

Então, dependendo da tarefa, essa tarefa é tão específica se será utilizada somente dentro daquela função ou contexto. Mas quando se trata de algo um pouco mais genérico, muitas vezes você pode deixar esse método dentro da função que o esta utilizando, e se precisar fazer um copia/cola dele, então é a hora de criar uma função específica para ele. 

Muitas das vezes você não terá uma visão do futuro do projeto para saber se deverá criar uma função extra para ele ou não, e está tudo bem, isso faz parte da vida mesmo, até porque ficar criando função específica para tudo é cansativo, pois devem ser levados alguns fatores em questão, organização do local que conterá essa nova função, os parametros que serão recebidos e utilizados. 
O que podemos deixar combinado é, caso precise fazer um copia/cola de algum método para utilizar em outra parte do projeto, pode criar uma função para ele, pois possivelmente ele será reutilizado mais vezes, e também, pelo motivo de manutenção, imagine ter que  buscar no projeto todo os lugares ondem foi colado o método copiado para alterar uma parte dele.