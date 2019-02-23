---
title: GETNAME_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae68c77e2d6a41adfff6b49e55bbc6df4393fec7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701717"
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

## <a name="members"></a>Membres
GN_NAME spécifie un nom convivial du document ou de contexte.

GN_FILENAME Spécifie le chemin d’accès complet du document ou de contexte.

GN_BASENAME spécifie un nom de fichier de base au lieu d’un chemin d’accès complet du document ou de contexte.

GN_MONIKERNAME spécifie un nom unique du document ou de contexte sous la forme d’un moniker.

GN_URL spécifie un nom de l’URL du document ou de contexte.

GN_TITLE spécifie un titre du document, le cas échéant.

GN_STARTPAGEURL Obtient l’URL pour la page de démarrage de la traite.

## <a name="remarks"></a>Notes
Ces valeurs sont passées en tant que paramètres à la [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), et [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) méthodes pour spécifier le type de nom à retourner.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
