---
title: "JsDebugReadMemoryFlags, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JsDebugReadMemoryFlags
apilocation: jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsDebugReadMemoryFlags, &#233;num&#233;ration
Indicateurs pour spécifier le comportement pendant la lecture de la mémoire.  
  
## Syntaxe  
  
```  
enum JsDebugReadMemoryFlags  
{  
   None = 0,  
   JsDebugAllowPartialRead= 0x1  
} JsDebugReadMemoryFlags;  
```  
  
## Membres  
  
### Valeurs  
  
|Nom|Description|  
|---------|-----------------|  
|`JsDebugAllowPartialRead`|Indique que l'appelant souhaite que l'opération de lecture réussisse si seule une partie de la lecture de la mémoire a réussi.  Si cette valeur est définie, une erreur E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS est levée uniquement si l'adresse n'est pas valide.  Si cet indicateur est désactivé, une erreur E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS est levée si une partie de la mémoire demandée était illisible.|  
|`None`|Indique que l'appelant souhaite le comportement par défaut pour ReadMemory.|  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [Interfaces Windows Script, référence](../../winscript/reference/windows-script-interfaces-reference.md)