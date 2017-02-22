---
title: "LocationType | Microsoft Docs"
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
  - "LocationType (énumération)"
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# LocationType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Indique le type d'informations sur l'emplacement contenu dans un symbole.  
  
## Syntaxe  
  
```cpp#  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## Éléments  
 `LocIsNull`  
 Les informations sur l'emplacement sont pas disponibles.  
  
 `LocIsStatic`  
 l'emplacement est statique.  
  
 `LocIsTLS`  
 l'emplacement est en stock le stockage local des threads.  
  
 `LocIsRegRel`  
 l'emplacement est registre\-parent.  
  
 `LocIsThisRel`  
 l'emplacement est `this`\- parent.  
  
 `LocIsEnregistered`  
 l'emplacement est dans un registre.  
  
 `LocIsBitField`  
 l'emplacement est dans un champ de bits.  
  
 `LocIsSlot`  
 L'emplacement est un emplacement de Microsoft Intermediate langage \(MSIL\).  
  
 `LocIsIlRel`  
 l'emplacement est MSIL\-parent.  
  
 `LocInMetaData`  
 L'emplacement se trouve dans les métadonnées.  
  
 `LocIsConstant`  
 L'emplacement est dans une valeur de constante.  
  
 `LocTypeMax`  
 Le numéro d'emplacement dans cette énumération.  
  
## Notes  
 les propriétés disponibles à l'interface d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) dépendent de l'emplacement du symbole dans le fichier image.  Pour plus d'informations, consultez [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Les valeurs de cette énumération sont retournées par un appel à la méthode d' [IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md) .  
  
## Configuration requise  
 en\-tête : cvconst.h  
  
## Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)   
 [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md)