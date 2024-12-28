# luhn

```markdown
# Validación de Número de Tarjeta de Crédito

Este repositorio contiene un script en Python que valida números de tarjeta de crédito utilizando el algoritmo de Luhn.

## Descripción

El script proporciona una función `verify_card_number()` que verifica si un número de tarjeta de crédito es válido. Además, una función `main()` que permite la verificación de un número de tarjeta de ejemplo.

## Funciones

### `verify_card_number(card_number)`

Esta función toma como argumento un número de tarjeta de crédito y verifica su validez utilizando el algoritmo de Luhn. Los pasos que sigue la función son los siguientes:

1. Invierte el número de tarjeta.
2. Extrae los dígitos en posiciones impares y los suma.
3. Multiplica por 2 cada dígito en posiciones pares. Si el resultado es mayor o igual a 10, suma los dígitos del resultado.
4. Suma los resultados de los pasos 2 y 3.
5. Si la suma total es divisible por 10, la tarjeta es válida.

```python
def verify_card_number(card_number):
    sum_of_odd_digits = 0
    card_number_reversed = card_number[::-1]  # Invierte el número de tarjeta
    odd_digits = card_number_reversed[::2]  # Obtiene los dígitos en posiciones impares

    for digit in odd_digits:
        sum_of_odd_digits += int(digit)  # Suma los dígitos impares

    sum_of_even_digits = 0
    even_digits = card_number_reversed[1::2]  # Obtiene los dígitos en posiciones pares
    for digit in even_digits:
        number = int(digit) * 2
        if number >= 10:
            number = (number // 10) + (number % 10)  # Suma los dígitos del resultado si es mayor o igual a 10
        sum_of_even_digits += number
    total = sum_of_odd_digits + sum_of_even_digits
    return total % 10 == 0  # Verifica si la suma es divisible por 10
```

### `main()`

Esta función define un número de tarjeta de ejemplo, elimina los guiones y espacios, y verifica si el número de tarjeta es válido utilizando la función `verify_card_number()`. Dependiendo del resultado, imprime "VALID!" o "INVALID!".

```python
def main():
    card_number = '4111-1111-4555-1142'
    card_translation = str.maketrans({'-': '', ' ': ''})  # Elimina guiones y espacios
    translated_card_number = card_number.translate(card_translation)

    if verify_card_number(translated_card_number):
        print('VALID!')
    else:
        print('INVALID!')

main()
```

## Uso

Para utilizar este script, simplemente ejecuta el archivo. El resultado será la validación del número de tarjeta proporcionado en la función `main()`.

```sh
python nombre_del_archivo.py
```
