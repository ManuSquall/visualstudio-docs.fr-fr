---
title: StopTrackingAndCleanup | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- StopTrackingAndCleanup
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7b4a6cca4010284c9a75767710710d28c093c271
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59659954"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Arrête tout le suivi et libère la mémoire utilisée par la session de suivi.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une ([HRESULT]<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) avec le ([réussite]<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) bit défini si le suivi a été arrêté.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** FileTracker.h  
  
## <a name="see-also"></a>Voir aussi  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
