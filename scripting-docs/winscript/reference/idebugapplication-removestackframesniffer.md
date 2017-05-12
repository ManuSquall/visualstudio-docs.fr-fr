---
title: "IDebugApplication::RemoveStackFrameSniffer | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.RemoveStackFrameSniffer
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::RemoveStackFrameSniffer"
ms.assetid: 00304b88-e435-4b87-a331-44e7492eb32d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::RemoveStackFrameSniffer
Supprime un fournisseur d'énumérateur du frame de pile de cette application.  
  
## Syntaxe  
  
```  
HRESULT RemoveStackFrameSniffer(  
   DWORD  dwCookie  
);  
```  
  
#### Paramètres  
 `dwCookie`  
 \[in\]  Le cookie retourné par la méthode d' `AddStackFrameSniffer` lorsque le fournisseur d'énumérateur du frame de pile a été ajouté.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 La méthode d' `RemoveStackFrameSniffer` supprime un fournisseur d'énumérateur du frame de pile de cette application.  
  
## Voir aussi  
 [IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)   
 [IDebugApplication, interface](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugStackFrameSniffer, interface](../../winscript/reference/idebugstackframesniffer-interface.md)