---
title: 'IDebugCustomAttributeQuery2 :: EnumCustomAttributes (| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 97476647c42dc66d3998aecf2c717fa3bbb08cf4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842457"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
Obtient un énumérateur pour tous les attributs personnalisés attachés à ce champ.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumCustomAttributes( 
   IEnumDebugCustomAttributes** ppEnum
);
```

```csharp
int EnumCustomAttributes(
   out IEnumDebugCustomAttributes ppEnum
);
```

## <a name="parameters"></a>Paramètres
`ppEnum`\
à Retourne un objet [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) représentant la liste des attributs personnalisés ; Sinon, retourne une valeur null s’il n’y a pas d’attributs personnalisés.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ou S_FALSE s’il n’y a pas d’attributs personnalisés dans ce champ. Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Remarques
 Un champ peut avoir plusieurs attributs personnalisés.

## <a name="see-also"></a>Voir aussi
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
