---
title: ResumeTracking | Microsoft Docs
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
ms.openlocfilehash: 6bb4663013a73d88ed7c2118816007705834162c
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578450"
---
# <a name="resumetracking"></a>ResumeTracking
Reprend le suivi dans le contexte actuel.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Valeur retournée
 Un **HRESULT** avec le bit **SUCCEEDED** défini si le suivi a été repris. **E_FAIL** est retourné si le suivi ne peut pas être repris, car le contexte n’était pas disponible.

## <a name="requirements"></a>Spécifications
 **En-tête :** *FileTracker. h*

## <a name="see-also"></a>Voir aussi
- [SuspendTracking](../msbuild/suspendtracking.md)