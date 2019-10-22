---
title: 'IDebugApplicationThread :: SetStateString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.SetStateString
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SetStateString
ms.assetid: a59001d5-ea00-4fd0-bb20-0b592d9c795d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de4a3e4e9666d6686400e5560343309591b2b3e1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574509"
---
# <a name="idebugapplicationthreadsetstatestring"></a>IDebugApplicationThread::SetStateString
Définit la description de l’état du thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetStateString(  
   LPCOLESTR  pstrState  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrState`  
 dans Description de l’état du thread.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode définit la description de l’état du thread.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)