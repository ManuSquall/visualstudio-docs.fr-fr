---
description: Récupère des informations sur les modules dans le groupe de symboles.
title: 'IDebugSymbolProviderDirect :: GetCurrentModulesInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetCurrentModulesInfo
- GetCurrentModulesInfo
ms.assetid: b3b45ed2-ea4e-4389-b78a-11fc9796a6c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d59c3bd88c82d6f7bacc7ce66c33b36a137d4e8b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081345"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesinfo"></a>IDebugSymbolProviderDirect::GetCurrentModulesInfo
Récupère des informations sur les modules dans le groupe de symboles.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCurrentModulesInfo(
   unsigned long * pCount,
   GUID *          ppGuids,
   DWORD *         pADIds,
   DWORD *         pCurrentState,
   IUnknown **     ppCDModItfs
);
```

```csharp
int GetCurrentModulesInfo(
   uint       pCount,
   Guid       ppGuids,
   uint       pADIds,
   uint       pCurrentState,
   out object ppCDModItfs
);
```

## <a name="parameters"></a>Paramètres
`pCount`\
dans Nombre de modules dans le `ppGuids` tableau.

`ppGuids`\
dans Tableau qui contient les identificateurs uniques des modules.

`pADIds`\
dans Identificateurs des domaines d’application.

`pCurrentState`\
dans État actuel du groupe de symboles.

`ppCDModItfs`\
à Retourne un objet qui contient les modules dans le groupe de symboles.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
