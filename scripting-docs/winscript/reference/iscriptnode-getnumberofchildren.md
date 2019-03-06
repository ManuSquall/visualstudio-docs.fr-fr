---
title: IScriptNode::GetNumberOfChildren | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetNumberOfChildren
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetNumberOfChildren
ms.assetid: 3451c7e9-cb50-482e-9038-6e7d7ce1ecdf
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a6c1cd7ee65f4bd01373d112bc7afdcf0dd06d2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094677"
---
# <a name="iscriptnodegetnumberofchildren"></a>IScriptNode::GetNumberOfChildren
Retourne le nombre de nœuds enfants de la `IScriptNode` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetNumberOfChildren(  
   ULONG              *pcsn  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pcsn`  
 [out] Le nombre de nœuds enfants qui le `IScriptNode` a de l’objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptNode](../../winscript/reference/iscriptnode-interface.md)