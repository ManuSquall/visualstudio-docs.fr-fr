---
title: Fonctions de raccordement de rapport | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: d3b7916f729f0d1ea1a254ecde8e5c53ea8b8a51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777254"
---
# <a name="report-hook-functions"></a>Fonctions de raccordement de rapport
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une fonction de raccordement de rapport, installée à l’aide [_CrtSetReportHook](http://msdn.microsoft.com/library/1ae7c64f-8c84-4797-9574-b59f00f7a509), est appelée chaque fois [_CrtDbgReport](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) génère un rapport de débogage. Vous pouvez vous en servir, entre autres, pour filtrer les rapports de façon à vous concentrer sur des types d'allocations spécifiques. Une fonction de raccordement de rapport doit avoir un prototype similaire au suivant :  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Le pointeur que vous passez à **_CrtSetReportHook** est de type **_CRT_REPORT_HOOK**, tel que défini dans CRTDBG. H :  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Lorsque la bibliothèque Runtime appelle votre fonction de raccordement, le *nRptType* argument contient la catégorie du rapport (**_CRT_WARN**, **_CRT_ERROR**, ou **_CRT _ASSERT**), *szMsg* contient un pointeur vers une chaîne de message de rapport entièrement assemblé et *retVal* Spécifie si `_CrtDbgReport` doivent poursuivre leur exécution normale Après avoir généré le rapport ou démarrez le débogueur. (Un *retVal* valeur zéro continue l’exécution, la valeur 1 démarre le débogueur.)  
  
 Si le raccordement gère intégralement le message concerné et qu’aucun rapport supplémentaire n’est requis, il doit retourner **TRUE**. Si elle retourne **FALSE**, `_CrtDbgReport` communiquera le message normalement.  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2, exemple](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



