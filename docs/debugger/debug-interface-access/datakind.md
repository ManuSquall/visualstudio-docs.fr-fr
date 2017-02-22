---
title: "DataKind | Microsoft Docs"
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
  - "DataKind (énumération)"
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DataKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

indique la portée particulière d'une valeur de données.  
  
## Syntaxe  
  
```cpp#  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## Éléments  
 DataIsUnknown  
 le symbole de données ne peut pas être déterminé.  
  
 DataIsLocal  
 l'élément de données est une variable locale.  
  
 DataIsStaticLocal  
 l'élément de données est une variable locale statique.  
  
 DataIsParam  
 l'élément de données est un paramètre formel.  
  
 DataIsObjectPtr  
 l'élément de données est un pointeur d'objet \(`this`\).  
  
 DataIsFileStatic  
 l'élément de données est une variable de fichier\-scoped.  
  
 DataIsGlobal  
 l'élément de données est une variable globale.  
  
 DataIsMember  
 L'élément de données est une variable membre objet.  
  
 DataIsStaticMember  
 L'élément de données est une variable statique de la classe.  
  
 DataIsConstant  
 l'élément de données est une valeur de constante.  
  
## Notes  
 Les valeurs de cette énumération sont retournées par la méthode d' [IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) .  
  
## Configuration requise  
 en\-tête : cvconst.h  
  
## Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)