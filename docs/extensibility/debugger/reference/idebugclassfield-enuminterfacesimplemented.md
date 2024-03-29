---
description: Crée un énumérateur pour les interfaces implémentées par cette classe.
title: 'IDebugClassField :: EnumInterfacesImplemented | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1763cbcd0a1c61150a054752c94a42f10127251a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088612"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Crée un énumérateur pour les interfaces implémentées par cette classe.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumInterfacesImplemented( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumInterfacesImplemented(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Paramètres
`ppEnum`\
à Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des interfaces implémentées. Retourne une valeur null s’il n’y a pas d’interface.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ou retourne S_FALSE si aucune interface n’est implémentée sur cette classe. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Chaque élément de l’énumération est un objet [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) décrivant une interface. Notez que [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] le code non managé n’utilise pas les interfaces comme une entité discrète, de sorte que cette méthode retourne toujours une valeur null pour le code non managé [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] .

## <a name="see-also"></a>Voir aussi
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
