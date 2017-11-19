---
title: IDebugDocumentProvider::GetDocument | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentProvider.GetDocument
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentProvider::GetDocument
ms.assetid: da67dab0-778a-4dab-8ca3-055ee7a4f141
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8dd952a63253dbbf6034e0345547e2bec73b60c2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentprovidergetdocument"></a>IDebugDocumentProvider::GetDocument
Provoque le document à instancier si elle n’existe pas déjà.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDocument(  
   IDebugDocument**  ppssd  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppssd`  
 [out] Le document de débogage correspondant au document.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode entraîne le document à instancier si elle n’existe pas déjà.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentProvider](../../winscript/reference/idebugdocumentprovider-interface.md)