---
title: IActiveScriptDebug::EnumCodeContextsOfPosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::EnumCodeContextsOfPosition
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: abca643dc4e18f786421959c20804a28cf54ec7b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097173"
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Utilisé par un hôte intelligent pour déléguer la `IDebugDocumentContext::EnumCodeContexts` (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwSourceContext`  
 [in] Le contexte de la source fournie à `IActiveScriptParse::ParseScriptText` ou `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Caractère décalée par rapport à début du texte de script.  
  
 `uNumChars`  
 [in] Nombre de caractères dans ce contexte.  
  
 `ppescc`  
 [out] Énumérateur des contextes de code dans la plage spécifiée.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Hôtes intelligents permet de déléguer le `IDebugDocumentContext::EnumCodeContexts` (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptDebug (Interface)](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)