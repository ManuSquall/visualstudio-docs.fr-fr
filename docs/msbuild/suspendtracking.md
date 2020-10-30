---
title: SuspendTracking | Microsoft Docs
description: En savoir plus sur la syntaxe, les exigences et la valeur de retour pour MSBuild SuspendTracking, qui interrompt le suivi dans le contexte actuel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 164e1a11c7d107bf1d98419d77fdc50ed353f93b
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048087"
---
# <a name="suspendtracking"></a>SuspendTracking

Interrompt le suivi dans le contexte actuel.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Valeur de retour

 **HRESULT** avec le bit **Succeeded** défini si le suivi a été suspendu.

## <a name="requirements"></a>Spécifications

 **En-tête :** *FileTracker.h*

## <a name="see-also"></a>Voir aussi

- [ResumeTracking](../msbuild/resumetracking.md)