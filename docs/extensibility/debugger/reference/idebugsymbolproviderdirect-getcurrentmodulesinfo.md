---
title: IDebugSymbolProviderDirect::GetCurrentModulesInfo Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetCurrentModulesInfo
- GetCurrentModulesInfo
ms.assetid: b3b45ed2-ea4e-4389-b78a-11fc9796a6c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a51a7bbbe081d323ea478b64917507ce43b45762
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719119"
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
[dans] Nombre de modules `ppGuids` dans le tableau.

`ppGuids`\
[dans] Array qui contient les identificateurs uniques pour les modules.

`pADIds`\
[dans] Identifiants pour les domaines d’application.

`pCurrentState`\
[dans] État actuel du groupe de symboles.

`ppCDModItfs`\
[out] Retourne un objet qui contient les modules dans le groupe de symboles.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
