---
title: "IActiveScriptSiteDebug::GetDocumentContextFromPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetDocumentContextFromPosition
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetDocumentContextFromPosition"
ms.assetid: ba5f7348-0107-4b12-b949-79a012476cf7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetDocumentContextFromPosition
Utilisé par le moteur de langue à déléguer `IDebugCodeContext::GetSourceContext`.  
  
## Syntaxe  
  
```  
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### Paramètres  
 `dwSourceContext`  
 \[in\]  Le contenu source de la façon prévue à `ParseScriptText` ou à `AddScriptlet`.  
  
 `uCharacterOffset`  
 \[in\]  Au début relatif d'offset de caractère de bloc de script ou de scriptlet.  
  
 `uNumChars`  
 \[in\]  Nombre de caractères dans ce contexte.  
  
 `ppsc`  
 \[out\]  le contexte de document correspondant à cet intervalle de caractère\-position.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Les moteurs de langage utilisez cette méthode pour déléguer `IDebugCodeContext::GetSourceContext`.  
  
## Voir aussi  
 [IActiveScriptSiteDebug, interface](../../winscript/reference/iactivescriptsitedebug-interface.md)