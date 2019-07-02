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
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 35be465064c9524eb0e1339794b6a19b7a595da1
ms.sourcegitcommit: d2b234e0a4a875c3cba09321cdf246842670d872
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67493635"
---
# <a name="annotating-structs-and-classes"></a>Structs et classes d'annotation

Vous pouvez annoter des membres de struct et class à l’aide des annotations qui agissent comme des invariants, elles sont supposées avoir la valeur true à n’importe quel appel de fonction ou d’une entrée/sortie de la fonction qui implique la structure englobante comme paramètre ou une valeur de résultat.

## <a name="struct-and-class-annotations"></a>Annotations de classe et de struct

- `_Field_range_(low, high)`

     Le champ est dans la plage (limites incluses) à partir de `low` à `high`.  Équivalent à `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` appliqué à l’objet annoté en utilisant les conditions pre ou post.

- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     Un champ qui a une taille accessible en écriture dans les éléments (ou octets) comme spécifié par `size`.

- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`

     Un champ qui a une taille accessible en écriture dans les éléments (ou octets) comme spécifié par `size`et le `count` de ces éléments (octets) qui sont accessibles en lecture.

- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     Un champ qui a une taille accessible en lecture et en écriture dans les éléments (ou octets) comme spécifié par `size`.

- `_Field_z_`

     Un champ qui a une chaîne se terminant par null.

- `_Struct_size_bytes_(size)`

     S’applique à la déclaration de struct ou une classe.  Indique qu’un objet valide de ce type peut être plus grand que le type déclaré, avec le nombre d’octets qui est spécifié par `size`.  Par exemple :

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     La taille du tampon en octets d’un paramètre `pM` de type `MyStruct *` est alors dirigé vers l’être :

    ```cpp
    min(pM->nSize, sizeof(MyStruct))
    ```

## <a name="example"></a>Exemple

```cpp
#include <sal.h>
// For FIELD_OFFSET macro
#include <windows.h>

// This _Struct_size_bytes_ is equivalent to what below _Field_size_ means.
_Struct_size_bytes_(FIELD_OFFSET(MyBuffer, buffer) + bufferSize * sizeof(int))
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
    int buffer[0];
};
```

Notes de publication pour cet exemple :

- `_Field_z_` équivaut à `_Null_terminated_`.  `_Field_z_` pour le nom de champ spécifie que le champ nom est une chaîne se terminant par null.
- `_Field_range_` pour `bufferSize` Spécifie que la valeur de `bufferSize` ne doit pas dépasser 1 et `MaxBufferSize` (tous deux inclus).
- Le résultat final de la `_Struct_size_bytes_` et `_Field_size_` annotations sont équivalentes. Pour les structures ou classes qui ont une disposition semblable, `_Field_size_` est plus facile à lire et à gérer, car il a moins de références et de calculs que son équivalent `_Struct_size_bytes_` annotation. `_Field_size_` ne nécessite pas la conversion à la taille en octets. Si la taille en octets est la seule option, par exemple, pour un champ de pointeur void, `_Field_size_bytes_` peut être utilisé. Si les deux `_Struct_size_bytes_` et `_Field_size_` existe, les deux seront disponibles aux outils. C’est à l’outil que faire si les deux annotations désaccord.

## <a name="see-also"></a>Voir aussi

- [Utilisation d’annotations SAL pour réduire les défauts du code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Présentation de SAL](../code-quality/understanding-sal.md)
- [Annotation des paramètres de fonction et des valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)
- [Annotation du comportement d’une fonction](../code-quality/annotating-function-behavior.md)
- [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)
- [Spécification du moment et de l’endroit où une annotation s’applique](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)
- [Bonnes pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)