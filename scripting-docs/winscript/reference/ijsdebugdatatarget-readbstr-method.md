---
title: "IJsDebugDataTarget::ReadBSTR, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadBSTR
apilocation: jscript9diag.dll
ms.assetid: 4b571db7-04b9-42a0-9a3e-310ac9d0e659
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadBSTR, m&#233;thode
Lit un BSTR à partir de la cible de débogage.  
  
## Syntaxe  
  
```  
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### Paramètres  
 `address`  
 \[in\] Adresse à partir de laquelle lire.  
  
 `pString`  
 \[out\] Données BSTR lues dans la cible de débogage.  
  
## Valeur de retour  
  
## Notes  
 Retourne E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS si l'adresse n'est pas valide.  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebugDataTarget, interface](../../winscript/reference/ijsdebugdatatarget-interface.md)