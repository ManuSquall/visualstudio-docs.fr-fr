---
title: 'IDebugMethodField :: EnumAllLocals | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727332"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Crée un énumérateur pour toutes les variables locales de la méthode, y compris celles générées en interne par un compilateur.

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
dans Objet [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) qui représente une adresse de débogage dans la méthode, pointant vers une portée ou un contexte particulier.

`ppLocals`\
à Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste de tous les variables locales dans l’étendue spécifiée ; Sinon, retourne une valeur null indiquant qu’il n’y a pas de variables locales.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ou retourne S_FALSE s’il n’y a pas de variables locales. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Seules les variables définies dans le bloc qui contient l’adresse de débogage donnée sont énumérées. Cette méthode comprend les variables locales générées par le compilateur. Si tout ce qui est nécessaire est les variables locales définies explicitement dans la source, appelez la méthode [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) .

 Une méthode peut contenir plusieurs contextes ou blocs d’étendue.

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
