---
title: Annotation de structs et de classes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 6db2202971facb0419db68c04835c8d5c848f528
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77271581"
---
# <a name="annotating-structs-and-classes"></a>Structs et classes d'annotation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez annoter des membres de classe et de struct à l’aide d’annotations qui agissent comme des invariants. elles sont supposées avoir la valeur true lors de n’importe quel appel de fonction ou entrée/sortie de fonction qui implique la structure englobante en tant que paramètre ou valeur de résultat.  
  
## <a name="struct-and-class-annotations"></a>Annotations de struct et de classe  
  
- `_Field_range_(low, high)`  
  
     Le champ se trouve dans la plage (inclusive) de `low` à `high` .  Équivalent à `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` appliqué à l’objet annoté à l’aide des conditions pre ou postales appropriées.  
  
- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     Champ qui a une taille accessible en écriture dans les éléments (ou octets), comme spécifié par `size` .  
  
- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     Champ qui a une taille accessible en écriture dans les éléments (ou octets) comme spécifié par `size` , et le `count` de ces éléments (octets) qui sont accessibles en lecture.  
  
- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     Champ qui a à la fois une taille lisible et accessible en écriture dans des éléments (ou octets), comme spécifié par `size` .  
  
- `_Struct_size_bytes_(size)`  
  
     Champ qui a à la fois une taille lisible et accessible en écriture dans des éléments (ou octets), comme spécifié par `size` .  
  
     S’applique à une déclaration de classe ou de struct.  Indique qu’un objet valide de ce type peut être plus grand que le type déclaré, avec le nombre d’octets spécifié par `size` .  Par exemple :  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     La taille de la mémoire tampon en octets d’un paramètre `pM` de type `MyStruct *` est ensuite considérée comme :  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’annotations SAL pour réduire les défauts du code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Comprendre SAL](../code-quality/understanding-sal.md)   
 [Annotation des paramètres de fonction et des valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotation du comportement d’une fonction](../code-quality/annotating-function-behavior.md)   
 [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)   
 [Spécification du moment et de l’endroit où une annotation s’applique](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)   
 [Bonnes pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)
