---
title: IActiveScriptAuthor::RemoveNamedItem | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 64f62acd02e0901af341a571fb09ba81f3a11f28
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088827"
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