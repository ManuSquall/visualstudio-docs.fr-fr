---
title: "Compiland | Microsoft Docs"
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
  - "compiland, symbole"
  - "compilands, symbole de compiland"
ms.assetid: c798eb2b-664a-41ec-ae90-5e9d292507ca
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Compiland
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il existe un symbole d' `SymTagCompiland` pour chaque module \(Compiland\) lié au fichier .exe.  Les informations de module \(Compiland\) sont fractionnés entre les symboles avec une balise d' `SymTagCompiland` , qui peut être récupérée sans charger des symboles supplémentaires de module \(compiland\), et les symboles avec une balise d' `SymTagCompilandDetails` , qui peut nécessiter charger des symboles supplémentaires.  
  
## Propriétés  
 Le tableau suivant indique les propriétés qui sont valides pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|---------------|---------------------|-----------------|  
|[IDiaSymbol::get\_editAndContinueEnabled](../Topic/IDiaSymbol::get_editAndContinueEnabled.md)|`BOOL`|`TRUE` si la modification et Continue ont été activées à la compilation.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|symbole pour le fichier.exe.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID du symbole parent lexicale.|  
|[IDiaSymbol::get\_libraryName](../Topic/IDiaSymbol::get_libraryName.md)|`BSTR`|nom de la bibliothèque ou du fichier objet d'où l'objet a été chargé.|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|Nom du fichier objet du module \(compiland\).|  
|[IDiaSymbol::get\_sourceFileName](../Topic/IDiaSymbol::get_sourceFileName.md)|`BSTR`|nom du fichier source.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d'index de symbole.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retourne `SymTagCompiland` \(une des valeurs de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) \).|  
  
## Voir aussi  
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)   
 [CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)   
 [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)