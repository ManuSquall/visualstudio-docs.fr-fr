---
title: IDebugDocumentText::GetDocumentAttributes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetDocumentAttributes
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetDocumentAttributes
ms.assetid: 8c544ca1-8db4-4bca-973e-09315d9a0ee5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f689aa6f930a596239483176e1aa9f2fcc8cdd3e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086604"
---
# <a name="idebugdocumenttextgetdocumentattributes"></a>IDebugDocumentText::GetDocumentAttributes
Retourne les attributs du document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDocumentAttributes(  
   TEXT_DOC_ATTR*  ptextdocattr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ptextdocattr`  
 [out] Les attributs de texte du document.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne les attributs du document.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentText (Interface)](../../winscript/reference/idebugdocumenttext-interface.md)   
 [Constantes TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)