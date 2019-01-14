---
title: StartTrackingContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a12945400c1d479ad8543b2c8f050098d326881
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844117"
---
# <a name="starttrackingcontext"></a>StartTrackingContext
Démarre un contexte de suivi.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `intermediateDirectory`  
 Répertoire où stocker le journal de suivi.  
  
 [in] `taskName`  
 Identifie le contexte de suivi. Ce nom est utilisé pour créer le nom du fichier journal.  
  
## <a name="return-value"></a>Valeur de retour  
 **HRESULT** avec le bit **SUCCEEDED** défini si le contexte de suivi a été créé.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** *FileTracker.h*