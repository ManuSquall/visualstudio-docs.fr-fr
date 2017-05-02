---
title: "IDebugApplication::AddStackFrameSniffer | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.AddStackFrameSniffer
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::AddStackFrameSniffer"
ms.assetid: a7a9684a-14c5-415a-ae63-a17397d58d07
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::AddStackFrameSniffer
Ajoute un fournisseur d'énumérateur du frame de pile à cette application.  
  
## Syntaxe  
  
```  
HRESULT AddStackFrameSniffer(  
   IDebugStackFrameSniffer*  pdsfs,  
   DWORD*                    pdwCookie  
);  
```  
  
#### Paramètres  
 `pdsfs`  
 \[in\]  Le fournisseur d'énumérateur du frame de pile à ajouter à cette application.  
  
 `pdwCookie`  
 \[out\]  Un cookie utilisé pour supprimer ce fournisseur d'énumérateur du frame de pile de l'application.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Bien que les moteurs de langages appellent généralement cette méthode pour exposer leurs frames de pile au débogueur, il est possible que d'autres entités exposent des frames de pile.  
  
## Voir aussi  
 [IDebugApplication, interface](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)   
 [IDebugStackFrameSniffer, interface](../../winscript/reference/idebugstackframesniffer-interface.md)