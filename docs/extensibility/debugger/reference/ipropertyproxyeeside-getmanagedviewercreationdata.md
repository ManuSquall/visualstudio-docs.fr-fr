---
title: IPropertyProxyEESide::GetManagedViewerCreationData (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e72922b348c8744f10037e199e93f735ff4be8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714962"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Récupère des informations sur le spectateur pour ce type de propriété afin d’instantanéer ce spectateur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
   out string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     className,
   out enum_ASSEMBLYLOCRESOLUTION alr,
   out int                        replacementOk
);
```

## <a name="parameters"></a>Paramètres
`assemName`\
[out] Retourne le nom de l’assemblage contenant cet objet.

`assemBytes`\
[out] Renvoie un objet [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) contenant les octets d’assemblage de cet objet (il s’agit d’une valeur nulle si aucun octet n’est disponible).

`assemPdb`\
[out] Renvoie `IEEDataStorage` un objet contenant les informations de magasin de symboles pour cet objet (il s’agit d’une valeur nulle si aucun magasin de symbole n’est disponible).

`className`\
[out] Retourne le nom de classe contenant cet objet.

`alr`\
[out] Retourne une valeur du recensement [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) indiquant l’emplacement de l’assemblage.

`replacementOk`\
[out] Retourne nonzero`TRUE`( ) si la valeur de cet objet peut être changée ; zéro`FALSE`( ) si l’objet est lu seulement.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode est utilisée par des visualisateurs de type pour instantanéiser un spectateur géré.

## <a name="see-also"></a>Voir aussi
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
