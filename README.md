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
