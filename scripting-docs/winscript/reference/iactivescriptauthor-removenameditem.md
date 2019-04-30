---
title: IActiveScriptAuthor::RemoveNamedItem | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.RemoveNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::RemoveNamedItem
ms.assetid: 1173ef46-39a5-4bc1-8e0c-89259a16be16
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 052704b9a1bef8c50c457e51438f0204813c2efe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955144"
---
# <a name="iactivescriptauthorremovenameditem"></a>IActiveScriptAuthor::RemoveNamedItem
Supprime un `NamedItem` objet à partir de l’espace de noms du script du moteur de création.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszName`  
 [in] L’adresse de la mémoire tampon qui identifie le `NamedItem` objet à supprimer.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`S_FALSE`|Le `NamedItem` objet n’est pas présent dans l’espace de noms du script du moteur de création.|  
  
## <a name="remarks"></a>Notes  
 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) est utilisée pour injecter le `NamedItem` objet dans l’espace de noms du moteur de création de script.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptAuthor (Interface)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)