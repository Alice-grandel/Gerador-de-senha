# 🧠 Exercícios de Lógica de Programação em Rust

Este repositório contém exercícios de lógica de programação que estou resolvendo para treinar minha base em desenvolvimento e fortalecer meu raciocínio lógico, usando a linguagem **Rust**.

---

## ✍️ Objetivo

Praticar lógica de programação e registrar minha evolução nos estudos com Rust. Aqui você encontrará exercícios envolvendo:

- Variáveis e tipos de dados em Rust
- Condicionais (`if`, `else`)
- Laços de repetição (`for`, `loop`)
- Funções
- Vetores (`Vec<T>`)
- Desafios diversos de lógica

---

# EXERCICIOS RUST: 1

CALCULADORA SIMPLES:

Crie um programa que funcione como uma calculadora básica, realizando operações matemáticas entre dois números fornecidos pelo usuário.
Funcionalidades:

    Solicitar ao usuário que digite dois números.

    Solicitar qual operação matemática deseja realizar:

        Soma (+)

        Subtração (-)

        Multiplicação (*)

        Divisão (/)

    Realizar a operação escolhida e mostrar o resultado.

    Caso o usuário escolha uma operação inválida, exibir uma mensagem de erro.

    Perguntar ao usuário se deseja realizar outra operação, repetindo o processo enquanto desejar.

 # Codigo:    
```
use std::io;

fn main() {

    loop {

    println!("[BEM-VINDOS]");

    let num1 = read_number("Digite o primeiro numero");
        let operator = read_operator("Digite o operador (+,-,*,/)");
    let num2 = read_number("Digite o segundo numero");


    let result = match operator {
        '+' => num1 + num2,
        '-' => num1 - num2,
        '*' => num1 * num2,
        '/' => if num2 == 0.0 {
            println!("Erro de divisao por zero");
            return;
        } else {
            num1 / num2
        }
        _ => unreachable!()
    }; 

    println!("{} {} {} = {}", num1, operator, num2, result);


        println!("Gostaria de refazer [S/N]?");

    let mut respostas = String::new();
    io::stdin().read_line(&mut respostas).expect("Erro");

    if respostas.trim().eq_ignore_ascii_case("n") {
        println!("Programa encerrado!")
    }

    }   

}

fn read_number(prompt: &str) -> f64 {
    loop{
    println!("{}", prompt);
    let mut input = String::new();
    io::stdin().read_line(&mut input).expect("Erro");

    match input.trim().parse::<f64>() {
        Ok(num) => return num,
        Err(_) => println!("Erro"),
        }

     }
 } 


fn read_operator(prompt: &str) -> char {
    loop{
        println!("{}", prompt);
        let mut input = String::new();
         io::stdin().read_line(&mut input).expect("Erro");

        let operador = input.trim().chars().next();

        match operador {
            Some('+') | Some('-') | Some('*') | Some('/') => return operador.unwrap(),
            _ => {     
                println!("Operador invalido")
            }

        } 


    }
```

## 🚀 Como estou estudando

Estou estudando Rust diariamente, resolvendo exercícios passo a passo e aplicando boas práticas de código mesmo em problemas simples. A ideia é evoluir gradualmente e usar este repositório para acompanhar meu progresso.

---

## 📌 Observações

- Todos os exercícios foram feitos por mim, com base em listas de lógica e desafios disponíveis na internet ou criados por mim mesma.
- O foco é o **aprendizado**, então nem sempre o código será o mais otimizado — o importante é que funcione e eu entenda o que está acontecendo.


# EXERCICIO RUST: 2

FOLHA DE PAGAMENTO:

Faça um programa para cálculo de uma folha de pagamento, considerando os seguintes descontos e regras:

    Imposto de Renda (IR) descontado conforme tabela do salário bruto:

        Até R$ 900,00 (inclusive): isento

        Até R$ 1500,00 (inclusive): 5%

        Até R$ 2500,00 (inclusive): 10%

        Acima de R$ 2500,00: 20%

    Desconto de 10% para o INSS.

    FGTS corresponde a 11% do salário bruto, mas não é descontado do trabalhador — é um depósito feito pela empresa.

    O salário líquido é o salário bruto menos os descontos (IR + INSS).

O programa deverá solicitar ao usuário:

    Valor da hora trabalhada.

    Quantidade de horas trabalhadas no mês.

    Exemplo de saída: 
    Salário Bruto:                 : R$ 1100,00
    IR (5%)                       : R$   55,00
    INSS (10%)                    : R$  110,00
    FGTS (11%)                    : R$  121,00
    Salário Líquido               : R$  935,00

