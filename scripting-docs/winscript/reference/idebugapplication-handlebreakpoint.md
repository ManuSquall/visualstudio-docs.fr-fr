---
title: IDebugApplication::HandleBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30937817424e88f80cfa6afa8c874adfd2b2687b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574961"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Provoque le blocage du thread actuel et envoie une notification du point d’arrêt à l’IDE du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `br`  
 dans Raison de l’arrêt.  
  
 `pbra`  
 à Action à entreprendre lorsque le débogueur reprend l’application.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Un moteur de langage appelle cette méthode dans le contexte d’un thread qui atteint un point d’arrêt. Cette méthode bloque le thread actuel et envoie une notification de point d’arrêt à l’IDE du débogueur. Lorsque le débogueur reprend l’application, le paramètre `pbra` spécifie l’action à entreprendre.  
  
> [!NOTE]
> Le moteur de langage peut être appelé par le thread pour effectuer des tâches telles que l’énumération des frames de pile ou l’évaluation d’expressions pendant le point d’arrêt.  
  
 Cette méthode provoque l’appel de `IApplicationDebugger::onHandleBreakPoint`.  
  
## <a name="see-also"></a>Voir aussi  
   de l' [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [IApplicationDebugger :: onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
   de l' [énumération BREAKREASON](../../winscript/reference/breakreason-enumeration.md)  
 [Énumération BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)