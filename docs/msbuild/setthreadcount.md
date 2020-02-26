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
ms.openlocfilehash: 5b1eb28d5a54af1708fa8d3ea7a12887174a15bb
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579590"
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

## <a name="requirements"></a>Spécifications
 **En-tête :** *FileTracker. h*