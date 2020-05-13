---
title: IDebugMethodField::EnumAllLocals - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50da5af616c56276a0299a0d08e6eeb0b88181cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727332"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Crée un enumérateur pour toutes les variables locales de la méthode, y compris celles générées en interne par un compilateur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumAllLocals( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumAllLocals(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Paramètres
`pAddress`\
[dans] Un objet [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) représentant une adresse de débogé dans la méthode, pointant vers une portée ou un contexte particulier.

`ppLocals`\
[out] Renvoie un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste de tous les habitants dans la portée spécifiée; autrement, retourne une valeur nulle indiquant aucun local.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK ou retournent S_FALSE s’il n’y a pas d’habitants. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Seules les variables définies dans le bloc qui contient l’adresse de débaillement donnée sont énumérées. Cette méthode comprend tous les habitants générés par les compilateurs. Si tout ce qui est nécessaire sont les habitants explicitement définis dans la source, appelez la méthode [EnumLocals.](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)

 Une méthode peut contenir plusieurs contextes ou blocs d’établissement de la portée.

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
