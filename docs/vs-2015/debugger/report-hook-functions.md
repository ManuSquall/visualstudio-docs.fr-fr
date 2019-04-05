---
title: Fonctions de raccordement de rapport | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 38d553abd50d1b5870adc31e08d349f9f84c0579
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951695"
---
# <a name="report-hook-functions"></a>Fonctions de raccordement de rapport
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une fonction de raccordement de rapport, installée avec [_CrtSetReportHook](http://msdn.microsoft.com/library/1ae7c64f-8c84-4797-9574-b59f00f7a509), est appelée chaque fois que [_CrtDbgReport](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) génère un rapport de débogage. Vous pouvez vous en servir, entre autres, pour filtrer les rapports de façon à vous concentrer sur des types d'allocations spécifiques. Une fonction de raccordement de rapport doit avoir un prototype similaire au suivant :  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Le pointeur que vous passez à **_CrtSetReportHook** est de type **_CRT_REPORT_HOOK**, tel que défini dans CRTDBG. H :  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Quand la bibliothèque Runtime appelle votre fonction de raccordement, l’argument *nRptType* contient la catégorie du rapport (**_CRT_WARN**, **_CRT_ERROR**, or **_CRT_ASSERT**), *szMsg* contient un pointeur vers une chaîne de message de rapport entièrement assemblé, et *retVal* spécifie si `_CrtDbgReport` doit poursuivre normalement son exécution après avoir généré le rapport ou bien démarrer le débogueur. (Si la valeur de *retVal* est zéro, l’exécution se poursuit ; si cette valeur est 1, le débogueur est démarré.)  
  
 Si le raccordement gère intégralement le message concerné et qu’aucun rapport supplémentaire n’est requis, il devrait retourner la valeur **TRUE**. S’il retourne **FALSE**, `_CrtDbgReport` communique le message de façon normale.  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2, exemple](http://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
