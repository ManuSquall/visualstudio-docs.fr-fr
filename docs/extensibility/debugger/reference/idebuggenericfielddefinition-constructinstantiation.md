---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89f7ecfc79cc2a4279a8ca0fccfc527ef63e603b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313209"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
Construit une instance du champ étant donnée un tableau d’arguments de type.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ConstructInstantiation(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   IDebugField** ppConstructedField
);
```

```csharp
int ConstructInstantiation(
   uint            cArgs,
   IDebugField[]   ppArgs,
   out IDebugField ppConstructedField
);
```

## <a name="parameters"></a>Paramètres
`cArgs`\
[in] Nombre d’arguments dans le `ppArgs` tableau.

`ppArgs`\
[in] Tableau qui contient les arguments de type. Les arguments de type doivent être de types fermés (génériques non générique ou entièrement instanciés).

`ppConstructedField`\
[out] Retourne le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface qui représente le nouveau champ.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Les contraintes ne sont pas vérifiées.

## <a name="see-also"></a>Voir aussi
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)