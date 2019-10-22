---
title: 'IRemoteDebugApplicationThread :: SetNextStatement | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.SetNextStatement
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::SetNextStatement
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71e690d0e5b7567aabc88aabde907b67517f12aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575505"
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
Force l’exécution à se poursuivre le plus près possible du contexte de code donné, dans le contexte du frame donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pStackFrame`  
 dans Objet de frame de pile. Cet argument peut avoir la valeur NULL, ce qui implique que le frame de pile actuel doit être utilisé.  
  
 `pCodeContext`  
 dans Contexte de code. Cet argument peut avoir la valeur NULL, ce qui implique que le contexte de code actuel doit être utilisé.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode force l’exécution à se poursuivre le plus près possible du contexte de code spécifié par `pCodeContext`, dans le contexte du frame spécifié par `pStackFrame`. L’un ou l’autre de ces arguments peut être `NULL`, représentant l’image ou le contexte actuel.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)