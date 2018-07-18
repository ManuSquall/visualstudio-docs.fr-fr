---
title: IScriptNode::Delete | Documents Microsoft
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
ms.openlocfilehash: 1d1404d90cc1edd882505e463938a2c1a5e8aea8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733659"
---
# <a name="iscriptnodedelete"></a>IScriptNode::Delete
Supprime cette arborescence d’objets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Delete();  
```  
  
#### <a name="parameters"></a>Paramètres  
 La méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Après le `Delete` méthode est appelée, le [IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md) méthode doit indiquer ce nœud de script n’est pas actif.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptNode](../../winscript/reference/iscriptnode-interface.md)