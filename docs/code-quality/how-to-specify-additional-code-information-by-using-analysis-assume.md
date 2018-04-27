---
title: 'Comment : spécifier des informations de Code supplémentaire à l’aide de _Analysis_assume'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: ce8102bbc790019490c4dc2a2ccbfab7d8c33981
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Comment : spécifier des informations de Code supplémentaire à l’aide de _Analysis_assume
Vous pouvez fournir des indications à l’outil d’analyse de code pour le code C/C++ qui aideront le processus d’analyse et réduire les avertissements. Pour fournir des informations supplémentaires, utilisez la fonction suivante :

 `_Analysis_assume(`  `expr`  `)`

 `expr` -toute expression supposée être évaluée à true.

 L’outil d’analyse de code suppose que la condition représentée par l’expression a la valeur true au point où la fonction s’affiche et le reste jusqu'à ce que l’expression est modifiée, par exemple, par assignation à une variable.

> [!NOTE]
>  `_Analysis_assume` ne pas avoir un impact sur l’optimisation du code. À l’extérieur de l’outil d’analyse de code, `_Analysis_assume` est défini comme une absence d’opération.

## <a name="example"></a>Exemple
 Le code suivant utilise `_Analysis_assume` pour corriger l’avertissement d’analyse du code [C6388](../code-quality/c6388.md):

```
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
 [__assume](/cpp/intrinsics/assume)