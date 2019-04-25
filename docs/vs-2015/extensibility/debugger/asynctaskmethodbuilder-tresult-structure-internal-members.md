---
title: AsyncTaskMethodBuilder&lt;TResult&gt; Structure - membres internes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e4999b71ae8f654aa3d362ba16c6cf5bc6574da
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947883"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult&gt; Structure - membres internes
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette rubrique décrit les membres internes de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> classe. Pour obtenir des informations générales sur cette classe, consultez le <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> rubrique de référence.  
  
 **Espace de noms :** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
 Étant donné que vous ne peut pas accéder à ces membres internes à partir de .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Membres internes  
  
|Nom|Description|  
|----------|-----------------|  
|[Propriété de ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Obtient un objet qui peut être utilisé pour identifier de manière unique ce générateur au débogueur.|  
|[m_task field](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Représente l’initialisation différée créé la tâche.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [Valeurs internes d’extension parallèle pour .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
