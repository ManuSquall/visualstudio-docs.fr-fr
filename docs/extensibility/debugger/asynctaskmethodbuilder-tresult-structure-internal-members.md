---
title: "Structure AsyncTaskMethodBuilder &lt; TResult &gt; - membres internes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Structure AsyncTaskMethodBuilder < TResult > [moteurs de débogage .NET Framework]"
  - "moteurs de débogage, structure AsyncTaskMethodBuilder < TResult > (.NET Framework)"
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Structure AsyncTaskMethodBuilder &lt; TResult &gt; - membres internes
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit les membres internes de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> classe. Pour obtenir des informations générales sur cette classe, consultez la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> rubrique de référence.  
  
 **Espace de noms :** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly :** mscorlib \(dans mscorlib.dll\)  
  
 Étant donné que vous ne pouvez pas accéder à ces membres internes du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language \(CIL\).  
  
## Syntaxe  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## Membres internes  
  
|Nom|Description|  
|---------|-----------------|  
|[Propriété de ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Obtient un objet qui peut être utilisé pour identifier de manière unique ce générateur au débogueur.|  
|[champ de m\_task](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Représente l'initialisation différée créé la tâche.|  
  
## Voir aussi  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [Internes de Parallel Extensions pour .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)