---
title: 'IActiveScriptSiteDebug32 :: GetDocumentContextFromPosition | Microsoft Docs'
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
ms.openlocfilehash: 7acbe2a5741fa94ac42470a85803d1720e0a8fa1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574844"
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
 dans Contenu source fourni pour `ParseScriptText` ou `AddScriptlet`.  
  
 `uCharacterOffset`  
 dans Décalage de caractère par rapport au début du bloc de script ou du scriptlet.  
  
 `uNumChars`  
 dans Nombre de caractères dans ce contexte.  
  
 `ppsc`  
 à Contexte de document correspondant à cette plage de position de caractère.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Les moteurs de langage utilisent cette méthode pour déléguer `IDebugCodeContext::GetSourceContext`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)