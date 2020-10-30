---
title: ResumeTracking | Microsoft Docs
description: En savoir plus sur la syntaxe, les exigences et la valeur de retour pour MSBuild ResumeTracking, qui reprend le suivi dans le contexte actuel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9af7c90342638fb0c154e7de21fa111d560905d0
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048421"
---
# <a name="resumetracking"></a>ResumeTracking

Reprend le suivi dans le contexte actuel.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Valeur de retour

 **HRESULT** avec le bit **Succeeded** défini si le suivi a été repris. **E_FAIL** est retourné si le suivi ne peut pas être repris car le contexte n’était pas disponible.

## <a name="requirements"></a>Spécifications

 **En-tête :** *FileTracker.h*

## <a name="see-also"></a>Voir aussi

- [SuspendTracking](../msbuild/suspendtracking.md)