---
description: Objet qui représente les données que l’action doit utiliser.
title: Champ m_stateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2128073f47c76244a18e18005a431f9317686c3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054788"
---
# <a name="m_stateobject-field"></a>champ m_stateObject
Objet qui représente les données que l’action doit utiliser.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (en *mscorlib.dll*)

 Étant donné que vous ne pouvez pas accéder à ce membre interne à partir de la .NET Framework, la syntaxe suivante est fournie en Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Notes
 Il s’agit du `state` paramètre dans le <xref:System.Threading.Tasks.Task.%23ctor%2A> constructeur. C’est également le champ de stockage de la <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> propriété.

## <a name="see-also"></a>Voir aussi
- [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)