# Codigo:     
```
use std::io;

fn main() {


    loop {
        println!("[BEM-VINDO]");

    let salario = read_number("Digite o seu salario");
     let hora_trabalhada = read_number("Quantas horas vc trabalha por mes?");

     let percentual: f64;
      let salario_bruto = salario * hora_trabalhada;

    if salario_bruto <= 900.0 {
        percentual = 0.0; 
    }else if salario_bruto <= 1500.0 {
        percentual = 5.0;
    } else if salario_bruto <= 2500.0 {
        percentual = 10.0;
    } else {
        percentual = 20.0;
    }

    let ir = salario_bruto * (percentual / 100.0);
     let inss = salario_bruto * 0.10;
    let fgts = salario_bruto * 0.11;
     let salario_liquido = salario_bruto - ir - inss;

    println!("[FOLHA-DE-PAGAMENTO]");
    println!("Salario bruto:  R${:.2}", salario_bruto);
    println!("IR:(5%)  R${:.2}", ir);
    println!("INSS:  R${:.2}", inss );
    println!("FGTS:  R${:.2}", fgts);
    println!("----------------------------------");
    println!("Salario liquido:  R${:.2}", salario_liquido);


    println!("Voce gostaria de refazer [S/N]?");
     let mut respostas = String::new();
      io::stdin().read_line(&mut respostas).expect("Erro");

      if respostas.trim().eq_ignore_ascii_case("n") {
        println!("Programa encerrado");
         break;
      }


  }

}

fn read_number(prompt: &str) -> f64 {
    loop{
        println!("{}",prompt);
         let mut input = String::new();
          io::stdin().read_line(&mut input).expect("Erro");

        match input.trim().parse::<f64>() {
            Ok(num) => return num,
             Err(_) => println!("Valor invalido"),
        }
    }
}

```

# EXERCICIO RUST: 3

TABUADA: Desenvolva um programa que faça a tabuada de um número qualquer inteiro que será digitado pelo usuário, mas a tabuada não deve necessariamente iniciar em 1 e terminar em 10, o valor inicial e final devem ser informados também pelo usuário, conforme exemplo abaixo:
```
Montar a tabuada de: 5
Começar por: 4
Terminar em: 7

Vou montar a tabuada de 5 começando em 4 e terminando em 7:
5 X 4 = 20
5 X 5 = 25
5 X 6 = 30
5 X 7 = 35
```
CODIGO:
```
use std::io;

fn main() { 

    let numero = read_number("Digite um numero");
    let comecar = read_number("Começar por: ");
    let terminar = read_number("terminar por: ");


    for i in comecar..=terminar {
        let result = numero * i;
        println!("{} X {} = {}", numero, i, result);
    }


}

fn read_number(prompt: &str) -> i32 {
    loop {
        println!("{}",prompt);
         let mut input = String::new();
          io::stdin().read_line(&mut input).expect("Erro");

          match input.trim().parse::<i32>() {
            Ok(num) => return num,
             Err(_) => println!("Valor invalido"),
           } 
    }
}
```
# EXERCICIO RUST: 4

CAIXA ELETRONICO: Faça um Programa para um caixa eletrônico.
```
O programa deverá perguntar ao usuário a valor do saque e depois informar quantas notas de cada valor serão fornecidas.

As notas disponíveis serão as de 1, 5, 10, 50 e 100 reais. O valor mínimo é de 10 reais e o máximo de 600 reais.

O programa não deve se preocupar com a quantidade de notas existentes na máquina.

Exemplo 1: Para sacar a quantia de 256 reais, o programa fornece duas notas de 100, uma nota de 50, uma nota de 5 e uma nota de 1;

Exemplo 2: Para sacar a quantia de 399 reais, o programa fornece três notas de 100, uma nota de 50, quatro notas de 10, uma nota de 5 e quatro notas de 1.
```
CODIGO:

```
use std::io;

fn main() {


    loop {

        // apresentação do programa
        println!("\nCAIXA-ELETRONICO]\n");
        println!("\nnotas disponiveis: 100 reais , 50 reais, 20 reais , 10 reais, 5 reais, 1 real\n");

        // input que pede ao usuario pra escrever o valor que deseja sacar
        let saque = read_number("\nQuanto você deseja sacar? valor de R$10.0 reais a R$600.0 reais disponiveis\n");

        // operção que diz quantas notas vão ser fornecidas
        if saque >= 10 && saque <= 600 {
          println!("Saque autorizado de {} reais ", saque);

          let mut valor_restante = saque;
          
            let nota100 = valor_restante / 100;
             valor_restante %= 100;
            
            let nota50 = valor_restante / 50;
             valor_restante %= 50;
            
            let nota20 = valor_restante / 20;
             valor_restante %= 20;

            let nota10 = valor_restante / 10; 
             valor_restante %= 10;
            
            let nota5 = valor_restante / 5;
             valor_restante %= 5;

            let nota1 = valor_restante / 1;
             valor_restante %= 1; 


             println!("[NOTAS-FORNECIDAS!]");
             read_nota(nota100, 100);
             read_nota(nota50, 50);
             read_nota(nota20, 20);
             read_nota(nota10, 10);
             read_nota(nota5, 5);
             read_nota(nota1, 1);

              if valor_restante > 0 {
                println!("n foi possivel fornecer notas para R${} de reais", valor_restante);
            }
        } else {

            println!("Valor invalido tente algo entre 10 a 600 reais");
        }


        println!("---------------------------------------------");

            // loop pra repetir o programa ou encerrar
            println!("Deseja voltar e recomeçar a operação [S/N]?");
            let mut respostas = String::new();
             io::stdin().read_line(&mut respostas).expect("Erro");

            if respostas.trim().eq_ignore_ascii_case("n") {
                println!("operação encerrada");
                break;
            }
        }

}


// função das notas
fn read_nota(quantidade: i32, valor: i32) {
    if quantidade > 0 {
        println!("{} notas fornecidas de {} reais", quantidade, valor);
    }
}

// função do input
fn read_number(prompt: &str) -> i32 {
    loop {
        println!("{}", prompt);
         let mut input = String::new();
          io::stdin().read_line(&mut input).expect("Erro");

          match input.trim().parse::<i32>() {
            Ok(num) => return num,
            Err(_) => println!("Valor invalido"),
          }
    }
}
```
