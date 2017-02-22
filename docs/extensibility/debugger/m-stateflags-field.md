---
title: "m_stateFlags champ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "champ m_stateFlags, classe de tâche [moteurs de débogage .NET Framework]"
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# m_stateFlags champ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Stocke des informations sur l’état actuel de la <xref:System.Threading.Tasks.Task> objet.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib \(dans mscorlib.dll\)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language \(CIL\).  
  
## Syntaxe  
  
```  
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags  
```  
  
## Notes  
 Vous utilisez généralement le <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> propriété pour accéder à cette valeur.  
  
 Ce membre peut être n’importe quelle combinaison des valeurs suivantes :  
  
-   [TASK\_STATE\_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)  
  
-   [TASK\_STATE\_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)  
  
-   [TASK\_STATE\_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)  
  
-   [TASK\_STATE\_WAITING\_ON\_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)  
  
-   [TASK\_STATE\_RAN\_TO\_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)  
  
## Voir aussi  
 [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)