---
title: IScriptNode::GetChild | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptNode.GetChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d127b1b8a8db0c6d272e50d33b523fbe182a9e21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Retourne l’enfant qui est à l’index spécifié dans le nœud.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `isn`  
 [in] L’index de l’enfant du parent.  
  
 `ppsn`  
 [out] L’adresse d’une variable qui reçoit un pointeur vers le `IScriptNode` interface de l’instance enfant.  
  
 Pour `IScriptNode` les objets qui représentent une page Web, ce paramètre retourne un objet qui contient un bloc de script.  
  
 Pour `IScriptEntry` les objets qui spécifient un bloc de script, ce paramètre retourne un objet qui spécifie une fonction.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Pour `IScriptEntry` objets qui spécifient un objet de fonction et pour `IScriptScriptlet` des objets, cette méthode échoue, car aucune entrée enfant.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptNode](../../winscript/reference/iscriptnode-interface.md)