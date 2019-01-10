---
title: IActiveScriptSiteDebug::GetDocumentContextFromPosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetDocumentContextFromPosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetDocumentContextFromPosition
ms.assetid: ba5f7348-0107-4b12-b949-79a012476cf7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1bcc7469e02ba380ebd6839e9fe55031e52ecd32
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086982"
---
# <a name="iactivescriptsitedebuggetdocumentcontextfromposition"></a>IActiveScriptSiteDebug::GetDocumentContextFromPosition
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
 [Interface IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)