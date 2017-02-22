---
title: "Structure AsyncTaskMethodBuilder - membres internes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "moteurs de débogage, structure AsyncTaskMethodBuilder (.NET Framework)"
  - "Structure AsyncTaskMethodBuilder [moteurs de débogage .NET Framework]"
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Structure AsyncTaskMethodBuilder - membres internes
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit les membres internes de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> classe. Pour obtenir des informations générales sur cette classe, consultez la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> rubrique de référence.  
  
 **Espace de noms :** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly :** mscorlib \(dans mscorlib.dll\)  
  
 Étant donné que vous ne pouvez pas accéder à ces membres internes du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language \(CIL\).  
  
## Syntaxe  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## Membres internes  
  
|Nom|Description|  
|---------|-----------------|  
|[Propriété de ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Obtient un objet qui peut être utilisé pour identifier de manière unique ce générateur au débogueur.|  
|[champ de m\_builder](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Représente l'objet Générateur générique auquel cette instance non générique délègue.|  
  
## Voir aussi  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [Internes de Parallel Extensions pour .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)