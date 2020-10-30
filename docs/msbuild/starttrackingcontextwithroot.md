---
title: StartTrackingContextWithRoot | Microsoft Docs
description: Apprenez à utiliser MSBuild StartTrackingContextWithRoot pour démarrer un contexte de suivi à l’aide d’un fichier réponse spécifiant un marqueur racine.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ccca75a0fe525c4e1d9f421b2264070ebda9bdf3
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048132"
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

 **HRESULT** avec le bit **Succeeded** défini si le contexte de suivi a été créé.

## <a name="requirements"></a>Spécifications

 **En-tête :** *FileTracker.h*

## <a name="see-also"></a>Voir aussi

- [StartTrackingContext](../msbuild/starttrackingcontext.md)