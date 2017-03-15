---
title: "Classe ContingentProperties - membres internes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Classe ContingentProperties [moteurs de débogage .NET Framework]"
  - "moteurs de débogage, classe ContingentProperties (.NET Framework)"
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Classe ContingentProperties - membres internes
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Contient des propriétés supplémentaires pour un <xref:System.Threading.Tasks.Task> objet.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib \(dans mscorlib.dll\)  
  
 Étant donné que vous ne pouvez pas accéder à ces membres internes du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language \(CIL\).  
  
## Syntaxe  
  
```  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## Membres  
  
### Champs  
  
|Nom|Description|  
|---------|-----------------|  
|[m\_children](../../extensibility/debugger/m-children-field.md)|La liste des tâches enfants qui sont enregistrés avec cette tâche.|  
  
## Notes  
 Le .NET Framework initialise les champs de cette classe uniquement lorsqu’elles sont nécessaires.  
  
## Voir aussi  
 [Internes de Parallel Extensions pour .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)