---
title: "IDiaStackWalker | Microsoft Docs"
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
  - "IDiaStackWalker (interface)"
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaStackWalker
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Fournit des méthodes pour effectuer un parcours de pile à l'aide de les informations du fichier .pdb.  
  
## Syntaxe  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDiaStackWalker`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Récupère un énumérateur du frame de pile pour les plateformes x86.|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Récupère un énumérateur du frame de pile pour un type spécifique de plateforme.|  
  
## Notes  
 Cette interface est utilisée pour obtenir une liste des frames de pile pour un module chargé.  Chacune des méthodes reçoit un objet d' [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) \(implémenté par l'application cliente\) qui fournit les informations nécessaires pour créer la liste des frames de pile.  
  
## Remarques pour les appelants  
 cette interface est obtenue en appelant la méthode d' `CoCreateInstance` avec l'identificateur de classe `CLSID_DiaStackWalker` et l'ID d'interface d' `IID_IDiaStackWalker`.  l'exemple montre comment cette interface est obtenue.  
  
## Exemple  
 cet exemple montre comment obtenir l'interface d' `IDiaStackWalker` .  
  
```cpp#  
  
      IDiaStackWalker* pStackWalker;  
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaStackWalker,  
                              (void**) &pStackWalker);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## Voir aussi  
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)