---
title: Utiliser _Analysis_assume pour les indicateurs d’analyse du code
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 186ea6ac58736098720d60c644c30801073b7453
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018722"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume"></a>Procédure : Spécifier des informations de code supplémentaire en utilisant _Analysis_assume

Vous pouvez fournir des indications sur l’outil d’analyse du code pourC++ C/code qui aide le processus d’analyse et réduire les avertissements. Pour fournir des informations supplémentaires, utilisez la fonction suivante :

`_Analysis_assume(`  `expr`  `)`

`expr`-toute expression supposée avoir la valeur true.

L’outil d’analyse du code suppose que la condition représentée par l’expression est vraie au point où la fonction apparaît et reste true jusqu’à ce que l’expression soit modifiée, par exemple, en l’assignant à une variable.

> [!NOTE]
> `_Analysis_assume` n’a pas d’impact sur l’optimisation du code. En dehors de l’outil d’analyse du code, `_Analysis_assume` est défini comme une absence d’opération.

## <a name="example"></a>Exemple

Le code suivant utilise `_Analysis_assume` pour corriger l’avertissement d’analyse du code [C6388](../code-quality/c6388.md):

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    __analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>Voir aussi

- [__assume](/cpp/intrinsics/assume)
