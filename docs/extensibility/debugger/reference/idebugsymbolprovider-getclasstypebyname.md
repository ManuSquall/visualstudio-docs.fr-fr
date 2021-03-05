---
description: Cette méthode obtient le type de champ de classe qui représente un nom de classe complet.
title: 'IDebugSymbolProvider :: GetClassTypeByName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetClassTypeByName
helpviewer_keywords:
- IDebugSymbolProvider::GetClassTypeByName method
ms.assetid: 2c748909-51dc-49b7-b193-19f96fca1138
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58b7002abf622992dacde4797f41a272177c280e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159664"
---
# <a name="idebugsymbolprovidergetclasstypebyname"></a>IDebugSymbolProvider::GetClassTypeByName
Cette méthode obtient le type de champ de classe qui représente un nom de classe complet.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetClassTypeByName( 
   LPCOLESTR          pszClassName,
   NAME_MATCH         nameMatch,
   IDebugClassField** ppField
);
```

```csharp
int GetClassTypeByName(
   string               pszClassName,
   NAME_MATCH           nameMatch,
   out IDebugClassField ppField
);
```

## <a name="parameters"></a>Paramètres
`pszClassName`\
dans Nom de la classe.

`nameMatch`\
dans Sélectionne le type de correspondance, par exemple en respectant la casse. Valeur de l’énumération [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) .

`ppField`\
à Retourne le type de classe tel que représenté par l’interface [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
