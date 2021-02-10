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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e8be768bc48c1815fc00069640e5bf3f4370f434
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945277"
---
# <a name="suspendtracking"></a>SuspendTracking

Interrompt le suivi dans le contexte actuel.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Valeur de retour

 **HRESULT** avec le bit **Succeeded** défini si le suivi a été suspendu.

## <a name="requirements"></a>Configuration requise

 **En-tête :** *FileTracker.h*

## <a name="see-also"></a>Voir aussi

- [ResumeTracking](../msbuild/resumetracking.md)