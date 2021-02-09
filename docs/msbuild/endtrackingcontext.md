---
title: EndTrackingContext | Microsoft Docs
description: Découvrez la syntaxe, la valeur de retour et la configuration requise pour utiliser MSBuild EndTrackingContext pour terminer le contexte de suivi actuel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90f4c8c4a83a496dba537e74dddfde4ae3f2f21a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877224"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

Mettez fin au contexte de suivi actuel.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Valeur de retour

**HRESULT** avec le bit **Succeeded** défini si le contexte de suivi a été terminé.

## <a name="requirements"></a>Configuration requise

**En-tête :** *FileTracker.h*

## <a name="see-also"></a>Voir aussi

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
