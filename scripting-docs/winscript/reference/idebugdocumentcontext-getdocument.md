---
title: 'IDebugDocumentContext :: GetDocument | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentContext.GetDocument
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentContext::GetDocument
ms.assetid: 32db2fea-4938-4644-b39a-8fae05960d1d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bdf4c52d1a866df12a129f1d4f2e864068c876fa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577083"
---
# <a name="idebugdocumentcontextgetdocument"></a>IDebugDocumentContext::GetDocument
Retourne le document qui contient ce contexte.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDocument(  
   IDebugDocument**  ppsd  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppsd`  
 à Document qui contient ce contexte.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 La méthode `GetDocument` retourne le document qui contient ce contexte.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md)