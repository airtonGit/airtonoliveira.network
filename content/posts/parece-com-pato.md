---
title: "Se parece como um pato? Sim!"
date: 2020-06-28T16:39:14-03:00
draft: true
---

### Usando duck typing em GO

Ducktyping na liguagem GO é uma das funcionalidades que acho entre outras incríveis é
uma das que traz mais liberade de criação.

Quando desenvolvemos com linguagens de programação mais convencionais como PHP, C#, Java e C++ temos possibilidades incríveis com orientação a objetos, mas também algumas limitações que o _duck typing_ vem para trazer alternativas ao processo criativo de desenvolver software.

Usando orientação a objetos tradicional temos interfaces que diversas classes podem herdar e gerar objetos da mesma _família_ definida pela interface implementada. Assim podemos definir métodos genéricos que aceitam parametros usando a interface e assim o mesmo pode ser chamado por todos aqueles objetos que implementam esta interface, isso já traz uma liberdade e ao mesmo tempo controle incríveis.

```
// Exemplo em Java
public interface IMensagemPadrao{
    public void setConteudo(String texto);
    public String getConteudo();
}

class OlaMundoMsg implements IMensagemPadrao {
    //obrigatorio definir os métodos da interface IMensagemPadrao
}

(. . .)

//Exemplo de método definido usando interface
void enviar(IMensagemPadrao msg){
    //Pode receber qualquer objeto que implemente IMensagemPadrao
}

(. . .)

// Exemplo chamada do método que implementa IMensagemPadrao e pode utilizar
// método enviar(IMensagemPadrao)
OlaMundoMsg msgOlaMundo = new OlaMundoMsg();
obj.enviar(msgOlaMundo); //Execução ocorre sem problemas
}
```

