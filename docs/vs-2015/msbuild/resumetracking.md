---
title: ResumeTracking | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- ResumeTracking
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2328b318c00b214138cf70e505c1988f8f1afc6a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54802200"
---
# <a name="resumetracking"></a>ResumeTracking
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Reprend le suivi dans le contexte actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 [HRESULT](<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) avec le bit [SUCCEEDED](<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) défini si le suivi a été repris. E_FAIL (<!-- TODO: review code entity reference <xref:assetId:///E_FAIL?qualifyHint=False&amp;autoUpgrade=True>  -->) est retourné si le suivi ne peut pas être repris, car le contexte n’était pas disponible.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** FileTracker.h  
  
## <a name="see-also"></a>Voir aussi  
 [SuspendTracking](../msbuild/suspendtracking.md)
