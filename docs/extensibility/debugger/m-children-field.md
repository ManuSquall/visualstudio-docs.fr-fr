---
title: "m_children, champ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "champ m_children, ContingentProperties classe [moteurs de débogage .NET Framework]"
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# m_children, champ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La liste des tâches enfants qui sont enregistrés avec cette tâche.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib \(dans mscorlib.dll\)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language \(CIL\).  
  
## Syntaxe  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## Notes  
 Lorsque la tâche s’exécute, seul le thread qui exécute la tâche doit accéder à ce tableau.  
  
 Si la tâche est terminée, autres threads peuvent accéder à ce champ tant qu’ils n’exigent pas rien ajouter ou supprimer tout élément à partir de celui\-ci.  
  
## Voir aussi  
 [ContingentProperties \(classe\)](../../extensibility/debugger/contingentproperties-class-internal-members.md)