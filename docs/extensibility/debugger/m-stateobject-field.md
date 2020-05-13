---
title: m_stateObject Field ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fed70f2eda19ad96454a83217c20c046809f3034
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738376"
---
# <a name="m_stateobject-field"></a>champ m_stateObject
Un objet qui représente les données que l’action utilisera.

 **Espace nom:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assemblée:** mscorlib (en *mscorlib.dll*)

 Parce que vous ne pouvez pas accéder à ce membre interne à partir du cadre .NET, la syntaxe suivante est fournie dans common Intermediate Language (CIL).

## <a name="syntax"></a>Syntaxe

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Notes
 C’est `state` le <xref:System.Threading.Tasks.Task.%23ctor%2A> paramètre dans le constructeur. C’est aussi le <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> champ d’appui de la propriété.

## <a name="see-also"></a>Voir aussi
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
