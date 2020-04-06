---
title: IDebugProcess2::GetName ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetName
helpviewer_keywords:
- IDebugProcess2::GetName
ms.assetid: a2f66ab5-53e5-4cdc-a1b5-3b8afa8ee646
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68026ed56aabd08f93588277c8d2b44e13604974
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723971"
---
# <a name="idebugprocess2getname"></a>IDebugProcess2::GetName
Obtient le titre, le nom amical, ou le nom de fichier du processus.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetName( 
   GETNAME_TYPE  gnType,
   BSTR*         pbstrName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE  gnType,
   out string         pbstrName
);
```

## <a name="parameters"></a>Paramètres
`gnType`\
[dans] Une valeur de [l’énumération GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) qui précise le type de nom à retourner.

`pbstrName`\
[out] Retourne le nom du processus.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
