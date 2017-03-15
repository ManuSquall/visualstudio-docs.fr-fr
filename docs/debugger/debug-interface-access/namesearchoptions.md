---
title: "NameSearchOptions | Microsoft Docs"
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
  - "NameSearchOptions (énumération)"
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# NameSearchOptions
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Spécifie les options de recherche pour le symbole et les noms de fichiers.  
  
## Syntaxe  
  
```cpp#  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## Éléments  
 `nsNone`  
 Aucune option n'est spécifiée.  
  
 `nsfCaseSensitive`  
 Applique une correspondance respecte la casse de nom.  
  
 `nsfCaseInsensitive`  
 Applique une correspondance respecte la casse de nom.  
  
 `nsfFNameExt`  
 Les noms de traite comme des chemins d'accès et applique une correspondance de nom de filename.ext.  
  
 `nsfRegularExpression`  
 Applique une correspondance respecte la casse de nom en utilisant l'astérisque \(\*\) et des points d'interrogation \(?\) comme caractère générique.  
  
 `nsfUndecoratedName`  
 S'applique uniquement aux symboles qui ont des noms non décorés et décorés.  
  
## Notes  
 les valeurs de cette énumération sont passées aux méthodes suivantes :  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## Configuration requise  
 en\-tête : dia2.h  
  
## Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)