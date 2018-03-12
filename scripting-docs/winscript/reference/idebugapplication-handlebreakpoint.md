---
title: IDebugApplication::HandleBreakPoint | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplication.HandleBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16b05533c566cb90529766d81fb7197dbc284664
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Provoque le blocage du thread actuel et envoie une notification du point d’arrêt dans le débogueur IDE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `br`  
 [in] La raison de l’arrêt.  
  
 `pbra`  
 [out] Action à entreprendre lorsque le débogueur sort de l’application.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Un moteur de langage appelle cette méthode dans le contexte d’un thread qui atteint un point d’arrêt. Cette méthode bloque le thread actuel et envoie une notification de point d’arrêt dans le débogueur IDE. Lorsque le débogueur sort de l’application, le `pbra` paramètre spécifie l’action à entreprendre.  
  
> [!NOTE]
>  Le moteur de langage peut être appelé par le thread d’effectuer des tâches, telles qu’énumérer la pile de cadres ou évaluent les expressions pendant le point d’arrêt.  
  
 Cette méthode provoque `IApplicationDebugger::onHandleBreakPoint` à appeler.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplication (Interface)](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [Énumération BREAKREASON](../../winscript/reference/breakreason-enumeration.md)   
 [Énumération BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)