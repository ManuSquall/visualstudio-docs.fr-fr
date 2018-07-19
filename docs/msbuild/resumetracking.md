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
ms.openlocfilehash: e241af310821463f60f323b9fd20099fad44a3ba
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326278"
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
 **En-tête :** FileTracker.h  
  
## <a name="see-also"></a>Voir aussi  
 [SuspendTracking](../msbuild/suspendtracking.md)