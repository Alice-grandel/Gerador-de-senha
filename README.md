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

# EXERCICIOS RUST: 

CALCULADORA:
```bash
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
> Os arquivos são nomeados de forma descritiva, com foco na clareza e na didática.

---

## 🚀 Como estou estudando

Estou estudando Rust diariamente, resolvendo exercícios passo a passo e aplicando boas práticas de código mesmo em problemas simples. A ideia é evoluir gradualmente e usar este repositório para acompanhar meu progresso.

---

## 📌 Observações

- Todos os exercícios foram feitos por mim, com base em listas de lógica e desafios disponíveis na internet ou criados por mim mesma.
- O foco é o **aprendizado**, então nem sempre o código será o mais otimizado — o importante é que funcione e eu entenda o que está acontecendo.

---

## 💬 Contato

Se quiser trocar ideia sobre Rust, lógica de programação ou sugerir melhorias, fique à vontade para abrir uma issue ou me chamar!

}
```

