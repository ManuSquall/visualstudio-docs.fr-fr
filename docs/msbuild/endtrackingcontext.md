---
title: EndTrackingContext | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf982200b8e65e404325bdbd189ff3b0f2daebac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634238"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

Mettez fin au contexte de suivi actuel.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Valeur retournée

**HRESULT** avec le bit **Succeeded** défini si le contexte de suivi a été terminé.

## <a name="requirements"></a>Configuration requise

**En-tête :** *FileTracker.h*

## <a name="see-also"></a>Voir aussi

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
