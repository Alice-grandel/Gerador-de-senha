# Calculadora em Rust

Uma calculadora simples de terminal feita em Rust. Permite somar, subtrair, multiplicar e dividir dois números.

## Como executar

CODIGO PRINCIPAL:

```bash
use std::io;

fn main() {

        println!("[BEM-VINDOS]");

     let num1 = read_number("Digite o primeiro numero?");

     let operator = read_operator("Digite o operador (+,-,*,/)");

     let num2 = read_number("Digite o segundo numero");


     let result = match operator {
        '+' => num1 + num2,
        '-' => num1 - num2,
        '*' => num1 * num2,
        '/' => if num2 == 0.0 {
            println!("Erro divisão por zero");
            return;
        } else {
            num1 / num2
        }
        _ => unreachable!(),
     };

     println!(" {} {} {} = {} ", num1, operator, num2, result);

     println!("Programa encerrado!");

}

fn read_number(prompt: &str) -> f64 {
    loop {
        println!("{}", prompt);
        let mut input = String::new();
        io::stdin().read_line(&mut input).expect("Error");

        match input.trim().parse::<f64>() {
            Ok(num) => return num,
            Err(_) => println!("Erro")
        }

    }
}

fn read_operator(prompt: &str) -> char {
    loop {
        println!("{}", prompt);
            let mut input = String::new();
                io::stdin().read_line(&mut input).expect("Erro");


          let operator = input.trim().chars().next();

          match operator {
            Some('+') | Some('-') | Some('*') | Some('/') => return operator.unwrap(),
        
        _ => {
            println!("Operador invalido");
        }
        

          }

    }
}
```

