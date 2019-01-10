---
title: IScriptNode::GetChild | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 55cd6cf5233e850e4109128e322d3fc5bd0b1355
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086591"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Retourne l’enfant qui est à l’index spécifié dans le nœud.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `isn`  
 [in] L’index de l’enfant de la page parente.  
  
 `ppsn`  
 [out] L’adresse d’une variable qui reçoit un pointeur vers le `IScriptNode` interface de l’instance enfant.  
  
 Pour `IScriptNode` les objets qui représentent une page Web, ce paramètre retourne un objet qui contient un bloc de script.  
  
 Pour `IScriptEntry` les objets qui spécifient un bloc de script, ce paramètre retourne un objet qui spécifie une fonction.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Pour `IScriptEntry` objets qui spécifient un objet de fonction et pour `IScriptScriptlet` objets, cette méthode échoue, car aucune entrée enfant.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptNode](../../winscript/reference/iscriptnode-interface.md)