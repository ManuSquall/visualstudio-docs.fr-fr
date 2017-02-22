---
title: "FuncDebugStart | Microsoft Docs"
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
  - "FuncDebugStart (symbole)"
  - "déboguer [DIA SDK], point de départ"
ms.assetid: 1cbc6ca5-87d0-4c30-a39e-0a9dc62ce1a9
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# FuncDebugStart
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Si une fonction est un point défini auquel le débogage doit démarrer, ce point est identifié par un symbole avec une balise d' `SymTagFuncDebugStart` .  
  
## Propriétés  
 Le tableau suivant indique les propriétés qui sont valides pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|---------------|---------------------|-----------------|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Partie décalée d'emplacement ; pour plus d'informations, consultez [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Élément de section d'emplacement ; pour plus d'informations, consultez [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` si la fonction utilise une convention d'appel personnalisée \(uniquement dans diamètre Kit de développement logiciel v8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` si la fonction effectue loin un de retour \(uniquement dans diamètre Kit de développement logiciel v8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` si la fonction contient un retour de l'interruption \(uniquement dans diamètre Kit de développement logiciel v8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` si la fonction est marquée comme static \(uniquement dans diamètre Kit de développement logiciel v8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|symbole pour la fonction englobante.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID du symbole parent lexicale.|  
|[IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)|`DWORD`|les points de départ ont des emplacements statiques ; pour plus d'informations, consultez [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get\_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` si la fonction était spécifiée avec l'attribut de [noinline](/visual-cpp/cpp/noinline) \(uniquement dans diamètre Kit de développement logiciel v8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` si la fonction était spécifiée avec l'attribut de [noreturn](/visual-cpp/cpp/noreturn) \(uniquement dans diamètre Kit de développement logiciel v8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` si la fonction n'est jamais appelée \(uniquement dans diamètre Kit de développement logiciel v8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Offset de symbole en mémoire ; pour plus d'informations, consultez [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel`.|  
|[IDiaSymbol::get\_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` si le code contient les informations de débogage pour le code optimisé uniquement dans diamètre Kit de développement logiciel v8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Position relative de la fonction dans le bloc.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d'index de symbole.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retourne `SymTagFuncDebugStart` \(une des valeurs de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|position de la fonction dans le fichier exécutable.|  
  
## Voir aussi  
 [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)   
 [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md)