---
layout: post
title:  "42 Notlara hoş geldiniz"
author: akarah
category: [Örnek Taslağı]
tag: [örnek taslağı]
---

# Yeni post oluşturma

Yeni post oluşturmak için **\_posts** klasörün içine **YIL-AY-GÜN-başlık.md** şeklinde dosya oluşturmanız gerekiyor.

## Örneğin

```text
2022-02-16-merhaba-dunya.md
```

# Kategori ve Tag ekleme

Postun başına meta bilgi ekleyerek başlık, kategori veya kategoriler, tag veya tagler belirlenebilir. Meta bilgi YAML yazma stilini kullanıyor.

## Dikkatli olun!

Eğer sadece bir kategori eklemek isterseniz **category** opsiyonu kullanınız aksi takdirde **categories** kullandığınız zaman boşluk kategori ayıracı olarak algılanıyor.

```text
---
layout: post
title:  "Merhaba Dunya!"
category: [kategori ismi]
categories: [kategori_ismi1 kategori_ismi2 ...]
tag: [tag ismi]
tags: [tag_ismi1 tag_ismi2 ...]
---

# Hoş Geldiniz

**Merhaba Dunya**, benim ilk postum.

Umarım beğenirsiniz!
```

# Resim ve PDF ekleme

Resim veya PDF eklemek için önce onu **assets** klasörüne yüklemeniz gerekiyor. Sonra yazdığınız postun içine şu şekilde eklemeler yapmanız gerekiyor:

```text
![resim için yorum](/assets/screenshot.jpg)
[benim pdfim](/assets/mydoc.pdf)
```

# Kod ekleme

```c
#include <stdio.h>

int main(int argc, char *argv[]) {
  printf("Merhaba Dunya!\n");
  return 0;
}

// => 'Merhaba Dunya!' STDOUT'a yazdırılıyor.
```

# Referanslar

[Jekyll post dokümantasyonu [EN]][jekyll-docs]

[Markdown Formatı [EN]][md-cheat-sheet]

[jekyll-docs]: https://jekyllrb.com/docs/posts/
[md-cheat-sheet]: https://itopaloglu83.github.io/Jekyll-Markdown-Cheat-Sheet/
