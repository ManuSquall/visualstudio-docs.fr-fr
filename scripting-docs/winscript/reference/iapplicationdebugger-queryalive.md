---
title: 'IApplicationDebugger :: QueryAlive | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.QueryAlive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::QueryAlive
ms.assetid: 41181ebb-a3bf-4e41-82af-d6c7348dc706
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 867d00a4ef42aa8759496540edc1937fc6f2a0a6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577823"
---
# <a name="iapplicationdebuggerqueryalive"></a>IApplicationDebugger::QueryAlive
Indique si le débogueur est réactif.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT QueryAlive();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode indique si le débogueur est réactif. Les implémentations de cette méthode doivent toujours retourner `S_OK`.  
  
 Si le processus du débogueur s’arrête de manière inattendue, COM retourne une erreur du proxy de marshaling pour les appels à cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)