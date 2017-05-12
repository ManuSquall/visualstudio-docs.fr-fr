---
title: "DebugStackFrameDescriptor, structure | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DebugStackFrameDescriptor
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DebugStackFrameDescriptor (structure)"
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DebugStackFrameDescriptor, structure
Énumère les frames de pile et fusionne la sortie de plusieurs énumérateurs sur le même thread.  
  
## Syntaxe  
  
```  
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## Membres  
 `pdsf`  
 L'objet frame de pile.  
  
 `dwMin`  
 Une représentation d'ordinateur dépendant de l'intervalle inférieur des adresses physiques associé à ce frame de pile.  
  
 `dwLim`  
 Une représentation d'ordinateur dépendant de la plage supérieur des adresses physiques associé à ce frame de pile.  
  
 `fFinal`  
 Réduisez qui indique que le frame est traité.  
  
 `punkFinal`  
 Si ce paramètre n'est pas `NULL`, fusionner actuel d'énumérateur doit s'arrêter et un nouveau doit être démarré.  L'objet indique comment démarrer la nouvelle énumération.  
  
## Notes  
 Le processus de débogage utilise de gestionnaire cette structure de trier les frames de pile plusieurs moteurs de script.  Par convention, les piles développez vers le bas.  Par conséquent, dans les architectures où les piles grandissent, les adresses deux doivent être remplies.  
  
## Voir aussi  
 [Débogueur de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)