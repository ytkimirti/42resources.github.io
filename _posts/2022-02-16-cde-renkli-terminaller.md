---
layout: post
title:  "C de renkli printfler 🌈 (norminetteyi kızdırmadan)"
author: kımırtı
category: C
---

Aynı `\n` (newline) `\t` (tab) `\0` (C için EOL) gibi, terminalde renkler de ANSI escape kodları ile belirtilir.

Mesela `\e[0;31m` kırmızı rengini `\e[0;36m` mavi rengini temsil eder (en azından C için).

## Nasıl kullanılır?

Herhangi bir özel kodu yazdırdığınızda bir sonraki renk koduna kadar o renk kalır.

```c
int	main(void)
{
	printf("Ben renksizim\n");

	printf("\e[0;31m"); // RED

	printf("Uuuv ben kirmizi\n");

	printf("\e[0;36m"); // BLUE

	printf("Merhaba ben volkan konak\n");
}
```
![ex0](/assets/cde_renkli_terminaller/ex0.png)

Eğer renklerin taşmamasını isterseniz `\e[0m` (reset) kodunu kullanabilirsiniz.

```c
int	main(void)
{
	printf("\e[0;31m"); // RED

	printf("Bu kırmızı\n");

	printf("\e[0m"); // RESET

	printf("Merhaba ben vol...\n");
}
```
![ex1](/assets/cde_renkli_terminaller/ex1.png)


Aynı satırda kullandığınız renkleri resetlemek her zaman iyidir. Hata mesajları ekrana pembe yazılınca ayırt etmek zor oluyor.

```c
printf("\e[0;34m G \e[0;31m o \e[0;33m o \e[0;34m g \e[0;32m l \e[0;31m e \e[0m\n");
```
![Deneme](/assets/cde_renkli_terminaller/google.png)

## Nasıl *güzel* kullanılır

Tamam iyi güzel de böyle kullanmak acı verici. Her seferinde renkleri kopyala yapıştır. Ve de kodu incelerken hangi kodun hangi renk olduğunu göremiyoruz.

Bunun için çok güzel bir çözümümüz var. C nin özelliklerinde biri de derleme sırasında aralarında sadece boşluk olan string sabitlerini birleştirmesi. Mesela

```c
// Derleme öncesi
printf("Hello" " " "World");
```
```c
// Derleme sonrası
printf("Hello World");
```

Bu da demek ki makroları kullanarak çok kullanışlı şeyler yapabiliriz.

Bir stringi cyan yapmak istiyorsak (`"Hello"`) başına ve sonun bu kodları boşluk bırakarak koymamız yeterli (`"\e[0;36m" "Hello" "\e[0m"`).
Ve eğer bu kodları tanımlayan makrolarımız da varsa (mesela `#define CYN "\e[0;36m"`) yerine yazabiliriz (`CYN "Hello" RST`).

```c
#include <stdio.h>

#define RED "\e[0;31m"
#define MAG "\e[0;35m"
#define RST "\e[0m"

int main(void)
{
	printf(RED "Ben kırmızı, " RST "ben beyaz, " MAG "ben de magenta O.O\n" RST);
}
```

