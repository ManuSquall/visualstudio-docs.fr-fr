---
description: Liste des tâches enfants inscrites avec cette tâche.
title: Champ m_children | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 311ab164551e46fbe1c30b5a6045a7993a900a67
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901368"
---
# <a name="m_children-field"></a>Champ m_children
Liste des tâches enfants inscrites avec cette tâche.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (en *mscorlib.dll*)

 Étant donné que vous ne pouvez pas accéder à ce membre interne à partir de la .NET Framework, la syntaxe suivante est fournie en Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Notes
 Pendant que la tâche est en cours d’exécution, seul le thread qui exécute la tâche doit accéder à ce tableau.

 Si la tâche est terminée, les autres threads peuvent accéder à ce champ tant qu’ils n’y ajoutent rien ou n’en suppriment rien.

## <a name="see-also"></a>Voir aussi
- [ContingentProperties, classe](../../extensibility/debugger/contingentproperties-class-internal-members.md)
