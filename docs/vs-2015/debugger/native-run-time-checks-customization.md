---
title: Personnalisation des vérifications natives à l’exécution | Microsoft Docs
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
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 396778e87732d73462a7ecc2a420ea22a00936b1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856598"
---
# <a name="native-run-time-checks-customization"></a>Personnalisation des contrôles natifs à l'exécution
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous compilez avec **/RTC** (contrôles d’exécution) ou utilisez le `runtime_checks` pragma, la bibliothèque Runtime C fournit les contrôles natifs à l’exécution. Dans certains cas, il est utile de personnaliser le contrôle à l'exécution :  
  
- Pour acheminer des messages de contrôle à l'exécution vers d'autres emplacements que le fichier ou la destination par défaut.  
  
- Pour spécifier une destination de sortie en cas de messages de contrôle à l'exécution venant d'un débogueur tiers.  
  
- Pour rapporter des messages de contrôle à l’exécution en provenance d’un programme compilé avec une version Release de la bibliothèque Runtime C. Les versions finales de la bibliothèque n’utilisent pas `_CrtDbgReportW` pour rapporter les erreurs d’exécution. Au lieu de cela, ils affichent une **Assert** boîte de dialogue pour chaque erreur d’exécution.  
  
  Pour personnaliser le contrôle des erreurs d'exécution, vous pouvez :  
  
- Écrire une fonction permettant d'obtenir un rapport sur les erreurs d'exécution. Pour plus d’informations, consultez [Comment : écrire une fonction de création de rapports exécution erreur](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
- Personnaliser la destination des messages d'erreur.  
  
- Demander des informations sur les erreurs de contrôle à l'exécution.  
  
## <a name="customize-the-error-message-destination"></a>Personnaliser la destination des messages d'erreur  
 Si vous utilisez `_CrtDbgReportW` pour rapporter des erreurs, vous pouvez utiliser `_CrtSetReportMode` pour spécifier la destination des messages d'erreur.  
  
 Si vous utilisez une fonction personnalisée pour obtenir vos rapports, associez une erreur à un type de rapport à l'aide de `_RTC_SetErrorType`.  
  
## <a name="query-for-information-about-run-time-checks"></a>Demander des informations sur les contrôles à l'exécution  
 `_RTC_NumErrors` retourne le nombre de types d'erreurs détectés par les vérifications des erreurs au moment de l'exécution. Pour obtenir une brève description de chaque erreur, faites une boucle allant de 0 à la valeur de retour `_RTC_NumErrors`, en transmettant, à chaque boucle, la valeur de l'itération à `_RTC_GetErrDesc`. Pour plus d’informations, consultez [_RTC_NumErrors](http://msdn.microsoft.com/library/7e82adae-38e2-4f8b-bc0b-37bda8109fd1) et [_RTC_GetErrDesc](http://msdn.microsoft.com/library/7994ec2b-5488-4fd4-806d-a166c9a9f927).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : utiliser des contrôles d’exécution natifs](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [_CrtDbgReport, _CrtDbgReportW](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc)





