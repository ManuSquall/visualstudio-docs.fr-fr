---
title: IDebugCustomAttribute::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2556a424e5109e75b667e9f32ecac5cc26ca781b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205338"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Obtient le nom de l’attribut personnalisé.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetName( 
   BSTR* bstrName
);
```

```csharp
int GetName(
   out string bstrName
);
```

## <a name="parameters"></a>Paramètres
`bstrName`\
[out] Retourne une chaîne contenant le nom de l’attribut personnalisé.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Nommé retourné par cette méthode correspond au nom de la classe utilisée pour déclarer l’attribut. Pas exactement cela peut correspondre au nom de la classe d’attributs personnalisés lui-même, car c# permet le suffixe « Attribute » à supprimer à partir d’un nom d’attribut personnalisé lorsqu’elle est utilisée dans une déclaration.

## <a name="see-also"></a>Voir aussi
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)