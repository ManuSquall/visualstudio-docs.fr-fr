---
title: 'ISetNextStatement :: SetNextStatement | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISetNextStatement.SetNextStatement
apilocation:
- scrobj.dll
ms.assetid: c5534f3b-39a5-4466-b8fc-69b717c6eee9
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8b940e603deb0aa9715e89b49eb1afdd28832ac
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571912"
---
# <a name="isetnextstatementsetnextstatement"></a>ISetNextStatement::SetNextStatement
Cette méthode met à jour le contexte de code suivant que l’interpréteur de script peut exécuter.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pStackFrame`  
 dans Pointeur vers un objet de frame de pile.  
  
 `pCodeContext`  
 dans Pointeur vers un objet de contexte de code.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)