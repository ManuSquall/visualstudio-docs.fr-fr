---
title: IDebugApplication::HandleBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0478d0154ee79c1781885b94ae342e421e61e5e1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095366"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Provoque le blocage du thread actuel et envoie une notification du point d’arrêt à l’IDE de débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `br`  
 [in] La raison de l’arrêt.  
  
 `pbra`  
 [out] Action à entreprendre lorsque le débogueur reprend l’application.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Un moteur de langage appelle cette méthode dans le contexte d’un thread qui atteint un point d’arrêt. Cette méthode bloque le thread actuel et envoie une notification de point d’arrêt à l’IDE de débogueur. Lorsque le débogueur reprend l’application, le `pbra` paramètre spécifie l’action à entreprendre.  
  
> [!NOTE]
>  Le moteur de langage peut être appelé par le thread d’effectuer des tâches telles que la pile d’énumérer des frames ou évaluent les expressions pendant le point d’arrêt.  
  
 Cette méthode provoque `IApplicationDebugger::onHandleBreakPoint` à appeler.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [Énumération BREAKREASON](../../winscript/reference/breakreason-enumeration.md)   
 [Énumération BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)