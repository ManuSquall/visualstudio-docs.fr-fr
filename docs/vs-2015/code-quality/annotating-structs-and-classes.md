---
title: Annoter les Classes et Structs | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 965a823c658516edf247f6a99d23d189097b31f0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801471"
---
# <a name="annotating-structs-and-classes"></a>Structs et classes d’annotation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez annoter des membres de struct et class à l’aide des annotations qui agissent comme des invariants, elles sont supposées avoir la valeur true à n’importe quel appel de fonction ou d’une entrée/sortie de la fonction qui implique la structure englobante comme paramètre ou une valeur de résultat.  
  
## <a name="struct-and-class-annotations"></a>Annotations de classe et de struct  
  
-   `_Field_range_(low, high)`  
  
     Le champ est dans la plage (limites incluses) à partir de `low` à `high`.  Équivalent à `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` appliqué à l’objet annoté en utilisant les conditions pre ou post.  
  
-   `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     Un champ qui a une taille accessible en écriture dans les éléments (ou octets) comme spécifié par `size`.  
  
-   `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     Un champ qui a une taille accessible en écriture dans les éléments (ou octets) comme spécifié par `size`et le `count` de ces éléments (octets) qui sont accessibles en lecture.  
  
-   `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     Un champ qui a une taille accessible en lecture et en écriture dans les éléments (ou octets) comme spécifié par `size`.  
  
-   `_Struct_size_bytes_(size)`  
  
     Un champ qui a une taille accessible en lecture et en écriture dans les éléments (ou octets) comme spécifié par `size`.  
  
     S’applique à la déclaration de struct ou une classe.  Indique qu’un objet valide de ce type peut être plus grand que le type déclaré, avec le nombre d’octets qui est spécifié par `size`.  Exemple :  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     La taille du tampon en octets d’un paramètre `pM` de type `MyStruct *` est alors dirigé vers l’être :  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’Annotations SAL pour réduire les défauts du Code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Présentation de SAL](../code-quality/understanding-sal.md)   
 [Annotation des paramètres de fonction et valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotation du comportement de la fonction](../code-quality/annotating-function-behavior.md)   
 [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)   
 [Spécifiant le moment où une Annotation est applicable et](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)   
 [Bonnes pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)



