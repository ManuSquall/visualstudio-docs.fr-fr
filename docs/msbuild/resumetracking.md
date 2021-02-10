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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fd6722ca0b930d66a386732dac466a8e4fe36976
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937912"
---
# <a name="resumetracking"></a>ResumeTracking

Reprend le suivi dans le contexte actuel.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Valeur de retour

 **HRESULT** avec le bit **Succeeded** défini si le suivi a été repris. **E_FAIL** est retourné si le suivi ne peut pas être repris car le contexte n’était pas disponible.

## <a name="requirements"></a>Configuration requise

 **En-tête :** *FileTracker.h*

## <a name="see-also"></a>Voir aussi

- [SuspendTracking](../msbuild/suspendtracking.md)