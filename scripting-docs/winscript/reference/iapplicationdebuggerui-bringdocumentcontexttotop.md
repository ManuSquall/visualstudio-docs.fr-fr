---
title: "IApplicationDebuggerUI::BringDocumentContextToTop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebuggerUI.BringDocumentContextToTop
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebuggerUI::BringDocumentContextToTop"
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI::BringDocumentContextToTop
Apporte la fenêtre contenant le contexte de document donné en haut de l'interface utilisateur du débogueur et fait défiler la fenêtre au contexte.  
  
## Syntaxe  
  
```  
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### Paramètres  
 `pddc`  
 \[in\]  Contexte de document à apporter au début de l'interface utilisateur du débogueur.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_INVALIDARG`|Le contexte spécifié par `pddc` n'est pas connu.|  
  
## Notes  
 Cette méthode apporte la fenêtre contenant le contexte de document donné en haut de l'interface utilisateur du débogueur et fait défiler la fenêtre au contexte.  
  
## Voir aussi  
 [IApplicationDebuggerUI, interface](../../winscript/reference/iapplicationdebuggerui-interface.md)