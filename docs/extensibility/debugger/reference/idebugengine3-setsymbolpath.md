---
title: "IDebugEngine3::SetSymbolPath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::SetSymbolPath"
helpviewer_keywords: 
  - "IDebugEngine3::SetSymbolPath"
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Définit le chemin d'accès ou le chemin d'accès qui se trouvent les symboles de débogage.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```c#  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`szSymbolSearchPath`|\[in\]  Chaîne contenant le chemin de recherche ou le chemin d'accès du symbole.  Consultez « notes » pour plus de détails.  Ne peut pas avoir la valeur Null.|  
|`szSymbolCachePath`|\[in\]  Chaîne contenant le chemin d'accès local où les symboles peuvent être mis en cache.  Ne peut pas avoir la valeur Null.|  
|`Flags`|\[in\]  non utilisé ; toujours la valeur 0.|  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon retourne un code d'erreur.  
  
## Notes  
 La chaîne`szSymbolSearchPath` est une liste d'un ou plusieurs chemins d'accès, séparés par des points\-virgules, pour rechercher des symboles.  Ces chemins d'accès peuvent être un chemin local, un chemin d'accès de style UNC, ou une URL.  Ces chemins d'accès peuvent également être une combinaison de types différents.  Si le chemin d'accès est UNC \(par exemple, \\\\Symserver\\Symbols\), le moteur de débogage doit déterminer si le chemin d'accès est sur un serveur de symboles et peut charger des symboles de ce serveur, les mettre en cache dans le chemin d'accès spécifié par `szSymbolCachePath`.  
  
 le chemin d'accès aux symboles peut également contenir un ou plusieurs emplacements du cache.  Les mises en cache sont répertoriés par ordre de priorité, pour le cache est la plus élevée d'abord, et par séparés \* les symboles.  Par exemple :  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 La méthode d' [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) exécute la charge réelle des symboles.  
  
## Voir aussi  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)