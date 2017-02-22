---
title: "Exe | Microsoft Docs"
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
  - "fichiers .dll"
  - "symbole Exe"
  - "fichiers .exe"
  - "fichiers exécutables, symbole Exe"
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Exe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

.exe Est le seul symbole sans parent lexicale ou de la classe, comme il représente la portée globale des fichiers .exe ou .DLL.  Il n'existe qu'un symbole avec la balise d' `SymTagExe` par fichier.  La méthode d' [IDiaSession::get\_globalScope](../Topic/IDiaSession::get_globalScope.md) retourne le symbole.  
  
## Propriétés  
 Le tableau suivant indique les propriétés qui sont valides pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|---------------|---------------------|-----------------|  
|[IDiaSymbol::get\_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|Âge de ce fichier exécutable.|  
|[IDiaSymbol::get\_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|`GUID` de ce fichier exécutable.|  
|[IDiaSymbol::get\_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|`TRUE` si le fichier de symboles associé à ce fichier exécutable contient des C \(uniquement dans diamètre Kit de développement logiciel v8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|`TRUE` si les symboles privés ont été supprimés du fichier de symboles associé à ce fichier exécutable \(uniquement dans diamètre Kit de développement logiciel v8.0 ou version ultérieure\).|  
|[IDiaSymbol::get\_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|Évaluez indiquer l'unité centrale cible \(une des valeurs de [CV\_CPU\_TYPE\_e, énumération](../../debugger/debug-interface-access/cv-cpu-type-e.md) \).|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|nom du fichier.exe.|  
|[IDiaSymbol::get\_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|signature du fichier exécutable.|  
|[IDiaSymbol::get\_symbolsFileName](../Topic/IDiaSymbol::get_symbolsFileName.md)|`BSTR`|Chemin d'accès complet du fichier .pdb ou du .dbg du fichier .exe.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d'index de symbole.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retourne `SymTagExe` \(une des valeurs de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) \).|  
  
## Voir aussi  
 [IDiaSession::get\_globalScope](../Topic/IDiaSession::get_globalScope.md)   
 [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)