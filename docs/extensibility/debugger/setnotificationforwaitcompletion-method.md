---
title: "SetNotificationForWaitCompletion (m&#233;thode) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SetNotificationForWaitCompletion (méthode), la classe de tâche [moteurs de débogage .NET Framework]"
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# SetNotificationForWaitCompletion (m&#233;thode)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Active ou désactive le bit d'état TASK\_STATE\_WAIT\_COMPLETION\_NOTIFICATION.  
  
 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib \(dans mscorlib.dll\)  
  
## Syntaxe  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### Paramètres  
 `enabled`  
  
 `true` Pour définir le bit ; `false` à annuler le bit.  
  
## Exceptions  
  
## Notes  
 Le débogueur définit ce bit pour aider à pas sortant d'un corps de méthode asynchrone. Si `enabled` est `true`, cette méthode doit être appelée uniquement sur une tâche qui n'est pas encore terminée. Si `enabled` est `false`, cette méthode peut être appelée sur des tâches terminées. Dans les deux cas, il doit uniquement être utilisé pour les tâches de la promesse de style.  
  
## Configuration requise  
  
## Voir aussi  
 [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)