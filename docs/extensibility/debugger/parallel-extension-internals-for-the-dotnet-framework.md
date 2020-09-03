---
title: Éléments internes de l’extension parallèle pour le .NET Framework | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a3583e94a0bfff4474db03aa9d083add921f3da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738274"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Éléments internes de l’extension parallèle pour le .NET Framework
Cette section décrit les types, méthodes et champs internes des classes qui vous permettent d’implémenter un débogueur personnalisé pour les extensions parallèles au .NET Framework.

## <a name="in-this-section"></a>Contenu de cette section
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
