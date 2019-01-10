---
title: IActiveScriptSiteDebug32::GetDocumentContextFromPosition | Microsoft Docs
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
ms.openlocfilehash: 9a52abcfa4defb49526f944469c95a2247f5d85c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094482"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
Utilisé par le moteur de langage pour déléguer `IDebugCodeContext::GetSourceContext`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwSourceContext`  
 [in] Le contenu de la source fournie à `ParseScriptText` ou `AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Caractère décalée par rapport à début du bloc de script ou de scriptlet.  
  
 `uNumChars`  
 [in] Nombre de caractères dans ce contexte.  
  
 `ppsc`  
 [out] Le contexte de document correspondant à cette plage de la position de caractère.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Moteurs de langage permet de déléguer `IDebugCodeContext::GetSourceContext`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)