---
description: Récupère l’identificateur pour le domaine d’application.
title: 'IDebugAlias2 :: GetAppDomainId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6f5bd0d6a96ad41409b87433599fe693fc86c1cc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143868"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Récupère l’identificateur pour le domaine d’application.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAppDomainId (
   ULONG32* pappDomainId
);
```

```csharp
int GetAppDomainId (
   out uint pappDomainId
);
```

## <a name="parameters"></a>Paramètres
`pappDomainId`\
à Retourne l’identificateur de domaine d’application.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 L’identificateur de domaine d’application est modifié chaque fois que l’application est redémarrée et qu’un nouveau domaine d’application est créé.

## <a name="see-also"></a>Voir aussi
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
