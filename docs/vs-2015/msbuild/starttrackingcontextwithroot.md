---
title: StartTrackingContextWithRoot | Microsoft Docs
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
- StartTrackingContextWithRoot
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f93a82aea513eec6417b61c009ec239989f2d0c0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269700"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Démarre un contexte de suivi en utilisant un fichier réponse spécifiant un marqueur racine.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `intermediateDirectory`  
 Répertoire où stocker le journal de suivi.  
  
 [in] `taskName`  
 Identifie le contexte de suivi. Ce nom est utilisé pour créer le nom du fichier journal.  
  
 [in] `rootMarkerResponseFile`  
 Chemin d’un fichier réponse contenant un marqueur racine. Le nom de la racine est utilisé pour regrouper tout le suivi pour un contexte.  
  
## <a name="return-value"></a>Valeur de retour  
 [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) avec la [réussite] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) bit défini si le contexte de suivi a été créé.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** FileTracker.h  
  
## <a name="see-also"></a>Voir aussi  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)



