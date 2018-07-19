---
title: SetThreadCount | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b36da837ae1f4c327969b398c3964bfd6dd2aea3
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36302748"
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
  
## <a name="return-value"></a>Valeur de retour  
 **HRESULT** avec le bit **SUCCEEDED** défini si le nombre de threads a été mis à jour.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** FileTracker.h