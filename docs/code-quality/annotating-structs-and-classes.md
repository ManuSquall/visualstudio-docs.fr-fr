---
title: Structs et classes d’annotation
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 005cbb77fa0c2bc7c1b788b5076b425a2a8e363e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="annotating-structs-and-classes"></a>Structs et classes d’annotation
Vous pouvez annoter les membres de struct et class à l’aide des annotations qui agissent comme des invariants, elles sont supposées avoir la valeur true à n’importe quel appel de fonction ou d’une entrée/sortie de la fonction qui implique la structure englobante comme paramètre ou une valeur de résultat.

## <a name="struct-and-class-annotations"></a>Les Annotations de classe et de struct

-   `_Field_range_(low, high)`

     Le champ est en cours de la plage (incluse) à partir de `low` à `high`.  Équivalent à `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` appliqué à l’objet annoté en utilisant les conditions pre ou post.

-   `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     Un champ qui a une taille accessible en écriture dans les éléments (ou octets) comme spécifié par `size`.

-   `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`

     Un champ qui a une taille accessible en écriture dans les éléments (ou octets) comme spécifié par `size`et le `count` de ces éléments (octets) qui peuvent être lus.

-   `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     Un champ qui a une taille accessible en lecture et en écriture dans les éléments (ou octets) comme spécifié par `size`.

-   `_Struct_size_bytes_(size)`

     Un champ qui a une taille accessible en lecture et en écriture dans les éléments (ou octets) comme spécifié par `size`.

     S’applique à la déclaration de classe ou de struct.  Indique qu’un objet valide de ce type peut être plus grand que le type déclaré, le nombre d’octets qui est spécifié par `size`.  Par exemple :

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     La taille de mémoire tampon en octets d’un paramètre `pM` de type `MyStruct *` est ensuite dirigé vers l’être :

    ```cpp
    min(pM->nSize, sizeof(MyStruct))
    ```

## <a name="see-also"></a>Voir aussi
 [Utilisation d’Annotations SAL pour réduire les défauts du Code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [présentation de SAL](../code-quality/understanding-sal.md) [annotation de paramètres de fonction et valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md) [annotation du comportement de la fonction](../code-quality/annotating-function-behavior.md) [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md) [spécifiant le moment où une Annotation est applicable et](../code-quality/specifying-when-and-where-an-annotation-applies.md) [des fonctions intrinsèques](../code-quality/intrinsic-functions.md) [meilleures pratiques et Exemples](../code-quality/best-practices-and-examples-sal.md)