---
title: "IDiaSession::findChildren | Microsoft Docs"
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
  - "IDiaSession::findChildren (méthode)"
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère tous les enfants d'un identificateur parent spécifié qui correspondent au nom et le type de symbole.  
  
## Syntaxe  
  
```cpp#  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Paramètres  
 `parent`  
 \[in\]  un objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) représentant le parent.  Si ce symbole parent est une fonction, module, ou bloc, ses enfants lexicales sont retournés dans `ppResult`.  Si le symbole parent est un type, ses enfants de classe sont retournés.  Si ce paramètre est `NULL`, alors `symtag` doit être défini à `SymTagExe` ou à `SymTagNull`, qui retourne la portée globale \(fichier .exe\).  
  
 `symtag`  
 \[in\]  Spécifie l'indicateur de symbole des enfants à récupérer.  Les valeurs sont récupérées l'énumération de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) .  Affectez à `SymTagNull` pour récupérer tous les enfants.  
  
 `name`  
 \[in\]  Spécifie le nom des enfants à récupérer.  Affectez à `NULL` pour que tous les enfants soient extraits.  
  
 `compareFlags`  
 \[in\]  Spécifie des options de comparaison appliquées pour nommer la correspondance.  Les valeurs de l'énumération de [NameSearchOptions, énumération](../../debugger/debug-interface-access/namesearchoptions.md) peuvent être utilisées seul ou en association.  
  
 `ppResult`  
 \[out\]  Retourne un objet d' [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) qui contient la liste des symboles enfants récupérés.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Exemple  
 l'exemple suivant montre comment rechercher des variables locales de fonction `pFunc` que nom `szVarName`de correspondance.  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## Voir aussi  
 [Vue d’ensemble](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions, énumération](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)