---
title: "CompilandDetails | Microsoft Docs"
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
  - "CompilandDetails (symbole)"
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# CompilandDetails
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les informations de module \(Compiland\) sont fractionnés entre les symboles avec une balise d' `SymTagCompiland` bas \(détails\) et une balise d' `SymTagCompilandDetails` \(spécifiques élevé\).  `SymTagCompilandDetails` nécessite le chargement des symboles supplémentaires.  Toutefois, il fournit une quantité d'informations sur le module qui n'est pas disponible avec un symbole d' `SymTagCompiland` .  
  
## Propriétés  
 Le tableau suivant indique les propriétés qui sont valides pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|---------------|---------------------|-----------------|  
|[IDiaSymbol::get\_backEndBuild](../Topic/IDiaSymbol::get_backEndBuild.md)|`DWORD`|principal numéro de build du compilateur.|  
|[IDiaSymbol::get\_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Principal numéro de version principale du compilateur.|  
|[IDiaSymbol::get\_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|principal numéro de version secondaire du compilateur.|  
|[IDiaSymbol::get\_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nom du compilateur qui a produit ce module \(compiland\) \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_editAndContinueEnabled](../Topic/IDiaSymbol::get_editAndContinueEnabled.md)|`BOOL`|`TRUE` si la modification et Continue ont été activées à la compilation.|  
|[IDiaSymbol::get\_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|numéro de build frontal du compilateur.|  
|[IDiaSymbol::get\_frontEndMajor](../Topic/IDiaSymbol::get_frontEndMajor.md)|`DWORD`|Numéro de version principale frontal du compilateur.|  
|[IDiaSymbol::get\_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|numéro de version secondaire frontal du compilateur.|  
|[IDiaSymbol::get\_hasDebugInfo](../Topic/IDiaSymbol::get_hasDebugInfo.md)|`BOOL`|`TRUE` si ce module contient les informations de débogage \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` si ce module \(compiland\) contient le code managé \(uniquement dans diamètre Kit de développement logiciel v8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` si le module a été compilé avec le commutateur de compilation de [\/GS \(vérification de la sécurité des mémoires tampons\)](/visual-cpp/build/reference/gs-buffer-security-check) \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` si le module a été converti du code de langue \(CIL\) intermédiaire commun en code natif.|  
|[IDiaSymbol::get\_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` si des types définis par l' \(UDT\)utilisateur ont été alignés à une certaine limite spécifiée de mémoire \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_isHotpatchable](../Topic/IDiaSymbol::get_isHotpatchable.md)|`BOOL`|`TRUE` si le module a été compilé avec le commutateur de compilation de [\/hotpatch \(Créer une image corrigeable en mémoire\)](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image) \(uniquement dans diamètre Kit de développement logiciel v8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` si le module a été compilé avec le commutateur de compilation de [\/LTCG \(Génération de code durant l'édition de liens\)](/visual-cpp/build/reference/ltcg-link-time-code-generation) \(uniquement dans diamètre Kit de développement logiciel V8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_isMSILNetmodule](../Topic/IDiaSymbol::get_isMSILNetmodule.md)|`BOOL`|TRUE si le module est un module MSIL \(Microsoft Intermediate langage\) \(uniquement dans diamètre Kit de développement logiciel v8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md)|`DWORD`|langage de code source.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbole pour le module.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID du symbole parent lexicale.|  
|[IDiaSymbol::get\_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Plateforme sur laquelle le module \(compiland\) a été compilé \(une des valeurs de [CV\_CPU\_TYPE\_e, énumération](../../debugger/debug-interface-access/cv-cpu-type-e.md) \).|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d'index de symbole.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retourne `SymTagCompilandDetails` \(une des valeurs de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) \).|  
  
## Notes  
 Les compilateurs se présentent souvent sous une forme appelé un compilateur de en deux étapes ; dans certaines versions du compilateur, chaque série est géré par un programme séparés.  Il s'agit des compilateurs frontaux et principaux, respectivement, par conséquent les propriétés de symboles pour des principaux et frontaux numéros de version.  
  
## Voir aussi  
 [Compiland](../../debugger/debug-interface-access/compiland.md)   
 [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)