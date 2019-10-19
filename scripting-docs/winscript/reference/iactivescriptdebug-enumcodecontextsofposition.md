---
title: 'IActiveScriptDebug :: EnumCodeContextsOfPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: aedfe5d40d8f4086e30f3a62c070b8ccd5ef2388
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572785"
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Utilisé par un hôte intelligent pour déléguer la méthode `IDebugDocumentContext::EnumCodeContexts`.  
  
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
 dans Contexte source fourni à `IActiveScriptParse::ParseScriptText` ou `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 dans Décalage de caractère par rapport au début du texte du script.  
  
 `uNumChars`  
 dans Nombre de caractères dans ce contexte.  
  
 `ppescc`  
 à Énumérateur des contextes de code dans la plage spécifiée.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Les hôtes intelligents utilisent cette méthode pour déléguer la méthode `IDebugDocumentContext::EnumCodeContexts`.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)  
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)