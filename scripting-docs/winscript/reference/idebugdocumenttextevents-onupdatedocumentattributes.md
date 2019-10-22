---
title: 'IDebugDocumentTextEvents :: onUpdateDocumentAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onUpdateDocumentAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onUpdateDocumentAttributes
ms.assetid: 48fa909c-14c2-4ca4-af86-a5809c72dd39
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c256d2cc6d826a72eb369cda0ad1e5f108e909bc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576042"
---
# <a name="idebugdocumenttexteventsonupdatedocumentattributes"></a>IDebugDocumentTextEvents::onUpdateDocumentAttributes
Indique que les attributs du document ont été modifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onUpdateDocumentAttributes(  
   TEXT_DOC_ATTR  textdocattr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `textdocattr`  
 dans Nouveaux attributs du document.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode indique que les attributs de document ont été modifiés.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)  
 [Constantes TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)