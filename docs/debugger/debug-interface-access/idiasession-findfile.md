---
title: "IDiaSession::findFile | Microsoft Docs"
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
  - "IDiaSession::findFile (méthode)"
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::findFile
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère les fichiers sources par le module et le nom.  
  
## Syntaxe  
  
```cpp#  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### Paramètres  
 `pCompiland`  
 \[in\]  Un objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) représentant le module à utiliser comme contexte de la recherche.  Affectez à ce paramètre la `NULL` pour rechercher des fichiers sources dans tous les modules \(compilands\).  
  
 `name`  
 \[in\]  Spécifie le nom du fichier source à récupérer.  Affectez à ce paramètre la `NULL` pour que tous les fichiers sources sont récupérés.  
  
 `option`  
 \[in\]  spécifie les options de comparaison appliquées pour nommer rechercher.  Les valeurs de l'énumération de [NameSearchOptions, énumération](../../debugger/debug-interface-access/namesearchoptions.md) peuvent être utilisées unique ou en association.  
  
 `ppResult`  
 \[out\]  Retourne un objet d' [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) qui contient une liste des fichiers sources récupérés.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## Exemple  
  
```cpp#  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## Voir aussi  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions, énumération](../../debugger/debug-interface-access/namesearchoptions.md)