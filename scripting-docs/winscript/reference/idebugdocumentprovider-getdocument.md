---
title: 'IDebugDocumentProvider :: GetDocument | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentProvider.GetDocument
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentProvider::GetDocument
ms.assetid: da67dab0-778a-4dab-8ca3-055ee7a4f141
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9240f059023fee4f55f34c80087063638ec8ad6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572174"
---
# <a name="idebugdocumentprovidergetdocument"></a>IDebugDocumentProvider::GetDocument
Provoque l’instanciation du document s’il n’existe pas déjà.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDocument(  
   IDebugDocument**  ppssd  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppssd`  
 à Document de débogage correspondant au document.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode provoque l’instanciation du document s’il n’existe pas déjà.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentProvider](../../winscript/reference/idebugdocumentprovider-interface.md)