---
title: Méthode GetTaskSchedulersForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8d038c8c67731fe1bff9ec705b5ddf416807a57
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353719"
---
# <a name="gettaskschedulersfordebugger-method"></a>Méthode GetTaskSchedulersForDebugger
Récupère un tableau de tous les <xref:System.Threading.Tasks.TaskScheduler> les objets qui sont actuellement actives.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (dans *mscorlib.dll*)

 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Valeur de retour
 Un tableau de tous les <xref:System.Threading.Tasks.TaskScheduler> les objets qui sont actuellement actives dans ce <xref:System.AppDomain>.

## <a name="remarks"></a>Notes
 Cette méthode n’est pas thread-safe et vous ne devez pas l’utiliser en même temps que d’autres instances de <xref:System.Threading.Tasks.TaskScheduler>. Appelez cette méthode à partir d’un débogueur uniquement lorsque le débogueur a suspendu tous les autres threads.

## <a name="see-also"></a>Voir aussi
- [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)