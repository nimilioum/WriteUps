# Baby-IQ

-----------------------------

Use [this](https://github.com/nimilioum/WriteUps/blob/main/2021/S4CTF/crypto/Baby-IQ/Baby-IQ_58a2860994ee3c83a883945d71387cca08334a4d.txz) simple crypto algorithm to learn about padding and evaluate yourself on how well you understand algorithms.

-----------------------------

### Approach:

Looking at the source code we can see that the pad and chunkchunk
functions create a square matrix of the flag.

Then, the encrypt function iterates the matrix spirally and appends
each index to a temp list, and finally converts the list to a
square matrix.

| 1  | 2   | 3   |
| ---|:---:| ---:|
| 4  | 5   | 6   |
| 7  | 8   | 9   |

The matrix above turns into this :

| 1  | 2   | 3   |
| ---|:---:| ---:|
| 6  | 9   | 8   |
| 7  | 4   | 5   |

Finally, in the last lines we can see that the flag gets encrypted
n times, where n stands for number of rows. Since the encrypted flag
has 6 rows, we need to decrypt it 6 times!

The decryption goes like this :

| 1  | 2   | 3   |
| ---|:---:| ---:|
| 4  | 5   | 6   |
| 7  | 8   | 9   |

The matrix above turns into this :

| 1  | 2   | 3   |
| ---|:---:| ---:|
| 8  | 9   | 4   |
| 7  | 6   | 5   |

-----

With the explanation aboce, the encoded flag :

    enc = [[122, 83, 52, 67, 84, 70],[89, 114, 79, 48, 67, 125], [95, 121, 114, 53, 116, 55], [123, 95, 80, 51, 52, 95], [102, 115, 114, 95, 119, 107], [52, 117, 109, 33, 97, 112]]

turns into this after 6 times of decryption :

    [[122, 83, 52, 67, 84, 70], [123, 51, 52, 115, 89, 95], [67, 114, 121, 80, 116, 79], [95, 57, 97, 53, 107, 95], [102, 48, 114, 95, 119, 52], [114, 109, 117, 112, 22, 125]]

After flattening the matrix and turning to ASCII we get this string :

ZS4CTF{34sY_CryPtO_7a5k_f0r_w4rmup!}

-----------------

## Flag
S4CTF{34sY_CryPtO_7a5k_f0r_w4rmup!}
