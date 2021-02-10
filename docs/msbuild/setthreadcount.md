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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f7282b8c4589007492e48994628910b3a4ef0691
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966160"
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

## <a name="requirements"></a>Configuration requise

 **En-tête :** *FileTracker.h*