
# Projekat: Koalicione igre u mikro-mreži (PV + baterije)

## 1. Opis problema

U ovom projektu razmatra se **mikro-mreža domaćinstava** koja mogu imati:

- sopstvenu potrošnju energije
- fotonaponsku (PV) proizvodnju
- baterijski sistem za skladištenje energije

Domaćinstva mogu:

1. raditi **samostalno** (svako optimizuje svoju energiju),
2. formirati **koaliciju** i deliti energiju (pooling).

Cilj projekta je da se primenom **koalicione teorije igara** odredi:

- kolika je korist od saradnje,
- kako se ta korist **pravedno raspodeljuje** među članovima koalicije.

---

# 2. Matematički model

## 2.1 Solo optimizacija (jedno domaćinstvo)

Svako domaćinstvo rešava problem minimizacije troška kupovine energije iz mreže.

Trošak:

C_i = sum_t ( c_buy(t) * Import_i(t) - c_sell(t) * Export_i(t) )

uz ograničenje bilansa energije:

Import_i(t) + G_i(t) + Dis_i(t) = L_i(t) + Ch_i(t) + Export_i(t)

gde su:

- L_i(t) – potrošnja
- G_i(t) – PV proizvodnja
- Ch_i(t) – punjenje baterije
- Dis_i(t) – pražnjenje baterije
- Import / Export – razmena sa mrežom

Dinamika baterije:

SOC(t+1) = SOC(t) + eta_ch * Ch(t) - Dis(t) / eta_dis

---

# 3. Koalicioni model (pooling)

Ako grupa domaćinstava formira koaliciju S:

- PV viškovi jednog člana mogu pokriti deficit drugog
- mreža vidi samo **agregirani neto tok energije**

Koalicioni trošak:

C_S = min sum_t ( c_buy(t) * Import_S(t) - c_sell(t) * Export_S(t) )

bilans:

Import_S(t) - Export_S(t)
= sum_i ( L_i(t) - G_i(t) + Ch_i(t) - Dis_i(t) )

---

# 4. Karakteristična funkcija igre

Koalicija ima vrednost jednaku **uštedi koju ostvaruje saradnjom**.

v(S) = sum_{i in S} C_i^solo - C_S^coal

gde su:

- C_i^solo – trošak kada domaćinstvo radi samo
- C_S^coal – trošak kada rade zajedno

Ako je:

v(S) > 0

onda saradnja donosi ekonomsku korist.

---

# 5. Rešavanje optimizacionih problema

Solo i koalicioni problemi se rešavaju kao **linearni programi (LP)**.

Koristi se biblioteka:

scipy.optimize.linprog

Varijable u modelu:

- Import
- Export
- Charge
- Discharge
- SOC

LP rešava optimalan raspored energije kroz 24 sata.

---

# 6. Generisanje podataka

U demonstraciji se koriste **sintetički profili**:

### Potrošnja

modelovana kao:

- jutarnji pik
- večernji pik

### PV proizvodnja

modelovana gausovom krivom oko podne.

### Tarife

Time-of-use (TOU):

- jutarnji pik
- večernji pik
- niža cena noću

---

# 7. Formiranje koalicionih vrednosti

Za sve podskupove igrača računa se:

1. koalicioni trošak
2. zbir solo troškova

zatim:

v(S)

Ovo formira **koalicionu igru sa prenosivom korisnošću (TU game)**.

---

# 8. Shapley vrednost

Shapley raspodela predstavlja **pravednu raspodelu uštede**.

Definiše se kao očekivani marginalni doprinos igrača kroz sve permutacije.

phi_i = sum_{S subset N\{i}} |S|!(n-|S|-1)! / n! * ( v(S U {i}) - v(S) )

Implementacija koristi enumeraciju svih permutacija igrača.

Rezultat:

x_i = Shapley raspodela za svakog igrača

i važi:

sum_i x_i = v(N)

---

# 9. Core stabilnost

Koalicija je stabilna ako nijedna podkoalicija nema motiv da se odvoji.

Core uslov:

sum_{i in S} x_i >= v(S)

Ako ovaj uslov nije zadovoljen, koalicija S može blokirati raspodelu.

U kodu se proveravaju sve koalicije i traže **blokirajuće koalicije**.

---

# 10. Least Core

Ako je core prazan, koristi se **least-core** koncept.

Traži se minimalno ε takvo da:

sum_{i in S} x_i >= v(S) - ε

za sve koalicije.

Ovo se rešava kao LP:

min ε

uz ograničenja:

sum_i x_i = v(N)

i gore navedeni uslov za sve S.

ε predstavlja **najmanju moguću nestabilnost** sistema.

---

# 11. Vizualizacije

Notebook prikazuje:

### 1. profile cena

cbuy(t), csell(t)

### 2. profile potrošnje

L_i(t)

### 3. profile PV proizvodnje

G_i(t)

### 4. vrednosti koalicija

v(S)

### 5. raspodelu dobiti

- Shapley raspodela
- Least-core raspodela

grafički prikaz bar grafikom.

---

# 12. Šta rezultati pokazuju

Analiza omogućava:

- procenu koristi od **energetske saradnje**
- identifikaciju **najvažnijih igrača**
- proveru **stabilnosti koalicije**
- poređenje različitih raspodela dobiti

---

# 13. Moguća proširenja projekta

Projekat se može proširiti:

- realnim profilima potrošnje
- većim brojem kuća
- različitim baterijskim kapacitetima
- mrežnim ograničenjima
- Monte Carlo analizom

---

# 14. Zaključak

Koaliciona teorija igara pruža snažan alat za analizu **energetskih zajednica**.

Model omogućava:

- kvantifikaciju koristi saradnje
- pravednu raspodelu dobiti
- analizu stabilnosti koalicija

što je ključno za buduće **lokalne energetske zajednice i mikro-mreže**.
