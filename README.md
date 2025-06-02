# Calculadora em C++

Uma calculadora simples de terminal feita em C++. Permite somar, subtrair, multiplicar e dividir dois números.

## Como executar

CODIGO PRINCIPAL:

```bash
#include  <iostream>

using namespace std;
        
int main() {

    double n1, n2, resultado;
    char operador, ops;

    do {
    cout << "\nDigite o primeiro numero:\n";
    cin >> n1;

    cout << "\nDigite o operador (+,-,*,/)\n";
    cin >> operador;

    cout << "\nDigite o segundo numero:\n";
    cin >> n2;


    switch (operador) {
        case '+':
            resultado = n1 + n2;
                cout << " O Resultado de " << n1 << " + " <<  n2  << " = " << resultado << endl;
            break;

            case '-':
            resultado = n1 - n2;
                cout << " O Resultado de " << n1 << " - " <<  n2  << " = " << resultado << endl;
            break; 

            case '*':
            resultado = n1 * n2;
                cout << " O Resultado de " << n1 << " * " <<  n2  << " = " << resultado << endl;
            break;

            case '/':
                if (n2 != 0) {
                    resultado = n1 / n2;
                    cout << "O resultado de " << n1 << " / " << n2 << " = " << resultado << endl;
                } else {
                cout << "\nDivisão por zero não é permitida.\n" << endl;
                }
            break;
            default:
            cout << "\nOperador inválido. Tente novamente.\n" << endl;

    }
    cout << "\nDeseja realizar outra operação? (s/n)\n";
    cin >> ops;

    } while (ops == 's' || ops == 'S');

    cout << "\nObrigado por usar a calculadora. Operação encerrada!\n" << endl;


    return 0;
}
```

