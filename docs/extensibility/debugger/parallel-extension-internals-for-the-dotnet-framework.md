---
title: Éléments internes de l’extension parallèle pour le .NET Framework | Microsoft Docs
description: Ces ressources décrivent les types internes, les méthodes et les champs de classes utilisés pour implémenter un débogueur personnalisé pour les extensions parallèles au .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9aec52f354043dabb3bf816bbd35352f0c3a28bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067827"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Éléments internes de l’extension parallèle pour le .NET Framework
Cette section décrit les types, méthodes et champs internes des classes qui vous permettent d’implémenter un débogueur personnalisé pour les extensions parallèles au .NET Framework.

## <a name="in-this-section"></a>Dans cette section
 [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md) Décrit les membres de données internes de la <xref:System.Threading.Tasks.Task?displayProperty=fullName> classe.

 [TaskScheduler (classe](../../extensibility/debugger/taskscheduler-class-internal-members.md) ) Décrit les membres de données internes de la <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe.

 [ContingentProperties, classe](../../extensibility/debugger/contingentproperties-class-internal-members.md) Décrit les membres de données internes de la `System.Threading.Tasks.ContingentProperties` classe.

 [AsyncTaskMethodBuilder, structure](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) Décrit les membres internes de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> structure.

 [La \<TResult> structure AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) décrit les membres internes de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> structure.

 [AsyncVoidMethodBuilder, structure](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) Décrit les membres internes de la <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> structure.

## <a name="see-also"></a>Voir aussi
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Extensibilité du débogueur Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Programmation parallèle](/dotnet/standard/parallel-programming/index)
