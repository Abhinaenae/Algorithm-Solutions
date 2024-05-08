# Luhn's Algorithm
Luhn's algorithm, also known as the Luhn formula or modulus 10 algorithm, is a simple checksum formula used to validate various identification numbers, such as credit card numbers, IMEI numbers, and National Provider Identifier numbers. It was developed by Hans Peter Luhn in 1954.

The algorithm works by verifying the validity of a number through a series of steps:

  1. Starting from the rightmost digit, double the value of every second digit.
  2. If doubling a digit results in a number greater than 9, subtract 9 from the product.
  3. Sum up all the digits obtained in step 2, along with the unchanged digits.
  4. If the total sum is divisible by 10 (i.e., the modulo 10 operation results in zero), then the number is valid according to Luhn's algorithm.

In simpler terms, Luhn's algorithm doubles every second digit from the right, subtracts 9 from the result if it's greater than 9, sums up all digits, and checks if the total sum is divisible by 10. If the sum is divisible by 10, the number is likely to be valid. This algorithm helps detect common transcription errors and prevents accidental errors in data entry.


More info can be found here: [wikipedia](https://en.wikipedia.org/wiki/Luhn_algorithm)

Python implementation:

Runtime: O(n)
```
def verify_card_number(card_number):
    sum_of_odd_digits = 0
    card_number_reversed = card_number[::-1]
    odd_digits = card_number_reversed[::2]

    for digit in odd_digits:
        sum_of_odd_digits += int(digit)

    sum_of_even_digits = 0
    even_digits = card_number_reversed[1::2]
    for digit in even_digits:
        number = int(digit) * 2
        if number >= 10:
            number = (number // 10) + (number % 10)
        sum_of_even_digits += number
    total = sum_of_odd_digits + sum_of_even_digits
    return total % 10 == 0

def main():
    card_number = input("Input card number: ")
    card_translation = str.maketrans({'-': '', ' ': ''})
    translated_card_number = card_number.translate(card_translation)

    if verify_card_number(translated_card_number):
        print('VALID!')
    else:
        print('INVALID!')

main()
```
