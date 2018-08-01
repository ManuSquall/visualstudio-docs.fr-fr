---
title: ResumeTracking | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2ec83d60046a74484035df9d7a7831d16b48d899
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151179"
---
# <a name="resumetracking"></a>ResumeTracking
Reprend le suivi dans le contexte actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT WINAPI ResumeTracking();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Un **HRESULT** avec le bit **SUCCEEDED** défini si le suivi a été repris. **E_FAIL** est retourné si le suivi ne peut pas être repris, car le contexte n’était pas disponible.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** *FileTracker.h*  
  
## <a name="see-also"></a>Voir aussi  
 [SuspendTracking](../msbuild/suspendtracking.md)