---
title: 'IDebugDocumentHelper :: SetTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetTextAttributes
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetTextAttributes
ms.assetid: 31657738-9e4c-436a-be61-23f4185d452e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cc5e5955652fd8b59d4c502e68d97a729ded141
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569461"
---
# <a name="idebugdocumenthelpersettextattributes"></a>IDebugDocumentHelper::SetTextAttributes
Définit les attributs d’une plage de texte, en substituant d’autres attributs sur ce texte.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetTextAttributes(  
   ULONG              ulCharOffset,  
   ULONG              cChars,  
   SOURCE_TEXT_ATTR*  pstaTextAttr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ulCharOffset`  
 dans Emplacement du début de la plage de texte.  
  
 `cChars`  
 dans Nombre de caractères de la plage.  
  
 `pstaTextAttr`  
 dans Attributs de texte source pour la plage de texte.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 L’appel de `SetTextAttributes` sur une plage de texte est une erreur avant que le texte ne soit ajouté au document. Appelez les méthodes `AddDBCSText`, `AddUnicodeText` ou `AddDeferredText` pour ajouter du texte au document.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHelper :: AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)    
 [IDebugDocumentHelper :: AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)    
 [IDebugDocumentHelper :: AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [Énumération SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)