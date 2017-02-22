---
title: "IDiaSymbol::get_addressSection | Microsoft Docs"
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
  - "IDiaSymbol::get_addressSection (méthode)"
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_addressSection
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait la partie de section d'un emplacement d'adresse.  Utilisez lorsque [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md) est défini à `LocIsStatic`.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  retourne la pièce de section d'un emplacement d'adresse.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Notes  
 Pour les membres statiques situés dans une DLL externe, la section retournée par cette méthode peut être 0 pendant que cette méthode s'appuie sur l'obtention de l'adresse virtuelle du membre.  Les adresses virtuelles sont valides uniquement si la méthode d' [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) dans l'interface d' [IDiaSession](../../debugger/debug-interface-access/idiasession.md) a été appelée avec un paramètre différent de zéro spécifiant l'adresse de chargement de la DLL.  
  
 Pour obtenir la partie d'offset d'adresse, appelez la méthode d' [IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) .  
  
## Configuration requise  
  
|Spécification|Description|  
|-------------------|-----------------|  
|en\-tête :|dia2.h|  
|version :|diamètre Kit de développement logiciel v7.0|  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)