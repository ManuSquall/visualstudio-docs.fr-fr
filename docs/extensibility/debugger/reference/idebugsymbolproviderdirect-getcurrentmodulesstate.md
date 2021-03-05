---
description: Récupère des informations sur le groupe de symboles dont le fournisseur de symboles est membre.
title: 'IDebugSymbolProviderDirect :: GetCurrentModulesState | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetCurrentModulesState
- IDebugSymbolProviderDirect::GetCurrentModulesState
ms.assetid: a0c85318-5686-4eed-b213-21f2b9e681e6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fcc127bd3450f06a51ab0b04d61d52f4ee08e092
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149481"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesstate"></a>IDebugSymbolProviderDirect::GetCurrentModulesState
Récupère des informations sur le groupe de symboles dont le fournisseur de symboles est membre.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCurrentModulesState(
    DWORD*          pState,
    unsigned long * count
);
```

```csharp
int GetCurrentModulesState(
    out uint pState,
    out uint count
);
```

## <a name="parameters"></a>Paramètres
`pState`\
à État du groupe de fournisseurs de symboles.

`count`\
à Nombre de modules dans le groupe.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 L’État est modifié chaque fois qu’un module est ajouté ou supprimé dans le groupe de symboles. Par conséquent, cette méthode peut être utilisée pour détecter si un groupe de symboles a été modifié.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
