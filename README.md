# Perfume árabe en datos

160 perfumes árabes de 15 casas, con la pirámide olfativa de cada uno leída en Fragrantica ficha a ficha. Sin descripciones de mayorista: solo notas, acordes y de dónde sale cada dato.

*English: note pyramids of 160 Arab perfumes (Lattafa, Armaf, Afnan, Rasasi, Ajmal, Al Haramain, Khadlaj, French Avenue, Orientica and others), each one checked by hand against its Fragrantica page. `piramides.csv` is the per-perfume table, `datos.json` holds the aggregates. CC BY 4.0. The method is described below in Spanish; the column names are self-explanatory.*

Los mismos números, comentados, están en [privateriche.com/perfume-arabe-en-cifras](https://privateriche.com/perfume-arabe-en-cifras). Si citas una cifra, enlaza a esa página o a este repositorio.

## Ficheros

| Fichero | Qué es |
|---|---|
| `piramides.csv` | Una fila por perfume: marca, nombre, género, concentración, notas de salida, corazón y fondo, acordes, y la URL de Fragrantica de donde se leyó. Las listas van separadas por ` \| `. |
| `piramides.json` | Lo mismo, con las notas como arrays. |
| `datos.json` | Los agregados: notas más repetidas, en qué nivel vive cada una, acordes, firma de cada casa, pares de perfumes con las mismas notas, parecido con originales de diseñador, precios por 100 ml de nuestro catálogo y valoraciones. |

Fecha de las pirámides: 2026-09-17 (primera versión 2026-09-07, con 152 perfumes). Fecha de los agregados: 2026-09-17. Cambios de la segunda versión: 8 perfumes nuevos (Fakhar Silver y Platin, Bade'e Al Oud Noble Blush, Art of Universe, Art of Arabia I, Yum Yum, Island Bliss, Bon Bon) y la ficha `lattafa-fakhar` corregida: es Fakhar Gold (Fragrantica 128690), no Fakhar Lattafa 2015; la primera versión llevaba la pirámide equivocada.

## Cómo se hizo

Cada perfume tiene su ficha en fragrantica.es. La URL de cada una está en la columna `fragrantica_url`, y se emparejó mirando el frasco, no el nombre: las casas árabes venden variantes con nombres casi idénticos (Kashmir y Kashmir Musk, Daarej pour Homme y pour Femme) y emparejar por texto ya nos costó fichas mezcladas.

De cada página se leyeron dos cosas distintas:

- Las **notas**, del bloque de pirámide (salida, corazón, fondo). 150 perfumes tienen pirámide. 8 no la tienen en Fragrantica, solo una lista plana, y así se marcan (`tiene_piramide = 0`); en esos la lista está en `notas` y los tres niveles van vacíos. 2 no tienen ninguna nota publicada.
- Los **acordes**, del bloque de acordes de la página, con su orden. No de la infografía: esa recorta a cinco y a veces se salta alguno.

Los nombres de las notas son los de Fragrantica en español, sin normalizar (por eso hay «limón (lima ácida)» o «frangipani (plumeria, plumaria, atapaima)»). Quien quiera agruparlas tiene el vocabulario completo en las propias filas.

El parecido entre dos perfumes es el índice de Jaccard sobre el conjunto de notas: notas en común dividido por notas distintas entre los dos. Cuenta si una nota está, no cuánta hay ni en qué nivel.

## Lo que sale de contar

- Almizcle aparece en el 52 % de las pirámides. Vainilla y ámbar, en el 41 %. Bergamota, 37 %; pachulí, 35 %; jazmín, 34 %.
- Bergamota, limón y mandarina están en salida el 100 % de las veces que aparecen. Ambroxán, en fondo el 100 %. Almizcle, en fondo el 95 %.
- Amaderado es acorde en el 70 % de las fichas. Dulce, 62 %. Atalcado, 61 %; ámbar, 60 %.
- Club de Nuit Untold (Armaf) y Amber Rouge (Orientica) declaran exactamente las mismas seis notas. Oud For Glory (Lattafa) tiene las seis de Oud for Greatness (Initio). Supremacy Silver (Afnan) y Club de Nuit Intense Man (Armaf), los dos clones de Aventus más vendidos, comparten 10 notas entre ellos.
- Contra los originales, el parecido baja: el mejor clon de Bleu de Chanel comparte 12 de 15 notas; el de Aventus, 9 de 13; el de Sauvage, 4 de 12.
- Cada casa repite algo: Khadlaj pone neroli 5,6 veces más de lo que le tocaría por su tamaño; Afnan, manzana 3,7; French Avenue, madera de gaiac 3,5.

## Lo que esto no demuestra

Una pirámide es lo que la marca declara, no lo que hay en el frasco ni en qué cantidad. Dos perfumes con las mismas notas pueden oler distinto. Los precios de `datos.json` son los de nuestro catálogo, no una media del mercado. Y la muestra son nuestros 160 frascos, no el perfume árabe entero.

## Licencia y cita

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.es). Puedes usar, copiar y transformar los datos, también con fines comerciales, citando la fuente:

> Private Riche (2026). *Perfume árabe en datos*. https://privateriche.com/perfume-arabe-en-cifras

Las notas y acordes se leyeron en [fragrantica.es](https://www.fragrantica.es); la URL de cada ficha está en los datos.

Dudas sobre el método: hola@privateriche.com.
