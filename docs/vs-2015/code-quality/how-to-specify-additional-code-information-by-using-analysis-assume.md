---
title: 'Comment : spécifier des informations de code supplémentaires à l’aide de __analysis_assume | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: f2f18c9284ec96de7a7b8663aff485962d194282
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277975"
---
# <a name="how-to-specify-additional-code-information-by-using-__analysis_assume"></a>Comment : spécifier des informations de code supplémentaire en utilisant __analysis_assume
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez fournir des indications à l’outil d’analyse du code pour le code C/C++ qui aide le processus d’analyse et à réduire les avertissements. Pour fournir des informations supplémentaires, utilisez la fonction suivante :  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` -toute expression supposée avoir la valeur true.  
  
 L’outil d’analyse du code suppose que la condition représentée par l’expression est vraie au point où la fonction apparaît et reste true jusqu’à ce que l’expression soit modifiée, par exemple, en l’assignant à une variable.  
  
> [!NOTE]
> `__analysis_assume` n’a pas d’impact sur l’optimisation du code. En dehors de l’outil d’analyse du code, `__analysis_assume` est défini comme une absence d’opération.  
  
## <a name="example"></a>Exemple  
 Le code suivant utilise `__analysis_assume` pour corriger l’avertissement d’analyse du code [C6388](../code-quality/c6388.md):  
  
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
  __analysis_assume(pc == NULL);   
  f(pc);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [__assume](https://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)
