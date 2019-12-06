---
title: Structs et classes d'annotation
ms.date: 06/28/2019
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
- _Field_z_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 70dc130633e9f191811748b2ab316ad339ad4277
ms.sourcegitcommit: 174c992ecdc868ecbf7d3cee654bbc2855aeb67d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74879254"
---
# <a name="annotating-structs-and-classes"></a>Structs et classes d'annotation

Vous pouvez annoter des membres de classe et de struct à l’aide d’annotations qui agissent comme des invariants. elles sont supposées avoir la valeur true lors de n’importe quel appel de fonction ou entrée/sortie de fonction qui implique la structure englobante en tant que paramètre ou valeur de résultat.

## <a name="struct-and-class-annotations"></a>Annotations de struct et de classe

- `_Field_range_(low, high)`

     Le champ se trouve dans la plage (inclusive) de `low` à `high`.  Équivaut à `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` appliquée à l’objet annoté à l’aide des conditions pre ou postales appropriées.

- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     Champ qui a une taille accessible en écriture dans les éléments (ou octets) comme spécifié par `size`.

- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`

     Champ qui a une taille accessible en écriture dans des éléments (ou octets) comme spécifié par `size`, et le `count` de ces éléments (octets) qui sont accessibles en lecture.

- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     Champ qui a à la fois une taille lisible et accessible en écriture dans des éléments (ou octets), comme spécifié par `size`.

- `_Field_z_`

     Champ qui a une chaîne terminée par le caractère null.

- `_Struct_size_bytes_(size)`

     S’applique à une déclaration de classe ou de struct.  Indique qu’un objet valide de ce type peut être plus grand que le type déclaré, avec le nombre d’octets spécifié par `size`.  Par exemple :

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     La taille de la mémoire tampon en octets d’un paramètre `pM` de type `MyStruct *` est ensuite considérée comme :

    ```cpp
    min(pM->nSize, sizeof(MyStruct))
    ```

## <a name="example"></a>Exemple

```cpp
#include <sal.h>

// This _Struct_size_bytes_ is equivalent to what below _Field_size_ means.
_Struct_size_bytes_(__builtin_offsetof(MyBuffer, buffer) + bufferSize * sizeof(int))
struct MyBuffer
{
    static int MaxBufferSize;
    
    _Field_z_
    const char* name;
    
    int firstField;

    // ... other fields

    _Field_range_(1, MaxBufferSize)
    int bufferSize;
    
    _Field_size_(bufferSize)        // Prefered way - easier to read and maintain.
    int buffer[]; // Using C99 Flexible array member
};
```

Remarques pour cet exemple :

- `_Field_z_` équivaut à `_Null_terminated_`.  `_Field_z_` pour le champ nom spécifie que le champ nom est une chaîne terminée par le caractère null.
- `_Field_range_` pour `bufferSize` spécifie que la valeur de `bufferSize` doit être comprise entre 1 et `MaxBufferSize` (les deux incluses).
- Les résultats finaux des annotations d' `_Struct_size_bytes_` et de `_Field_size_` sont équivalents. Pour les structures ou les classes qui ont une disposition similaire, `_Field_size_` est plus facile à lire et à gérer, car il a moins de références et de calculs que l’annotation `_Struct_size_bytes_` équivalente. `_Field_size_` ne nécessite pas de conversion en taille d’octet. Si la taille d’octet est la seule option, par exemple, pour un champ de pointeur void, `_Field_size_bytes_` peut être utilisée. Si `_Struct_size_bytes_` et `_Field_size_` existent, les deux seront disponibles pour les outils. C’est à l’outil qu’il faut faire si les deux annotations ne sont pas en désaccord.

## <a name="see-also"></a>Voir aussi

- [Utilisation d’annotations SAL pour réduire les défauts du code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Présentation de SAL](../code-quality/understanding-sal.md)
- [Annotation des paramètres de fonction et des valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)
- [Annotation du comportement d’une fonction](../code-quality/annotating-function-behavior.md)
- [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)
- [Spécification du moment et de l’endroit où une annotation s’applique](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)
- [Bonnes pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)
