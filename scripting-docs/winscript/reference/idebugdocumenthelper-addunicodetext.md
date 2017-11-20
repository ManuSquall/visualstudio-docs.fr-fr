---
title: IDebugDocumentHelper::AddUnicodeText | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.AddUnicodeText
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::AddUnicodeText
ms.assetid: f4ef648e-c55d-4ef0-8df3-e808b798d3b8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f387142675b0def99fb2cc0695bd3f9416d66809
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperaddunicodetext"></a>IDebugDocumentHelper::AddUnicodeText
Ajoute une chaîne Unicode à la fin de ce document.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AddUnicodeText(  
   LPCOLESTR  pszText  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszText`  
 [in] Pointeur vers une chaîne terminée par le caractère null qui contient le texte.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|La méthode n’a pas pu ajouter les caractères.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode génère `IDebugDocumentTextEvents` des notifications.  
  
> [!NOTE]
>  Si cette méthode est appelée après `AddDeferredText` a été appelée, `E_FAIL` est retourné.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentHelper (Interface)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Interface IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)