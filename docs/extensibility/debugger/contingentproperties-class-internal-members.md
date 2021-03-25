---
description: Contient des propriétés supplémentaires pour un objet System. Threading. Tasks. Task.
title: Classe ContingentProperties-membres internes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 295b8c3b33059811e665e362c9894103b47c422d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054996"
---
# <a name="contingentproperties-class---internal-members"></a>Classe ContingentProperties-membres internes
Contient des propriétés supplémentaires pour un <xref:System.Threading.Tasks.Task> objet.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (en mscorlib.dll)

 Étant donné que vous ne pouvez pas accéder à ces membres internes à partir du .NET Framework, la syntaxe suivante est fournie en Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Membres

### <a name="fields"></a>Champs

|Nom|Description|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|Liste des tâches enfants inscrites avec cette tâche.|

## <a name="remarks"></a>Notes
 L' .NET Framework initialise les champs de cette classe uniquement lorsqu’ils sont nécessaires.

## <a name="see-also"></a>Voir aussi
- [Éléments internes de l’extension parallèle pour le .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
