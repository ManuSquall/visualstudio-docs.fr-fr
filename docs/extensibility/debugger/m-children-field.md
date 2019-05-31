---
title: m_children Field | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab6446b18350fe1f11e0b164d9eb4bff39035ddb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330890"
---
# <a name="mchildren-field"></a>m_children field
La liste des tâches enfants qui sont inscrits auprès de cette tâche.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (dans *mscorlib.dll*)

 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Notes
 Alors que la tâche est en cours d’exécution, seul le thread qui exécute la tâche doit accéder à ce tableau.

 Si la tâche est terminée, autres threads peuvent accéder à ce champ tant que qu’ils n’ajoutent rien à celui-ci ou supprimer quoi que ce soit à partir de celui-ci.

## <a name="see-also"></a>Voir aussi
- [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)