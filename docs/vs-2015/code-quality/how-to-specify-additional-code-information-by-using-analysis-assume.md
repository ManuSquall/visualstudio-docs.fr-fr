---
title: 'Procédure : Spécifier les informations de Code supplémentaire en utilisant __analysis_assume | Microsoft Docs'
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
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: e130f2248ae6715b3248226c780bc162e1ff01ef
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63426641"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Procédure : Spécifier des informations de code supplémentaire en utilisant __analysis_assume
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez fournir des indications à l’outil d’analyse de code pour le code C/C++ qui aideront le processus d’analyse et réduire les avertissements. Pour fournir des informations supplémentaires, utilisez la fonction suivante :  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` -toute expression qui est supposée être évaluée à true.  
  
 L’outil d’analyse de code suppose que la condition représentée par l’expression est remplie au point où la fonction s’affiche et le reste jusqu'à ce que l’expression est modifiée, par exemple, par assignation à une variable.  
  
> [!NOTE]
> `__analysis_assume` ne pas avoir un impact sur l’optimisation du code. En dehors de l’outil d’analyse de code, `__analysis_assume` est défini comme une absence d’opération.  
  
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
 [__assume](http://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)
