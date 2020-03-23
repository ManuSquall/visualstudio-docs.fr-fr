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
ms.openlocfilehash: 248bb5e5e01b8209f826478e90b2c60b70922987
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632496"
---
# <a name="resumetracking"></a>ResumeTracking

Reprend le suivi dans le contexte actuel.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Valeur retournée

 Un **HRESULT** avec l’ensemble **de bits SUCCEEDED** si le suivi a été repris. **E_FAIL** est retourné si le suivi ne peut être repris parce que le contexte n’était pas disponible.

## <a name="requirements"></a>Spécifications

 **En-tête :** *FileTracker.h*

## <a name="see-also"></a>Voir aussi

- [SuspendTracking](../msbuild/suspendtracking.md)