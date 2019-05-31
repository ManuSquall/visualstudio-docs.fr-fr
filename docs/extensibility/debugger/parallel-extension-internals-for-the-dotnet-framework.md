---
title: En parallèle de valeurs internes d’Extension pour le .NET Framework | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ecc13be90259c68fa4d37daa5139b27b4ea8c7f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351483"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Mécanismes internes d’extension parallèle pour le .NET Framework
Cette section décrit les types internes, méthodes, et les champs de classes qui vous aident à implémentent un débogueur personnalisé pour les extensions parallèles au .NET Framework.

## <a name="in-this-section"></a>Dans cette section
 [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md) décrit les membres de données internes de la <xref:System.Threading.Tasks.Task?displayProperty=fullName> classe.

 [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md) décrit les membres de données internes de la <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe.

 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md) décrit les membres de données internes de la `System.Threading.Tasks.ContingentProperties` classe.

 [Structure AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) décrit les membres internes de le <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> structure.

 [AsyncTaskMethodBuilder\<TResult > structure](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) décrit les membres internes de le <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> structure.

 [Structure AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) décrit les membres internes de le <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> structure.

## <a name="see-also"></a>Voir aussi
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Extensibilité du débogueur Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Programmation parallèle](/dotnet/standard/parallel-programming/index)