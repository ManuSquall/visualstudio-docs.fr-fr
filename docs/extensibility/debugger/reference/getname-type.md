---
description: Spécifie le type de nom des fichiers à récupérer.
title: GETNAME_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a65c29a1925c8d0c1de97f87707f191713c2bb03
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054593"
---
# <a name="getname_type"></a>GETNAME_TYPE
Spécifie le type de nom des fichiers à récupérer.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
typedef DWORD GETNAME_TYPE;
```

```csharp
public enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
```

## <a name="fields"></a>Champs
`GN_NAME`\
Spécifie un nom convivial du document ou du contexte.

`GN_FILENAME`\
Spécifie le chemin d’accès complet du document ou du contexte.

`GN_BASENAME`\
Spécifie un nom de fichier de base au lieu d’un chemin d’accès complet au document ou au contexte.

`GN_MONIKERNAME`\
Spécifie un nom unique du document ou du contexte sous la forme d’un moniker.

`GN_URL`\
Spécifie le nom de l’URL du document ou du contexte.

`GN_TITLE`\
Spécifie le titre du document, s’il en existe un.

`GN_STARTPAGEURL`\
Obtient l’URL de la page de démarrage pour les processus.

## <a name="remarks"></a>Notes
Ces valeurs sont passées en tant que paramètres aux méthodes [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)et [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) pour spécifier le genre de nom à retourner.

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
