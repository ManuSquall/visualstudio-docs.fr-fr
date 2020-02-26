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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36b48529f82a908ea765151561a71c58cd2c7bc5
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578419"
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

## <a name="return-value"></a>Valeur retournée
 **HRESULT** avec le bit **SUCCEEDED** défini si le contexte de suivi a été créé.

## <a name="requirements"></a>Spécifications
 **En-tête :** *FileTracker. h*

## <a name="see-also"></a>Voir aussi
- [StartTrackingContext](../msbuild/starttrackingcontext.md)