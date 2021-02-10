---
title: 'IDebugMethodField :: GetThis | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1893ffac03aba345589274475f81abd44b5b7b5f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936819"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Obtient le `this` `Me` pointeur (en [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] ) de l’objet contenant la méthode.

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
à Retourne un objet [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) qui représente le pointeur « this ».

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Dans les langages orientés objet, il existe généralement un pointeur implicite vers l’instanciation actuelle d’une classe. Cela est connu sous le nom `this` de C#/c + + et comme `Me` dans [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] .

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
