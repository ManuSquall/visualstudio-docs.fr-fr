---
title: "IDebugEngine3::LoadSymbols | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::LoadSymbols"
helpviewer_keywords: 
  - "IDebugEngine3::LoadSymbols"
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugEngine3::LoadSymbols
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Charge \(si nécessaire\) des symboles pour tous les modules débogué par ce moteur de débogage.  
  
## Syntaxe  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```c#  
int LoadSymbols();  
```  
  
#### Paramètres  
 Aucun  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon retourne un code d'erreur.  
  
## Notes  
 Cette opération permet de charger des symboles de débogage pour tous les modules référencés par le moteur de débogage.  Les symboles sont chargés uniquement s'ils n'ont pas été déjà chargés.  Les symboles sont accessibles dans les chemins d'accès définis par un appel à [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).  
  
## Voir aussi  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)