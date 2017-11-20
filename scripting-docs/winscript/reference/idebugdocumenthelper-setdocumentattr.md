---
title: IDebugDocumentHelper::SetDocumentAttr | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.SetDocumentAttr
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::SetDocumentAttr
ms.assetid: bd7ffdbd-de51-477d-bd3f-760db020fe70
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d0fb7fc506c8ed0284fe7d0f4853c6410218865b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelpersetdocumentattr"></a>IDebugDocumentHelper::SetDocumentAttr
Définit les attributs de ce document.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetDocumentAttr(  
   TEXT_DOC_ATTR  pszAttributes  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszAttributes`  
 [in] Les attributs à appliquer au document.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode définit les attributs de ce document.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentHelper (Interface)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Constantes TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)