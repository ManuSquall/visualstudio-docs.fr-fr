---
title: 'IDebugCustomAttribute :: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5aade49d77861d6aacdf955a167aeccbbaca4071
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928430"
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
à Retourne une chaîne contenant le nom de l’attribut personnalisé.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Le nommé retourné par cette méthode correspond au nom de la classe utilisée pour déclarer l’attribut. Cela peut ne pas correspondre exactement au nom de la classe d’attributs personnalisés elle-même, car C# permet de supprimer le suffixe « Attribute » d’un nom d’attribut personnalisé lorsqu’il est utilisé dans une déclaration.

## <a name="see-also"></a>Voir aussi
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
