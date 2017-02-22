---
title: "IDiaSession::findInjectedSource | Microsoft Docs"
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
  - "IDiaSession::findInjectedSource (méthode)"
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSession::findInjectedSource
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une liste des sources placée dans le magasin de symboles par les fournisseurs d'attribut ou d'autres composants du processus de compilation.  
  
## Syntaxe  
  
```cpp#  
HRESULT findInjectedSource (   
   LPCOLESTR                 srcFile,  
   IDiaEnumInjectedSources** ppResult  
);  
```  
  
#### Paramètres  
 srcFile  
 \[in\]  Nom du fichier source pour lequel le recherche.  
  
 ppResult  
 \[out\]  Retourne un objet d' [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) qui contient une liste de toutes les sources injectées.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)