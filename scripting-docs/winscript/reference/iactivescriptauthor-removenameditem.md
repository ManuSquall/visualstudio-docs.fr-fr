---
title: 'IActiveScriptAuthor :: RemoveNamedItem | Microsoft Docs'
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
ms.openlocfilehash: cade532d2ca276237981855cafe12804307d0bb6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572840"
---
# <a name="iactivescriptauthorremovenameditem"></a>IActiveScriptAuthor::RemoveNamedItem
Supprime un objet `NamedItem` de l’espace de noms du moteur de création de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszName`  
 dans Adresse de la mémoire tampon qui identifie l’objet `NamedItem` à supprimer.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`S_FALSE`|L’objet `NamedItem` n’est pas présent dans l’espace de noms du moteur de création de script.|  
  
## <a name="remarks"></a>Notes  
 [IActiveScript :: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) est utilisé pour injecter l’objet `NamedItem` dans l’espace de noms du moteur de création de script.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)