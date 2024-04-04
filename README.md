# Oprea George
## 324CBa
### Tema1-AA-Masina Turing-Decodificator Morse

#### Implementare-Traducere
Masina Turing implementata in fisierul `morse.tms` functioneaza astfel:
Odata ce a fost introdus sirul de input, masina este in starea `q0`, care parcurge tot sirul si pune un `=` la finalul sirului. Dupa ce ajunge la final si scrie, trece in starea `q1` pentru a incepe sa citeasca. Cand ajunge la inceput, trece in starea `q2`, care este starea de inceput pentru citirea unei noi secvente de caractere. Dupa citirea fiecarui caracter, acesta este retinut intr-o stare unica pentru fiecare combinatie posibila (ex: `..-` = starea `ppl`). Cand masina intalneste caracterul `*` aceasta decodifica starea in litera specifica si trece in starea `SC_Litera` (`SC_A`, `SC_B`, `SC_C`...) si parcurge tot sirul pana intalneste caracterul `=` de la final, unde trece in starea `Litera` (`A`, `B`, `C`, `D`...) care trece peste orice litera scrisa deja si cand gaseste un loc liber, scrie litera pe banda. Dupa scriere, masina trece in starea `q3` care se intoarce la inceputul benzii pentru a sterge secventa descifrata anterior. Dupa ce parcurge sirul, trece in starea `q4` care sterge toate caracterele pana la intalnirea caracterului `*` si trece din nou in starea `q2` pentru a citi urmatoarea secventa.

#### Implementare-Cuvinte Cheie
Dupa ce a tradus sirul de input, masina se pozitioneaza la inceputul traducerii si trece in starea `START_CAUTARE`. Cand gaseste un caracter `H` sau `S`, intra in starea `GH`/`GS` si parcurge in continuare. Daca gaseste `E`, respectiv `O`, trece in `GHE`/`GSO` si tot asa pana gaseste fiecare litera din cuvantul cheie. Daca gaseste caracterul `/`, despartitorul de cuvinte, masina trece inapoi in starea `START_CAUTARE`.

