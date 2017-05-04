---
title: "IEnumJsStackFrames, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IEnumJsStackFrames, interface
Implémenté par le débogueur pour fournir une fonction de désempilage à jscript9diag.dll pour JavaScript.  
  
## Syntaxe  
  
```  
IEnumJsStackFrames : public IUnknown;  
```  
  
## Membres  
  
### Méthodes publiques  
  
|Nom|Description|  
|---------|-----------------|  
|[IEnumJsStackFrames::Next, méthode](../../winscript/reference/ienumjsstackframes-next-method.md)|Obtient le nombre spécifié de frames.|  
|[IEnumJsStackFrames::Reset, méthode](../../winscript/reference/ienumjsstackframes-reset-method.md)|Réinitialise le frame de pile à la position avant le premier élément.|  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [Interfaces Windows Script, référence](../../winscript/reference/windows-script-interfaces-reference.md)