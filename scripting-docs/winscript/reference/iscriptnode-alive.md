---
title: IScriptNode::Alive | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Alive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Alive
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da0a55d26b5ab643670ba7ed51e576eeb89d8b98
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787171"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
Indique si un objet est toujours actif.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>Paramètres  
 La méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|Le nœud de script est toujours actif.|  
  
## <a name="remarks"></a>Notes  
 Si l’objet n’est pas actif, le composant COM (Object Model) retourne une erreur à partir du proxy de marshaling pour les appels à cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptNode](../../winscript/reference/iscriptnode-interface.md)