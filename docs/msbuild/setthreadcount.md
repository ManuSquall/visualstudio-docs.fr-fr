---
title: SetThreadCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 102f46ec639719bb2bec70a38c6c7177c63793c1
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632327"
---
# <a name="setthreadcount"></a>SetThreadCount

Définit le nombre global de threads et affecte ce nombre au thread actif.

## <a name="syntax"></a>Syntaxe

```cmd
HRESULT WINAPI SetThreadCount(int threadCount);
```

#### <a name="parameters"></a>Paramètres

[in] `threadCount`

 Nombre de threads à utiliser.

## <a name="return-value"></a>Valeur retournée

 **HRESULT** avec le bit **SUCCEEDED** défini si le nombre de threads a été mis à jour.

## <a name="requirements"></a>Configuration requise

 **En-tête :** *FileTracker. h*