---
title: Utiliser _Analysis_assume pour indications d’analyse de code
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: f23dd3821744687d4f595ad404bc076e1d05af7b
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835920"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Procédure : Spécifier des informations de code supplémentaire en utilisant _Analysis_assume

Vous pouvez fournir des indications à l’outil d’analyse de code pour le code C/C++ qui aideront le processus d’analyse et réduire les avertissements. Pour fournir des informations supplémentaires, utilisez la fonction suivante :

`_Analysis_assume(`  `expr`  `)`

`expr` -toute expression qui est supposée être évaluée à true.

L’outil d’analyse de code suppose que la condition représentée par l’expression est remplie au point où la fonction s’affiche et le reste jusqu'à ce que l’expression est modifiée, par exemple, par assignation à une variable.

> [!NOTE]
> `_Analysis_assume` ne pas avoir un impact sur l’optimisation du code. En dehors de l’outil d’analyse de code, `_Analysis_assume` est défini comme une absence d’opération.

## <a name="example"></a>Exemple

Le code suivant utilise `_Analysis_assume` pour corriger l’avertissement d’analyse du code [C6388](../code-quality/c6388.md):

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

// calls free and sets ch to null
void FreeAndNull(char* ch);

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

void test( )
{
  char *pc = (char*)malloc(5);
  FreeAndNull(pc);
  _Analysis_assume(pc == NULL);
  f(pc);
}
```

## <a name="see-also"></a>Voir aussi

- [__assume](/cpp/intrinsics/assume)
