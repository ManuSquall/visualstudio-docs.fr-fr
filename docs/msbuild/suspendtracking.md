---
title: SuspendTracking | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a093b89264df43574acd3929d4370bb43162d829
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946748"
---
# <a name="suspendtracking"></a>SuspendTracking
Interrompt le suivi dans le contexte actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp 
HRESULT WINAPI SuspendTracking(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Un **HRESULT** avec le bit **SUCCEEDED** défini si le suivi a été repris.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** *FileTracker.h*  
  
## <a name="see-also"></a>Voir aussi  
 [ResumeTracking](../msbuild/resumetracking.md)