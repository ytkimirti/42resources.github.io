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

## Nasıl *güzel* kullanılır

Aynı satırda kullandığınız renkleri resetlemek her zaman iyidir. Hata mesajları ekrana pembe yazılınca ayırt etmek zor oluyor.

```c
printf("\e[0;34m G \e[0;31m o \e[0;33m o \e[0;34m g \e[0;32m l \e[0;31m e \e[0m\n");
```

![Deneme](assets/cde_renkli_terminaller/google.png)
