---
title: 'IScriptNode :: GetChild | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27ddde527be1ea4148e4166581ab2cb1a71d15f7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573564"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Retourne l’enfant qui se trouve à l’index spécifié dans le nœud.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `isn`  
 dans Index de l’enfant dans le parent.  
  
 `ppsn`  
 à Adresse d’une variable qui reçoit un pointeur vers l’interface `IScriptNode` de l’instance enfant.  
  
 Pour les objets `IScriptNode` qui représentent une page Web, ce paramètre retourne un objet qui contient un bloc de script.  
  
 Pour les objets `IScriptEntry` qui spécifient un bloc de script, ce paramètre retourne un objet qui spécifie une fonction.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Pour les objets `IScriptEntry` qui spécifient un objet de fonction et pour les objets `IScriptScriptlet`, cette méthode échoue parce qu’il n’y a pas d’entrées enfants.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptNode](../../winscript/reference/iscriptnode-interface.md)