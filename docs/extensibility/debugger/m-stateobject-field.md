---
title: "m_stateObject, champ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "champ m_stateObject, la classe de tâche [moteurs de débogage .NET Framework]"
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# m_stateObject, champ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Objet qui représente les données utilisées par l’action.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib \(dans mscorlib.dll\)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language \(CIL\).  
  
## Syntaxe  
  
```  
.field assembly object m_stateObject  
```  
  
## Notes  
 Il s’agit du `state` paramètre dans le <xref:System.Threading.Tasks.Task.%23ctor%2A> constructeur. Il est également le champ de stockage pour le <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> propriété.  
  
## Voir aussi  
 [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)