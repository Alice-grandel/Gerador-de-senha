# Calculadora em Rust

Uma calculadora simples de terminal feita em Rust. Permite somar, subtrair, multiplicar e dividir dois números.

## Como executar

```bash
use std::io;

fn main() {

    let num1 = read_number("Digite o primeiro numero:");

    let operator = read_operator("Digite o operador (+, -, *, /):");

    let num2 = read_number("Digite o segundo numero:");


    let result = match operator {
        '+' => num1 + num2,
        '-' => num1 - num2,
        '*' => num1 * num2,
        '/' => {
            if num2 == 0.0 {
                 println!("Erro: divisão por zero!");
                return;
            } 
                num1 / num2
            
        }
        _ => {
        println!("Operador inválido.");
        return;
       }
};
    println!("O resultado é: {} {} {} = {} ", num1, operator, num2, result);

}



fn read_number(prompt: &str) -> f64 {
    loop {
        println!("{}",prompt);
            let mut input = String::new();
                io::stdin().read_line(&mut input).expect("Error ao ler a linha");

        match input.trim().parse::<f64>() {
            Ok(num) => return num,
                Err(_) =>  println!("Invalid input, please enter a number"),
        
        }
    } 
 }


fn read_operator(prompt: &str) -> char {
    loop {
        println!("{}",prompt);
            let mut input = String::new();
                io::stdin().read_line(&mut input).expect("Error ao ler a linha");

       let operator = input.trim().chars().next();
        match operator {
            Some ('+') | Some ('-') | Some ('*') | Some ('/') => return operator.unwrap(),
            _ => {
                println!("Invalid input, please enter a valid operator");
            }
        }
    } 
 } 
