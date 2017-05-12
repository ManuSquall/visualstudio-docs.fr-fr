---
title: "IActiveScriptDebug::EnumCodeContextsOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::EnumCodeContextsOfPosition"
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::EnumCodeContextsOfPosition
Utilisé par un hôte intelligent pour déléguer la méthode d' `IDebugDocumentContext::EnumCodeContexts`.  
  
## Syntaxe  
  
```  
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### Paramètres  
 `dwSourceContext`  
 \[in\]  Le contexte de source de la façon prévue à `IActiveScriptParse::ParseScriptText` ou à `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 \[in\]  Au début relatif d'offset de caractères de texte de script.  
  
 `uNumChars`  
 \[in\]  Nombre de caractères dans ce contexte.  
  
 `ppescc`  
 \[out\]  Un énumérateur des contextes de code dans la plage spécifiée.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Les hôtes intelligents utilisez cette méthode pour déléguer la méthode d' `IDebugDocumentContext::EnumCodeContexts` .  
  
## Voir aussi  
 [IActiveScriptDebug, interface](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)