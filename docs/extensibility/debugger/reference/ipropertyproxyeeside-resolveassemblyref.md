---
description: Détermine l’emplacement de la référence d’assembly managée spécifiée.
title: 'IPropertyProxyEESide :: ResolveAssemblyRef | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 687ca5922cc59322c37b7b391a9b5f40d52c14ad
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225576"
---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
Détermine l’emplacement de la référence d’assembly managée spécifiée.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ResolveAssemblyRef(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  assemLocation,
   ASSEMBLYLOCRESOLUTION* alr
);
```

```csharp
int ResolveAssemblyRef(
   ref string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     assemLocation,
   out enum_ASSEMBLYLOCRESOLUTION alr
);
```

## <a name="parameters"></a>Paramètres
`assemName`\
dans Nom de l’assembly à résoudre.

`assemBytes`\
à Retourne un objet [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) contenant les octets d’assembly associés à la référence.

`assemPdb`\
à Retourne un `IEEDataStorage` objet contenant les données de magasin de symboles associées à cette référence.

`assemLocation`\
à Retourne l’emplacement du chemin d’accès de cette référence.

`alr`\
à Retourne une valeur de l’énumération [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) indiquant l’emplacement de l’assembly de cette référence.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode n’est généralement pas implémentée par un évaluateur d’expression personnalisé.

## <a name="see-also"></a>Voir aussi
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
