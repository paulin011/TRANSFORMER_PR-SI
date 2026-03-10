---
marp: true
theme: default
paginate: true
footer: ' Institut für Informatik  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 10.3.2026'
style: |
  @import url('https://fonts.googleapis.com/css2?family=Arial:wght@400;700&display=swap');
  section {
    font-family: Arial, sans-serif;
    font-size: 18pt;
    padding-bottom: 3.5rem;
  }
  h1 {
    font-size: 28pt;
    font-weight: bold;
  }
  h2 {
    font-size: 22pt;
    font-weight: bold;
  }
  h3 {
    font-size: 20pt;
    font-weight: bold;
  }
  table {
    font-size: 16pt;
  }
  .highlight {
    color: #00496A;
  }
  .alert {
    color: #cc0000;
  }
  /* Footer with logo */
  section::before {
    content: "";
    position: absolute;
    bottom: 0.3rem;
    left: 3.5rem;
    width: 6rem;
    height: 2.5rem;
    background-image: url("uni-koeln-logo.png");
    background-size: contain;
    background-repeat: no-repeat;
    background-position: left;
    z-index: 1;
  }
  /* Footer text styling */
  footer {
    position: absolute;
    left: 11rem;
    bottom: 1rem;
    font-size: 10pt;
    color: #00496A;
  }
  /* Adjust pagination position to right side */
  section::after {
    position: absolute;
    bottom: 2rem;
    right: 2rem;
    font-size: 10pt;
    color: #00496A;
    content: attr(data-marpit-pagination);
    font-weight: bold;
    
  }

---

<!-- _paginate: "" -->
# Transformer



**Referent:** Paulin Saher
**Datum:** 31.1.2026

---

# Inhalt

- Beispiel Gpt3 basierend auf 3Blue1Brown
- Übersicht 



---

Disclaimer

Wörter != Tokens

Wörter einfacher für Menschen deswegen hier austauschbar für besseres Verständnis

![](https://dataplatform.cloud.ibm.com/docs/api/content/wsj/analyze-data/images/fm-tokenization.png?context=wx&locale=de)
Quelle: https://dataplatform.cloud.ibm.com/docs/api/content/wsj/analyze-data/images/fm-tokenization.png?context=wx&locale=de


---


# Grundidee
1. Wörter -> Embedding -> Vektor
2. Gesamten Input verstehen -> Attention
3. Neues Wort als Vektor Generieren -> Attention
4. Neues Wort Generieren -> Unembedding


---


<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](Screenshot_05-Mär_11-46-02_org.kde.haruna.png)








---



<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](Screenshot_05-Mär_11-47-18_383.png)




---

# 1. Embedding
GPT3 50,257 Einzigartige Tokens
Tokens representiert als 12.288 Dimensionale Vektoren


![height:400](Screenshot_05-Mär_11-48-52_9885.png)

---

# 1.1 Grundidee Embedding Matrix
Bedeutung Mathematisch darstellen

---


<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](Screenshot_05-Mär_11-49-27_16135.png) 

---

<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](Screenshot_05-Mär_11-49-41_20720.png)

---

<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](Screenshot_05-Mär_11-51-32_3377.png)

---

# 1.2 Ziel von Embedding
Durch Rechnungen Kontext verstehen und enkodieren.

---

<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](Screenshot_05-Mär_11-54-34_19266.png)

---

# 2 Attention
Embedding erklärt das Wort aber Kontext fehlt
Kontext kommt von andern Wörtern

---

<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](Screenshot_05-Mär_12-38-32_205.png)

---

<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](Screenshot_05-Mär_12-43-47_30492.png)

---

# 2.1 Wie Effizient Kontext suchen und Einbetten

Wichtigkeit von Wörtern für den Kontext ist sehr verschieden

Beispiel: das Eis oder ein Eis -> wenig Bedeutung
geschmolzenes Eis oder leckeres Eis -> viel Bedeutung
### Queries 

Suche für bestimmte Attribute zum Beschreiben des Wortes
Beispiel: Token ist ein Nomen und sucht Adjektive dann Vektor des Tokens * Query = Suche Adjektive vor dem Token

---

<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](Screenshot_05-Mär_12-50-38_9257.png)

---

# Keys

Identifikation von attributen (z.b. Adjektiv)
Token * Key = Ich bin ein Adjektiv

---

<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](Screenshot_05-Mär_12-54-22_32272.png)

---

<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](Screenshot_05-Mär_12-56-04_28055.png)

---

# Verbinden von Query und Key
Skalarprodukt wird gebildet durch softmax gereinigt

---

<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](Screenshot_05-Mär_13-00-48_13577.png)

---

<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](Screenshot_05-Mär_13-02-21_31382.png)

---


<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](Screenshot_05-Mär_13-03-22_30634.png)

---

# 3 Attention is all you need
Basierend auf wichtigkeit für jeweilige Tokens den Kontext von jedem Token aktualisieren

---
<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>
![bg](Screenshot_05-Mär_13-17-35_11510.png)

---
<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](Screenshot_05-Mär_13-18-23_15345.png)

---

# 3.1 96x Hält besser
- 96 * Key Matritzen
96 * Query Matritzen
96 * Value Matritzen

- Alle Jeder Attention Block Gleichzeitig
Durchschnitt von allen 96 Attention Blocks -> Token Update

- Mehrere Interpretationen lernen

---
<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](image-2.png)


---

# Multi-Layer-Perceptron
Attention is wichtig aber nur 1/3 der Größe des Modells.

Die Wissensdatenbank (Multi-Layer-Perceptron) des Modells sind die restlichen 2/3

Klassisches Neural Network mit
Input - hidden - output Schichten

Beispiel Michal Jordan plays the sport of ______

Kommt die Ausgabe Basketball (!nicht im vorherigen Kontext)

---

<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>
 
![bg](image-3.png)

---

# 3.1 Funktionsweise 
Jede Zeile Fragt im prinzip eine Frage z.b. 
- ist es in Englisch
- ist es source code
- ist Land in der EU
- ist ein Basketballer
- Kodiert der Vektor Michal Jordan?

---


<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](Screenshot_05-Mär_13-48-19_4595.png)

---

<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>

![bg](Screenshot_05-Mär_13-47-38_22871.png)

---

<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>


![bg](image-4.png)

---
# Unembedding

---

![bg](Screenshot_05-Mär_12-01-32_4100.png)

<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>


---


<style scoped>
section::before { display: none; }
footer { display: none; }
section::after { display: none; }
</style>


![bg](Screenshot_05-Mär_12-01-47_8353.png)

---
# Vielen Dank für Ihre Aufmerksamkeit!

**Noch Fragen oder Anmerkungen?**

---
# Quellen 
- https://youtu.be/KpKog-L9veg -- Softmax erklärung
- https://youtu.be/9-Jl0dxWQs8 -- MLP 3Blue1Brown
- https://youtu.be/eMlx5fFNoYc -- Attention 3Blue1Brown
- https://youtu.be/wjZofJX0v4M -- Transformer Overview 3Blue1Brown
