---
title: IActiveScriptAuthor::GetRoot | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetRoot
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetRoot
ms.assetid: 8e55a0c0-dd35-43d5-bf6f-e2f59c1e88d1
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb20a896d54c2b8e85c93014e6bd8ad3c906f55c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetroot"></a>IActiveScriptAuthor::GetRoot
Retourne le `IScriptNode` racine d’arborescence de script de l’auteur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRoot(  
   IScriptNode        **ppsp  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppsp`  
 [out] L’adresse d’une variable qui reçoit un pointeur vers le `IScriptNode` interface du nœud racine.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptAuthor (Interface)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Interface IScriptNode](../../winscript/reference/iscriptnode-interface.md)