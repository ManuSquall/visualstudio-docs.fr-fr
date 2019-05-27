---
title: IPropertyProxyProvider::GetPropertyProxy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider::GetPropertyProxy
helpviewer_keywords:
- IPropertyProxyProvider::GetPropertyProxy
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 958b3571a5bfabbd609e3ca62bcdfe9b5a6171ca
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212854"
---
# <a name="ipropertyproxyprovidergetpropertyproxy"></a>IPropertyProxyProvider::GetPropertyProxy
Récupère l’interface de proxy de propriété pour l’ID de proxy spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPropertyProxy(
   DWORD                  dwID,
   IPropertyProxyEESide** proxy
);
```

```csharp
int GetPropertyProxy(
   uint                     dwID,
   out IPropertyProxyEESide proxy
);
```

## <a name="parameters"></a>Paramètres
`dwID`\
[in] ID du proxy de propriété souhaitée.

`proxy`\
[out] Retourne un [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) objet.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Pour prendre en charge les visualiseurs de type externe, cette méthode transfère généralement l’appel à la [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md) (méthode). Consultez [visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) pour plus d’informations sur la façon dont le IEEVisualizerService est obtenu.

## <a name="see-also"></a>Voir aussi
- [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)