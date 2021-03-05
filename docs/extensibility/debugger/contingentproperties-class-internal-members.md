---
description: Contient des propriétés supplémentaires pour un objet System. Threading. Tasks. Task.
title: Classe ContingentProperties-membres internes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2303318c7a5f36027ce7709c5b09b5846fc6fab6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154975"
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
