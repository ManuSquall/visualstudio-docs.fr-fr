---
title: IDebugApplicationThread::SetStateString | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationThread.SetStateString
apilocation: pdm.dll
helpviewer_keywords: IDebugApplicationThread::SetStateString
ms.assetid: a59001d5-ea00-4fd0-bb20-0b592d9c795d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2eafe5477759dbad109e5ae6294b477d56f9ee14
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadsetstatestring"></a>IDebugApplicationThread::SetStateString
Définit la description de l’état du thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetStateString(  
   LPCOLESTR  pstrState  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrState`  
 [in] Description de l’état du thread.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode définit la description de l’état du thread.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)