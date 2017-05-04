---
title: "IApplicationDebuggerUI::BringDocumentToTop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebuggerUI.BringDocumentToTop
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebuggerUI::BringDocumentToTop"
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI::BringDocumentToTop
Apporte la fenêtre contenant le spécifié de débogage le document vers le haut dans l'interface utilisateur du débogueur.  
  
## Syntaxe  
  
```  
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### Paramètres  
 `pddt`  
 \[in\]  Déboguez le document pour apporter au début de l'interface utilisateur du débogueur.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_INVALIDARG`|Le document n'est pas connu.|  
  
## Notes  
 Cette méthode apporte la fenêtre contenant le spécifié de débogage le document vers le haut dans l'interface utilisateur du débogueur.  
  
## Voir aussi  
 [IApplicationDebuggerUI, interface](../../winscript/reference/iapplicationdebuggerui-interface.md)