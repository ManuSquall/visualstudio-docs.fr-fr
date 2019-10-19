---
title: 'IScriptNode :: GetIndexInParent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetIndexInParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetIndexInParent
ms.assetid: 521c1ca1-2d27-4344-bf3b-d8b53132b648
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9251f65414a5ebd48ce56dae6a7dbfeec4e514e3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575044"
---
# <a name="iscriptnodegetindexinparent"></a>IScriptNode::GetIndexInParent
Retourne l’index d’un objet dans la liste des enfants du parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetIndexInParent(  
   ULONG              pisn,  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pisn`  
 à Retourne l’index d’un objet dans la liste des enfants du parent.  
  
 Si cette méthode est appelée par un objet `IScriptNode` qui représente une page Web, ce paramètre retourne 0.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptNode](../../winscript/reference/iscriptnode-interface.md)