---
title: IScriptNode::Delete | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Delete
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Delete
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cce802cc1a6d63001cfbed020592b30a9d8dab1b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094794"
---
# <a name="iscriptnodedelete"></a>IScriptNode::Delete
Supprime cette arborescence d’objets.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Delete();  
```  
  
#### <a name="parameters"></a>Paramètres  
 La méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Après le `Delete` méthode est appelée, le [IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md) méthode doit indiquer ce nœud de script n’est pas actif.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptNode](../../winscript/reference/iscriptnode-interface.md)