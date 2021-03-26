---
description: Récupère l’identificateur pour le domaine d’application.
title: 'IDebugAlias2 :: GetAppDomainId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee1caec6968f9a67a15a31c8064b7795a37a6829
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059104"
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
