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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e74e44289e4fd04acf82170584af8645767b63e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905236"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup

Arrête tout le suivi et libère la mémoire utilisée par la session de suivi.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Valeur de retour

 Retourne un **HRESULT** avec le bit **Succeeded** défini si le suivi a été arrêté.

## <a name="requirements"></a>Configuration requise

 **En-tête :** *FileTracker.h*

## <a name="see-also"></a>Voir aussi

- [StartTrackingContext](../msbuild/starttrackingcontext.md)