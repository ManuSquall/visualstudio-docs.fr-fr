---
title: "NotifyDebuggerOfWaitCompletion (m&#233;thode) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "NotifyDebuggerOfWaitCompletion (méthode), la classe de tâche [moteurs de débogage .NET Framework]"
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# NotifyDebuggerOfWaitCompletion (m&#233;thode)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Méthode d'espace réservé utilisé comme cible de point d'arrêt par le débogueur. Cette méthode ne doit pas être incorporées ou optimisé.  
  
 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib \(dans mscorlib.dll\)  
  
## Syntaxe  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## Notes  
 Toutes les opérations de jointure avec une tâche doivent appeler cette méthode si leur bit de notification de débogueur est défini.  
  
## Configuration requise  
  
## Voir aussi  
 [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)