---
title: "Se parece como um pato? Sim!"
date: 2020-06-28T16:39:14-03:00
draft: true
---

### Duck typing

- _Se parece com um pato?_
- _Sim!_
- _Então é um pato!_

Mesmo parecendo ser simples ou fracamente tipado este recurso de GO traz vantagens e uma liberdade
incrível de criação e re-uso no desenvolvimento de software.

No modelo tradicional de definição de tipos, deve existir uma declaração prévia para uso dos objetos.
Se o objeto não implementar a interface exigida na definição do método este não será aceito se passado como parâmetro.

```
// Exemplo em Java
void enviaMsg(IMsgBasica msg){
    // quem precisar chamar este método deve fornecer como 
    // parâmetro msg algum objeto que implemente a 
    // interface IMsgBasica
}

// Exemplo de objeto necessário
class MsgOla implements IMsgBasica{
    (...)
}
```
Utilizando Duck typing em GO qualquer objeto sem uma declaração prévia com interface pode ser utilizado, apenas este deve implementar os métodos que a interface exigem. Assim um objeto pode "implementar" a interface porém sem uma definição formal.

```
// Exemplo em GO
type IMsgBasica interface{
    SetTexto(valor string)
}

// Exemplo de objeto
type MsgOla struct{
    (...)
}

// Ao definir este método MsgOla _se parece_ com IMsgBasica
// logo implementa e pode ser utilizada
func (t *MsgOla) SetTexto(valor string){
    (...)
}
```

A implementação do interface é realizada de forma dinâmica sem estar _hard coded_

```
// continuação, exemplo de uso de MsgOla
func enviaMsg(msg IMsgBasica){
    (...)
}

//criando objeto MsgOla
msg := &MsgOla{}
msg.setTexto(˜Olá duck typing!˜)

// Utilizando corretamente objeto MsgOla onde se 
// exige IMsgBasica
enviaMsg(msg)
```

Para _parecer_ e ser aceito pela interface, o objeto deve implementar **todos** os métodos da mesma.
Se o _pato_ estiver com o bico faltando o mesmo não _se parece com pato_.

Esta liberdade na utilização de interfaces com duck typing é um dos muitos recursos incríveis que mais admiro na linguagem GO.