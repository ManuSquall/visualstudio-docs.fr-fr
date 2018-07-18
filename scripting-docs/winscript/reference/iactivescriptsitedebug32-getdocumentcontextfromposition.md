---
title: IActiveScriptSiteDebug32::GetDocumentContextFromPosition | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 71136a1b3cb136cbc0a97cf39f59f1f4e950048b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725079"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
Utilisé par le moteur de langage pour déléguer `IDebugCodeContext::GetSourceContext`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwSourceContext`  
 [in] Le contenu de la source à `ParseScriptText` ou `AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Un décalage relatif au début du bloc de script ou scriptlet de caractères.  
  
 `uNumChars`  
 [in] Nombre de caractères dans ce contexte.  
  
 `ppsc`  
 [out] Le contexte de document correspondant à cette étendue de la position de caractère.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Moteurs de langue permet de déléguer `IDebugCodeContext::GetSourceContext`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)