---
title: IDebugMethodField::GetThis Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b29252d1586d039084ec1d21f1fc4967aea68baf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727171"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Obtient `this` le`Me` [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]pointeur ( dans ) de l’objet contenant la méthode.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Paramètres
`ppClass`\
[out] Retourne un objet [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) représentant le pointeur "ce".

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 Dans les langues orientées objet, il y a généralement un pointeur implicite à l’instantanéisation actuelle d’une classe. C’est `this` ce qu’on appelle dans `Me` [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]C '/C ' et comme dans .

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
