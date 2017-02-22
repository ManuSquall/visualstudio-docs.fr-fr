---
title: "Structure AsyncVoidMethodBuilder - membres internes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "moteurs de débogage, structure AsyncVoidMethodBuilder (.NET Framework)"
  - "Structure AsyncVoidMethodBuilder [moteurs de débogage .NET Framework]"
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Structure AsyncVoidMethodBuilder - membres internes
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit les membres internes de la <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> classe. Pour obtenir des informations générales sur cette classe, consultez la <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> rubrique de référence.  
  
 **Espace de noms :** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly :** mscorlib \(dans mscorlib.dll\)  
  
 Étant donné que vous ne pouvez pas accéder à ces membres internes du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language \(CIL\).  
  
## Syntaxe  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## Membres internes  
  
|Nom|Description|  
|---------|-----------------|  
|[Propriété de ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Obtient un objet qui peut être utilisé pour identifier de manière unique ce générateur au débogueur.|  
|[champ de m\_objectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Représente l'objet initialisé tardivement utilisé par le débogueur pour identifier de manière unique ce générateur.|  
  
## Voir aussi  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [Internes de Parallel Extensions pour .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)