---
title: StopTrackingAndCleanup | Microsoft Docs
description: Découvrez comment MSBuild utilise StopTrackingAndCleanup pour arrêter tout le suivi et libérer la mémoire utilisée par la session de suivi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05aec8bc85ac392670469da8073da02888b2f063
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048096"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup

Arrête tout le suivi et libère la mémoire utilisée par la session de suivi.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Valeur de retour

 Retourne un **HRESULT** avec le bit **Succeeded** défini si le suivi a été arrêté.

## <a name="requirements"></a>Spécifications

 **En-tête :** *FileTracker.h*

## <a name="see-also"></a>Voir aussi

- [StartTrackingContext](../msbuild/starttrackingcontext.md)