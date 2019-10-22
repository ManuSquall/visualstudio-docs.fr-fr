---
title: 'IDebugDocumentHelper :: SetDocumentAttr | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDocumentAttr
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDocumentAttr
ms.assetid: bd7ffdbd-de51-477d-bd3f-760db020fe70
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2210557a1ca2b23d19d151d6fe6f3b5d25e7082
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574617"
---
# <a name="idebugdocumenthelpersetdocumentattr"></a>IDebugDocumentHelper::SetDocumentAttr
Définit les attributs de ce document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetDocumentAttr(  
   TEXT_DOC_ATTR  pszAttributes  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszAttributes`  
 dans Attributs à appliquer au document.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode définit les attributs de ce document.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [Constantes TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)