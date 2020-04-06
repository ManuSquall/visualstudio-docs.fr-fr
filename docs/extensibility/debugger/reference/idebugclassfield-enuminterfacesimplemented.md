---
title: IDebugClassField::EnumInterfacesImplemented Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91d9cac6b695ba2a0d34da776fa79ba62ba2e015
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734488"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Crée un enumérateur pour les interfaces mises en œuvre par cette classe.

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
[out] Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des interfaces implémentées. Renvoie une valeur nulle s’il n’y a pas d’interfaces.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK ou retournent S_FALSE s’il n’y a pas d’interfaces implémentées sur cette classe. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Chaque élément de l’énumération est un objet [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) décrivant une interface. Notez que le [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] code non menté n’utilise pas les interfaces comme une [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] entité discrète de sorte que cette méthode renvoie toujours une valeur nulle pour le code non gestion.

## <a name="see-also"></a>Voir aussi
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
