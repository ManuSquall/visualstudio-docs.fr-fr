---
title: "IDebugDocumentHelper::SetTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetTextAttributes
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetTextAttributes"
ms.assetid: 31657738-9e4c-436a-be61-23f4185d452e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetTextAttributes
Définit les attributs sur une plage de texte, et d'autres attributs sur ce texte.  
  
## Syntaxe  
  
```  
HRESULT SetTextAttributes(  
   ULONG              ulCharOffset,  
   ULONG              cChars,  
   SOURCE_TEXT_ATTR*  pstaTextAttr  
);  
```  
  
#### Paramètres  
 `ulCharOffset`  
 \[in\]  l'emplacement du début de la plage de texte.  
  
 `cChars`  
 \[in\]  Le nombre de caractères de la plage.  
  
 `pstaTextAttr`  
 \[in\]  Les attributs de texte source pour la plage de texte.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Il est erroné d'appeler `SetTextAttributes` sur une plage de texte avant que le texte est ajouté au document.  Appelez `AddDBCSText`, `AddUnicodeText`, ou les méthodes d' `AddDeferredText` pour ajouter du texte au document.  
  
## Voir aussi  
 [IDebugDocumentHelper, interface](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE\_TEXT\_ATTR, énumération](../../winscript/reference/source-text-attr-enumeration.md)