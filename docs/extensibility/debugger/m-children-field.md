---
title: m_children Field ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07933fd4c9f359e72714600abdf8b4ee29268f84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738427"
---
# <a name="m_children-field"></a>champ m_children
Liste des tâches d’enfant qui sont enregistrées dans cette tâche.

 **Espace nom:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assemblée:** mscorlib (en *mscorlib.dll*)

 Parce que vous ne pouvez pas accéder à ce membre interne à partir du cadre .NET, la syntaxe suivante est fournie dans common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Notes
 Pendant que la tâche est en cours d’exécution, seul le thread qui exécute la tâche doit accéder à ce tableau.

 Si la tâche est terminée, d’autres threads peuvent accéder à ce champ tant qu’ils n’y ajoutent rien ou en retirent quoi que ce soit.

## <a name="see-also"></a>Voir aussi
- [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)
