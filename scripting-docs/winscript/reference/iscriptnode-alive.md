---
title: IScriptNode::Alive | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptNode.Alive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Alive
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0631690cbd961273175cf8dfbe35550980d4994d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
Indique si un objet est toujours actif.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>Paramètres  
 La méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|Le nœud de script est toujours actif.|  
  
## <a name="remarks"></a>Remarques  
 Si l’objet n’est pas actif, le modèle COM (Component Object) retourne une erreur à partir du proxy de marshaling pour les appels à cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptNode](../../winscript/reference/iscriptnode-interface.md)