# Chapter Review

| Question | Answer |
| :---: | :---: |
| Why does C++ have more than one integer type? | Having more than one integer type lets you choose the type that is best suited to a particular need. For example, you could use short to conserve space or long to guarantee storage capacity or to find that a particular type speeds up a particular calculation. |
| What safeguards does C++ provide to keep you from exceeding the limits of an integer type? | C++ provides no automatic safeguards to keep you from exceeding integer limits; you can use the `climits` header file to determine what the limits are. |
| `char grade = 65;`  `char grade = 'A';`  Are they equivalent? | The two statements are not really equivalent, although they have the same effect on some systems. Most importantly, the first statement assigns the letter A to grade only on a system using the ASCII code, while the second statement also works for other codes. Second, 65 is a type int constant, whereas 'A' is a type char constant. |
| How could you use C++ to find out which character the code 88 represents? Come up with at least two ways. | `char c = 88; cout << c << endl; // char type prints as character`          `cout.put(char(88)); // put() prints char as character` `cout << char(88) << endl; // new-style type cast value to char <br/>`  `cout << (char)88 << endl; // old-style type cast value to char` |
| Assigning a long value to a float can result in a rounding error. What about assigning long to double? long long to double? | The answer depends on how large the two types are. If long is 4 bytes, there is no loss. That’s because the largest long value would be about 2 billion, which is 10 digits. Because double provides at least 13 significant figures, no rounding would be needed. The long long type, on the other hand, can reach 19 digits, which exceeds the 13 significant figures guaranteed for double. |

