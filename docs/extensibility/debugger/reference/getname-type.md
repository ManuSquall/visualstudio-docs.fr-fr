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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9811312188e63017e074d12be6dfa67ab6929aa6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162444"
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

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
