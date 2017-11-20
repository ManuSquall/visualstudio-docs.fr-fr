---
title: IApplicationDebugger::QueryAlive | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IApplicationDebugger.QueryAlive
apilocation: scrobj.dll
helpviewer_keywords: IApplicationDebugger::QueryAlive
ms.assetid: 41181ebb-a3bf-4e41-82af-d6c7348dc706
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48571476407c29b9af949bd6f626d14ea822f2e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggerqueryalive"></a>IApplicationDebugger::QueryAlive
Indique si le débogueur ne répond.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QueryAlive();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode indique si le débogueur ne répond. Les implémentations de cette méthode doivent toujours retourner `S_OK`.  
  
 Si le processus du débogueur s’arrête de manière inattendue, COM retourne une erreur à partir du proxy de marshaling pour les appels à cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)