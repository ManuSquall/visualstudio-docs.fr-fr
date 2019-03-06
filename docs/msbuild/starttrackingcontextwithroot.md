---
title: StartTrackingContextWithRoot | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContextWithRoot
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53f2c1ebd5896eaa8a4b9d5ff4e5cb7856a1f8e2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690486"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot
Démarre un contexte de suivi en utilisant un fichier réponse spécifiant un marqueur racine.

## <a name="syntax"></a>Syntaxe

```cpp
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
 **HRESULT** avec le bit **SUCCEEDED** défini si le contexte de suivi a été créé.

## <a name="requirements"></a>Spécifications
 **En-tête :** *FileTracker.h*

## <a name="see-also"></a>Voir aussi
- [StartTrackingContext](../msbuild/starttrackingcontext.md)