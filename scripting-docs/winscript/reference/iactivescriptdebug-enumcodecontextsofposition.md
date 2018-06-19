---
title: IActiveScriptDebug::EnumCodeContextsOfPosition | Documents Microsoft
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
ms.openlocfilehash: 40fd8e2d19d3949ff26811956ae3d203871e5510
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645589"
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Utilisé par un hôte actif pour déléguer la `IDebugDocumentContext::EnumCodeContexts` (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwSourceContext`  
 [in] Le contexte de la source à `IActiveScriptParse::ParseScriptText` ou `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Un décalage relatif au début du texte de script de caractères.  
  
 `uNumChars`  
 [in] Nombre de caractères dans ce contexte.  
  
 `ppescc`  
 [out] Énumérateur des contextes de code dans la plage spécifiée.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Hôtes actifs permet de déléguer le `IDebugDocumentContext::EnumCodeContexts` (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptDebug (Interface)](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)