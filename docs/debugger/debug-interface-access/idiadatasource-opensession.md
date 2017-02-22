---
title: "IDiaDataSource::openSession | Microsoft Docs"
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
  - "IDiaDataSource::openSession (méthode)"
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ouvre une session pour interroger des symboles.  
  
## Syntaxe  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### Paramètres  
 ppSession  
 \[out\]  Retourne un objet d' [IDiaSession](../../debugger/debug-interface-access/idiasession.md) représentant la séance publique.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Le tableau suivant montre les valeurs de retour possibles de cette méthode.  
  
|Valeur|Description|  
|------------|-----------------|  
|E\_UNEXPECTED|L'objet d' [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) n'a pas déjà été initialisé avec une source de symboles.|  
|E\_INVALIDARG|Paramètre non valide d' `ppSession` .|  
|E\_OUTOFMEMORY|mémoire insuffisante pour ouvrir la session.|  
  
## Notes  
 cette méthode ouvre un objet d' [IDiaSession](../../debugger/debug-interface-access/idiasession.md) pour une source de données.  
  
 les objets d'`IDiaSession` implémentent des requêtes dans la source de données.  Une session gère un espace d'adressage pour chaque jeu de symboles de débogage.  Si le fichier .exe ou .DLL décrit par les symboles de source de données est actif dans des plages à plusieurs adresses \(par exemple, car plusieurs processus l'a chargé\), une session pour chaque plage d'adresses doit être utilisée.  
  
## Exemple  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## Voir aussi  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Vue d’ensemble](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Interrogation du fichier .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)