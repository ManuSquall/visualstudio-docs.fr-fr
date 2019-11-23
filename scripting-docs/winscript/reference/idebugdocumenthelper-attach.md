---
title: 'IDebugDocumentHelper :: Attach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Attach
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3400a5bf6cd3e4a9726fdf4b2f20bbf43b9fc989
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577034"
---
# <a name="idebugdocumenthelperattach"></a>IDebugDocumentHelper::Attach
Ajoute ce document à l’arborescence du document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pddhParent`  
 dans Arborescence du document dans laquelle ce document sera ajouté. Peut être NULL.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode ajoute ce document à l’arborescence du document, à l’aide de `pddhParent` en tant que parent. Si le `pddhParent` est `NULL`, ce document sera le document de niveau supérieur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [Interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)