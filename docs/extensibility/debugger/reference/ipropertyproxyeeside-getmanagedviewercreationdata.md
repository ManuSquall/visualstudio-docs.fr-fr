---
description: Récupère des informations sur la visionneuse pour ce type de propriété afin d’instancier cette visionneuse.
title: 'IPropertyProxyEESide :: GetManagedViewerCreationData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc0ab85a3000db2090e9679b0ae065b9280f20cf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082502"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Récupère des informations sur la visionneuse pour ce type de propriété afin d’instancier cette visionneuse.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
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
à Retourne le nom de l’assembly contenant cet objet.

`assemBytes`\
à Retourne un objet [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) contenant les octets de l’assembly de cet objet (il s’agit d’une valeur null si aucun octet n’est disponible).

`assemPdb`\
à Retourne un `IEEDataStorage` objet contenant les informations du magasin de symboles pour cet objet (il s’agit d’une valeur null si aucun magasin de symboles n’est disponible).

`className`\
à Retourne le nom de la classe contenant cet objet.

`alr`\
à Retourne une valeur de l’énumération [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) indiquant l’emplacement de l’assembly.

`replacementOk`\
à Retourne une valeur différente `TRUE` de zéro () si la valeur de cet objet peut être modifiée ; zéro ( `FALSE` ) si l’objet est en lecture seule.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode est utilisée par les visualiseurs de type pour instancier une visionneuse managée.

## <a name="see-also"></a>Voir aussi
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
