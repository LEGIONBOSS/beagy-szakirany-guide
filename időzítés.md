# Időzítés

Tegyük fel hogy van egy metódusunk, ami valami fontos műveletet végez.

```arduino
void myFunction()
{
    // valami fontos művelet
    Serial.println("Valami fontos művelet elvégezve!");
}
```

Tegyük fel azt is, hogy ezt a műveletet mondjuk 1 másodpercenként el szeretnénk sütni.

Ennek a megvalósítására három elterjedtebb módszer (professzionalitás szempontjából növekvő sorrendben) létezik, melyek:

1. A `delay` módszer
2. A `millis` módszer
3. Az `interrupt` módszer

---
## A `delay` módszer

Az Arduino keretrendszer beépített metódusai a `delay()` és a `delayMicroseconds()`, amelyek arra valóak, hogy a program futását megállítsuk egy adott mennyiségű mili- vagy mikroszekundum erejéig.

```arduino
void loop()
{
    delay(1000); // 1 másodperc szünet
    myFunction(); // metódus hívás
}
```

Ennek a módszernek a nagy hátránya, hogy a `delay` által előírt szünet kötött hosszúságú, és nem lehet közben semmi mást csinálni.

Képzeljünk el egy olyan esetet, ahhol két metódusunk van, az egyiket **fél**, a másikat **egy** másodpercenként szeretnénk elsütni. Megpróbálhatnánk ezt az alábbi módon megoldani:

```arduino
void loop()
{
    delay(500); // 0,5 másodperc szünet
    myFunction1(); // egyik metódus
    delay(500); // 0,5 másodperc szünet
    myFunction1(); // egyik metódus
    myFunction2(); // másik metódus
}
```

Ez elsőre jónak tűnik, és ilyen kis példa esetén még használható is.

![](img/delay1.png)

De van ezzel két probléma is.

1. Ha nem két metódusunk van, hanem mondjuk 10, mind külömböző idő értékekkel, eléggé kényelmetlenné válik a `delay`-ek kiszámolgatása.

2. Ha figyelembe vesszük az egyes metódusok lefutási idejét (amit eddig figyelmen kívül hagytunk), akkor észrevehetjük, hogy a metódushívások között több idő telik el, mint szeretnénk.

![](img/delay2.png)

---
## A `millis` módszer

---
## Az `interrupt` módszer

---
## Hivatkozások

Arduino `delay()` - https://www.arduino.cc/reference/en/language/functions/time/delay/

Arduino `delayMicroseconds()` - https://www.arduino.cc/reference/en/language/functions/time/delaymicroseconds/

Arduino `millis()` - https://www.arduino.cc/reference/en/language/functions/time/millis/

Arduino `micros()` - https://www.arduino.cc/reference/en/language/functions/time/micros/