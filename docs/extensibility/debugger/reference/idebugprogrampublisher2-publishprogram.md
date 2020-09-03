---
title: IDebugProgramPublisher2 ::P ublishProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20de162bdc3be2cc4771c9746b13c40a1e140a96
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721688"
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
Cette méthode rend un programme disponible pour les moteurs de débogage (DEs) et le gestionnaire de débogage de session.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT PublishProgram(
   CONST_GUID_ARRAY Engines,
   LPCOLESTR        szFriendlyName,
   IUnknown*        pDebuggeeInterface
);
```

```csharp
int PublishProgram(
   CONST_GUID_ARRAY Engines,
   string           szFriendlyName,
   object           pDebuggeeInterface
);
```

## <a name="parameters"></a>Paramètres
`Engines`\
dans Tableau de GUID pour DEs qui peuvent être lancés ou attachés à ce programme.

`szFriendlyName`\
dans Nom convivial du programme (ce qui apparaît dans les menus ou les boîtes de dialogue présentés à l’utilisateur).

`pDebuggeeInterface`\
[in] `IUnknown` interface du programme (cette valeur est utilisée comme cookie pour identifier de manière unique le programme ; cette même valeur est utilisée pour annuler la publication du programme).

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Pour rendre un programme plus disponible pour le débogage, appelez [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).

## <a name="see-also"></a>Voir aussi
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)
