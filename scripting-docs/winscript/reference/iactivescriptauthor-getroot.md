---
title: 'IActiveScriptAuthor :: GetRoot | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetRoot
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetRoot
ms.assetid: 8e55a0c0-dd35-43d5-bf6f-e2f59c1e88d1
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca2aab154d56cd98c3c2acede61f86f725ce9c1b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576185"
---
# <a name="iactivescriptauthorgetroot"></a>IActiveScriptAuthor::GetRoot
Retourne la racine `IScriptNode` de l’arborescence de script de l’auteur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetRoot(  
   IScriptNode        **ppsp  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppsp`  
 à Adresse d’une variable qui reçoit un pointeur vers l’interface `IScriptNode` du nœud racine.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)  
 [Interface IScriptNode](../../winscript/reference/iscriptnode-interface.md)