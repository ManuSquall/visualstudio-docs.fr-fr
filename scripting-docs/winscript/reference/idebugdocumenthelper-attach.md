---
title: IDebugDocumentHelper::Attach | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: f0f397f70d994d0997163a06766d32c35e9b2ab7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090140"
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
 [in] L’arborescence du document où ce document doit être ajouté. Peut être NULL.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode ajoute ce document au document d’arborescence, à l’aide de `pddhParent` comme parent. Si le `pddhParent` est `NULL`, ce document sera le document de niveau supérieur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [Interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)