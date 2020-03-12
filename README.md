## Generating strong random passwords, and storing them for future use

*This project was completed as part of my cursus at Ironhack (a 9-week intensive coding bootcamp).*

This project is composed of **three Python files**, the two first being executable ones:

`password-generator.py` 

This file generates a random password from **a set of custom parameters**, entered as an input by the user:
- the  desired **password length** (max. 20 characters)
- the desired **character types** (uppercase, lowercase, numbers and symbols)

It then displays the **generated password**, along with the associated **security level**. A few details about it:

 - **The security level is defined by the entropy score** (*Very Weak* if <50, *Weak* if 50-60, *Fair* if 60-70, *Strong* if 70-80, *Very Strong* if >80). The entropy *H* is calculated with the formula <a href="https://www.codecogs.com/eqnedit.php?latex=H&space;=&space;log_2&space;N^{L}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?H&space;=&space;log_2&space;N^{L}" title="H = log_2 N^{L}" /></a>, where *N* is the number of possible symbols, and *L* is the number of symbols in the password.
- As the entropy score might not be meaningful to end-users, we rather display the **average time a brute-force attack would need to guess the generated password**. To do so, we assume that the hacking computer could make <a  href="https://www.codecogs.com/eqnedit.php?latex=10^{10}"  target="_blank"><img  src="https://latex.codecogs.com/gif.latex?10^{10}"  title="10^{10}"  /></a> attempts per seconds, and would need to try on average half of possible combinations before actually guessing the right one. In the end, the average guess time (in seconds) is defined by the following formula:\
<a  href="https://www.codecogs.com/eqnedit.php?latex=t&space;=&space;\frac{\frac{N}{2}}{10^{10}}"  target="_blank"><img  src="https://latex.codecogs.com/gif.latex?t&space;=&space;\frac{\frac{N}{2}}{10^{10}}"  title="t = \frac{\frac{N}{2}}{10^{10}}"  /></a>
 - Also, to reduce the probability of getting simple combinations that could be guessed easily, we made sure that **AZERTY keyboard neighbors** (such as 1234, TYUI, etc.) **would never appear in the generated password**. This feature could be improved by adding other keyboard combinations (QWERTY in particular).

If the user is satisfied with the generated password, the program suggests him/her to **save it into a** `saved-passwords` **binary file**, so that he/she can retrieve it later on, launching the `password-directory.py` executable. *If the* `saved-passwords` *file does not exist yet, it will be automatically created in the current working directory.* While saving the password, the user is asked to **indicate the associated website and username**.

 `password-directory.py` 

This file displays the **list of websites for which a password has been saved**, and displays the **associated usernames and passwords** at the demand of the user.

`functions.py`

This file **stores all the functions** that are used in the `password-generator.py`  and  `password-directory.py` files.
