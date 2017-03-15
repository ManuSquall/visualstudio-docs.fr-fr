---
title: "DiaAddressMapEntry | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DiaAddressMapEntry (énumération)"
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

décrit une entrée dans une configuration d'adresse.  
  
## Syntaxe  
  
```cpp#  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## Éléments  
 `rva`  
 une adresse virtuelle relative \(RVA\) dans l'image A.  
  
 `rvaTo`  
 Adresse virtuelle relative `rva` est mappée à dans l'image B.  
  
## Notes  
 Une configuration d'adresse fournit une interprétation d'une disposition de l'image \(a\) à un autre \(b\).  Un tableau de structures d' `DiaAddressMapEntry` triées par `rva` définit une configuration d'adresse.  
  
 Pour convertir une adresse, `addrA`, dans l'image à une adresse, `addrB`, dans l'image B, effectuez les étapes suivantes :  
  
1.  Recherchez la carte pour l'entrée, `e`, avec plus grand `rva` inférieure ou égale à `addrA`.  
  
2.  définissez `delta = addrA – e.rva`.  
  
3.  définissez `addrB = e.rvaTo + delta`.  
  
 Un tableau de structures d' `DiaAddressMapEntry` est passé à la méthode d' [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .  
  
## Configuration requise  
 en\-tête : dia2.h  
  
## Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)