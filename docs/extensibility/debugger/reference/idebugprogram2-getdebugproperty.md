---
title: IDebugProgram2::GetDebugProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 109e3ac1267afb4097429aafc9264416f3c2dbf1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319369"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Obtient les propriétés du programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDebugProperty( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>Paramètres
`ppProperty`\
[out] Retourne un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objet qui représente les propriétés du programme.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Les propriétés retournées par cette méthode sont spécifiques au programme. Si le programme doit retourner plusieurs propriétés, puis le [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objet retourné par cette méthode est un conteneur de propriétés supplémentaires et en appelant le [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) méthode retourne un liste de toutes les propriétés.

 Un programme peut exposer n’importe quel nombre et le type de propriétés supplémentaires qui peuvent être décrits par le biais du `IDebugProperty2` interface. Un IDE peut afficher les propriétés du programme supplémentaires via une interface utilisateur du navigateur propriété générique.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)