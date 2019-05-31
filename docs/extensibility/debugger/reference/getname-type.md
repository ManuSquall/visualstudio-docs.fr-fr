---
title: GETNAME_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1bdcbc4171c8a481ee0c45456ef5600f5150c6d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317583"
---
# <a name="getnametype"></a>GETNAME_TYPE
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
Spécifie un nom convivial du document ou de contexte.

`GN_FILENAME`\
Spécifie le chemin d’accès complet du document ou de contexte.

`GN_BASENAME`\
Spécifie un nom de fichier de base au lieu d’un chemin d’accès complet du document ou de contexte.

`GN_MONIKERNAME`\
Spécifie un nom unique du document ou de contexte sous la forme d’un moniker.

`GN_URL`\
Spécifie un nom de l’URL du document ou de contexte.

`GN_TITLE`\
Spécifie un titre du document, le cas échéant.

`GN_STARTPAGEURL`\
Obtient l’URL de page de démarrage pour les processus.

## <a name="remarks"></a>Notes
Ces valeurs sont passées en tant que paramètres à la [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), et [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) méthodes pour spécifier le type de nom à retourner.

## <a name="requirements"></a>Configuration requise
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
