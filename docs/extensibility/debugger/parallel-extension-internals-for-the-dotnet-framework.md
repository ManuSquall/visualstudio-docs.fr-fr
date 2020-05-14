---
title: Internals d’extension parallèle pour le cadre .NET (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738274"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Internals d’extension parallèle pour le cadre .NET
Cette section décrit les types internes, les méthodes et les champs de classes qui vous aident à mettre en œuvre un débbugger personnalisé pour les extensions parallèles au cadre .NET.

## <a name="in-this-section"></a>Contenu de cette section
 [Classe de tâches](../../extensibility/debugger/task-class-internal-members.md) Décrit les données internes <xref:System.Threading.Tasks.Task?displayProperty=fullName> des membres de la classe.

 [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md) Décrit les données internes <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> des membres de la classe.

 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md) Décrit les données internes `System.Threading.Tasks.ContingentProperties` des membres de la classe.

 [Structure AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) Décrit les membres internes <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> de la structure.

 [AsyncTaskMethodBuilder\<TResult> structure](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) décrit les membres <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> internes de la structure.

 [Structure AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) Décrit les membres internes <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> de la structure.

## <a name="see-also"></a>Voir aussi
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Visual Studio débbugger extensibility](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Programmation parallèle](/dotnet/standard/parallel-programming/index)
