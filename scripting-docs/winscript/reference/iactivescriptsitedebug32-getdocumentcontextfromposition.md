---
title: 'IActiveScriptSiteDebug32 :: GetDocumentContextFromPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b43b16f46cc62b6c70460d79c194b5e0d2cfede0
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835275"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
Utilisé par le moteur de langage pour déléguer `IDebugCodeContext::GetSourceContext` .  
  
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
 dans Contenu source fourni à `ParseScriptText` ou `AddScriptlet` .  
  
 `uCharacterOffset`  
 dans Décalage de caractère par rapport au début du bloc de script ou du scriptlet.  
  
 `uNumChars`  
 dans Nombre de caractères dans ce contexte.  
  
 `ppsc`  
 à Contexte de document correspondant à cette plage de position de caractère.  
  
## <a name="return-value"></a>Valeur renvoyée  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|S_OK|  
  
## <a name="remarks"></a>Remarques  
 Les moteurs de langage utilisent cette méthode pour déléguer `IDebugCodeContext::GetSourceContext` .  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)