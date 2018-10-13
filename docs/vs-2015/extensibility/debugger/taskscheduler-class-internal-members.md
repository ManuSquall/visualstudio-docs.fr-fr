---
title: Classe TaskScheduler - membres internes | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e384b9c7734c2197dd79c0b9fb6b415329ae0f05
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203786"
---
# <a name="taskscheduler-class---internal-members"></a>Classe TaskScheduler - Membres internes
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette rubrique décrit les membres internes de la <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe qui vous aident à implémenter un débogueur personnalisé. Pour obtenir des informations générales sur cette classe, consultez le <xref:System.Threading.Tasks.TaskScheduler> rubrique de référence.  
  
 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
 Étant donné que vous ne peut pas accéder à ces membres internes à partir de .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|Nom|Description|  
|----------|-----------------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Récupère un tableau de toutes les tâches planifiées.|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Récupère un tableau de tous les <xref:System.Threading.Tasks.TaskScheduler> les objets qui sont actuellement actives.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Valeurs internes d’extension parallèle pour .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

