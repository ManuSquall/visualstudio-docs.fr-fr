---
title: "IDiaStackWalkHelper | Microsoft Docs"
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
  - "IDiaStackWalkHelper2 (interface)"
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IDiaStackWalkHelper
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Facilitates parcours de la pile à l'aide de le fichier de base de données de débogage du programme \(.pdb\).  
  
## Syntaxe  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## méthodes en commande de VTable  
 Le tableau ci\-dessous répertorie les méthodes d' `IDiaStackWalkHelper`:  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaStackWalkHelper::get\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|extrait la valeur d'un registre.|  
|[IDiaStackWalkHelper::put\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|définit la valeur d'un registre.|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Lit un bloc de données de l'image du fichier exécutable en mémoire.|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|recherche le frame de pile spécifié pour l'adresse de retour de fonction la plus proche.|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../Topic/IDiaStackWalkHelper::searchForReturnAddressStart.md)|Recherche le frame de pile spécifié pour une adresse de retour ou près de l'adresse spécifiée de pile.|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Récupère le frame de pile qui contient l'adresse virtuelle spécifiée.|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Récupère le symbole qui contient l'adresse virtuelle spécifiée. **Note:**  le symbole doit avoir le type `SymTagFunctionType` \(une valeur de l'énumération de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Retourne le bloc de données de PDATA associé à l'adresse virtuelle spécifiée.|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Récupère l'adresse virtuelle de départ d'un exécutable, selon une adresse virtuelle trouve dans l'espace mémoire du fichier exécutable.|  
  
## Notes  
 Cette interface est appelée par du code d'un diamètre pour obtenir des informations sur le fichier exécutable pour construire une liste des frames de pile pendant l'exécution du programme.  
  
## Remarques pour les appelants  
 Une application cliente implémente cette interface pour prendre en charge la parcourt la pile pendant l'exécution du programme.  une instance de cette interface est passée aux méthodes d' [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) ou d' [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) .  
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## Voir aussi  
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)