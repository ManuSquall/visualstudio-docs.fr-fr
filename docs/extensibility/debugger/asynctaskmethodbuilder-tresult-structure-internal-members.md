---
title: AsyncTaskMethodBuilder&lt;TResult&gt; Structure - membres internes | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d6956cf1150a1a30d062201080a97dae7d231a75
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult&gt; Structure - membres internes
Cette rubrique décrit les membres internes de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> classe. Pour obtenir des informations générales sur cette classe, consultez la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> rubrique de référence.  
  
 **Namespace :**<xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
 Étant donné que vous ne pouvez pas accéder à ces membres internes du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Membres internes  
  
|Nom|Description|  
|----------|-----------------|  
|[Propriété de ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Obtient un objet qui peut être utilisé pour identifier de façon unique ce générateur au débogueur.|  
|[champ de m_task](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Représente l’initialisée tardivement créé la tâche.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [Valeurs internes d’extension parallèle pour .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)