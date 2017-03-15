---
title: "Fonction (Kit de d&#233;veloppement logiciel de Debug&#160;Interface&#160;Access) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "symbole de fonction"
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fonction (Kit de d&#233;veloppement logiciel de Debug&#160;Interface&#160;Access)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

chaque fonction est identifiée par un symbole d' `SymTagFunction` .  
  
## Propriétés  
 Le tableau suivant indique les propriétés qui sont valides pour ce type de symbole.  
  
|Propriété|`Data type`|Description|  
|---------------|-----------------|-----------------|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|L'une des valeurs de [CV\_access\_e, énumération](../../debugger/debug-interface-access/cv-access-e.md), si la fonction est une fonction membre.|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Partie décalée d'emplacement ; pour plus d'informations, consultez [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Élément de section d'emplacement ; pour plus d'informations, consultez [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|symbole pour la classe, si la fonction est une fonction membre.|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|ID du symbole de parent de classe.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` si la fonction est marquée comme constante.|  
|[IDiaSymbol::get\_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` si la fonction utilise une convention d'appel personnalisée \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` si la fonction effectue loin un de retour \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_hasAlloca](../Topic/IDiaSymbol::get_hasAlloca.md)|`BOOL`|`TRUE` si la fonction utilise la fonction de mémoire allouée \(uniquement diamètre Kit de développement logiciel V8.0 d'uinnder ou version ultérieure\).|  
|[IDiaSymbol::get\_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|`TRUE` si la fonction contient la gestion des exceptions de style C\+\+ \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_hasEHa](../Topic/IDiaSymbol::get_hasEHa.md)|`BOOL`|`TRUE` si la fonction contient la gestion des exceptions asynchrone \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|`TRUE` si la fonction contient l'assembly inline \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|`TRUE` si la fonction contient un appel de [longjmp](/visual-cpp/c-runtime-library/reference/longjmp) \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` si la fonction contient des vérifications de sécurité \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|`TRUE` si la fonction contient la gestion structurée des exceptions de style Win32 \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|`TRUE` si la fonction contient un appel de [setjmp](/visual-cpp/c-runtime-library/reference/setjmp) \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` si la fonction a un retour de l'interruption \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|`TRUE` si une fonction est introduction virtuelle.|  
|[IDiaSymbol::get\_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|`TRUE` si la fonction était marquée avec un des attributs d' [inline, \_\_inline, \_\_forceinline](../../misc/inline-inline-forceinline.md) .|  
|[IDiaSymbol::get\_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|`TRUE` si la fonction est marquée avec l'attribut de [naked](/visual-cpp/cpp/naked-cpp) \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` si la fonction est statique \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Nombre d'octets du code de fonction, à partir de l'emplacement.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbole du module englobant.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID du symbole parent lexicale.|  
|[IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)|`DWORD`|Les fonctions peuvent avoir des emplacements de statiques ou de métadonnées ; pour plus d'informations, consultez [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|Nom de la fonction.|  
|[IDiaSymbol::get\_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` si la fonction n'est pas une fonction inline \(uniquement diamètre Kit de développement logiciel V8.0 de n ou version ultérieure\).|  
|[IDiaSymbol::get\_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` si la fonction n'est pas accessible \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` si la fonction ne retourne pas de valeur \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_noStackOrdering](../Topic/IDiaSymbol::get_noStackOrdering.md)|`BOOL`|`TRUE` si la fonction est compilée avec des contrôles de sécurité de la mémoire tampon mais aucun classement de pile peut être effectuée.|  
|[IDiaSymbol::get\_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` si le code contient les informations de débogage pour le code optimisé uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|`TRUE` si la fonction est virtuelle pure.|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|position relative de cette fonction dans son module.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d'index de symbole.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retourne `SymTagFunction` \(une des valeurs de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|jeton de métadonnées pour la fonction.|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|symbole pour la signature de la fonction.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID du symbole de type.|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` si la fonction est non alignée.|  
|[IDiaSymbol::get\_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|La forme non décorée du nom de la fonction \(uniquement dans diamètre Kit de développement logiciel v8.0 ou version ultérieure\)|  
|[IDiaSymbol::get\_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|Partie ou la totalité forme non décorée du nom de la fonction \(uniquement dans diamètre Kit de développement logiciel v8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` si une fonction virtuelle.|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|position de cette fonction dans l'image exécutable.|  
|[IDiaSymbol::get\_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|si une fonction virtuelle, puis l'offset dans la table de fonctions virtuelles.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` si la fonction est marquée comme volatile.|  
  
## Voir aussi  
 [CV\_access\_e, énumération](../../debugger/debug-interface-access/cv-access-e.md)   
 [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)   
 [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md)