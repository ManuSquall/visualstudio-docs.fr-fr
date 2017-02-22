---
title: "IDiaSymbol::get_baseType | Microsoft Docs"
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
  - "IDiaSymbol::get_baseType (méthode)"
ms.assetid: 5c69a241-a8d3-48ed-8b36-27463a196572
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaSymbol::get_baseType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le type de base pour ce symbole*.*  
  
## Syntaxe  
  
```cpp#  
HRESULT get_baseType (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne une valeur de l'énumération de [BasicType, énumération](../../debugger/debug-interface-access/basictype.md) spécifiant le type de base du symbole.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Notes  
 Le type de base pour un symbole peut être déterminé en obtenant d'abord le type du symbole et en interrogeant après cela type retourné pour le type de base.  Notez que certains symboles ne peut pas avoir de base \(en date, par exemple un nom de structure.  
  
## Exemple  
  
```cpp#  
IDiaSymbol* pType;  
CComPtr<IDiaSymbol> pBaseType;  
if (pType->get_type( &pBaseType ) == S_OK)  
{  
    BasicType btBaseType;  
    if (pBaseType->get_baseType((DWORD *)&btBaseType) == S_OK)  
    {  
        // Do something with basic type.  
    }  
}  
```  
  
## Configuration requise  
  
|Spécification|Description|  
|-------------------|-----------------|  
|en\-tête :|dia2.h|  
|version :|diamètre Kit de développement logiciel v7.0|  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [BasicType, énumération](../../debugger/debug-interface-access/basictype.md)   
 [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)