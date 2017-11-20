---
title: IDebugDocumentContext::GetDocument | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentContext.GetDocument
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentContext::GetDocument
ms.assetid: 32db2fea-4938-4644-b39a-8fae05960d1d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6776a65ca9adbcf9304e57e0b93f4ebcb4a33bc4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentcontextgetdocument"></a>IDebugDocumentContext::GetDocument
Retourne le document qui contient ce contexte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDocument(  
   IDebugDocument**  ppsd  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppsd`  
 [out] Le document qui contient ce contexte.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Le `GetDocument` méthode retourne le document qui contient ce contexte.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md)