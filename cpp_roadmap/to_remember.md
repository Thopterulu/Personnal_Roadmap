# things that I didn't learned at school but are very cool

## Union cpp

Voici un exemple de code C++ qui prend un nombre à virgule flottante en entrée, convertit sa représentation binaire IEEE 754 en une valeur entière, puis affiche cette valeur :

```cpp
#include <iostream>
#include <bitset>

union FloatToInt {
    float f;
    int i;
};

int main() {
    float inputFloat;
    std::cout << "Entrez un nombre à virgule flottante : ";
    std::cin >> inputFloat;

    FloatToInt converter;
    converter.f = inputFloat;

    std::bitset<32> binaryRepresentation(converter.i);
    int intValue = binaryRepresentation.to_ulong();

    std::cout << "La valeur en binaire IEEE 754 est : " << binaryRepresentation << std::endl;
    std::cout << "La valeur en entier correspondante est : " << intValue << std::endl;

    return 0;
}
```
Ce code utilise un union pour convertir un nombre à virgule flottante en une valeur entière en interprétant les mêmes octets de mémoire. Il affiche également la représentation binaire IEEE 754 du nombre à virgule flottante. Assurez-vous de compiler ce code avec un compilateur C++ compatible.


User
pourquoi dans le code précédent union conserve les octets de mémoire ?
ChatGPT
Dans le code précédent, l'utilisation d'un union est une technique pour partager la même zone mémoire pour deux types différents (float et int). Cela signifie que, quelle que soit la valeur que vous stockez dans l'union, vous accédez aux mêmes octets de mémoire, mais avec une interprétation différente du contenu.

Le fait que l'union conserve les octets de mémoire est une caractéristique des unions en C++. Lorsque vous stockez une valeur dans la partie de l'union associée au type float (converter.f dans ce cas), les octets de mémoire sont interprétés comme une valeur à virgule flottante en utilisant la représentation IEEE 754. Lorsque vous accédez à la même mémoire en utilisant la partie de l'union associée au type int (converter.i dans ce cas), ces mêmes octets sont interprétés comme une valeur entière.

Cela signifie que, en changeant la valeur de converter.f, vous modifiez également la valeur de converter.i sans avoir à copier explicitement les octets de mémoire. C'est une façon de manipuler la mémoire de manière flexible, mais cela nécessite une certaine prudence, car cela peut entraîner des comportements indéfinis si vous n'êtes pas attentif aux types de données que vous utilisez.


## prototyping functions

```cpp
#include <iostream>
using namespace std;

// Function prototype
int multiplyNumbers(int x, int y);

int main() {
    int num1 = 3, num2 = 7;
    int result = multiplyNumbers(num1, num2); // Calling the function
    cout << "The product is: " << result << endl;
    return 0;
}

// Function definition
int multiplyNumbers(int x, int y) {
    int product = x * y;
    return product;
}
```
