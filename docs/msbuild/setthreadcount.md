---
title: SetThreadCount | Microsoft Docs
description: Découvrez comment MSBuild utilise SetThreadCount pour définir le nombre de threads global et assigner ce nombre au thread actuel.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 01bfdae1dcd11d7df042948308c424b7773b3bb0
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048328"
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

 **HRESULT** avec le bit **Succeeded** défini si le nombre de threads a été mis à jour.

## <a name="requirements"></a>Spécifications

 **En-tête :** *FileTracker.h*