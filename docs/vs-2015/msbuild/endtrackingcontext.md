---
title: EndTrackingContext | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- EndTrackingContext
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43c871099370b1a3b94ff855f4ee4834b9627d20
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306577"
---
# <a name="endtrackingcontext"></a>EndTrackingContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Mettez fin au contexte de suivi actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT WINAPI EndTrackingContext();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) avec la [réussite] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) bit défini si le contexte de suivi a été interrompue.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** FileTracker.h  
  
## <a name="see-also"></a>Voir aussi  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)



