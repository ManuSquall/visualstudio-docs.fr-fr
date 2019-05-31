---
title: IDebugDocument2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 31eddcc07adc181e179c3f3edba669fff85fa565
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310280"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Obtient le nom du document sous plusieurs formes.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetName( 
   GETNAME_TYPE gnType,
   BSTR*        pbstrFileName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE gnType,
   out string        pbstrFileName
);
```

## <a name="parameters"></a>Paramètres
`gnType`\
[in] Une valeur comprise entre le [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) énumération qui détermine le type de nom à retourner.

`pbstrFileName`\
[out] Retourne une chaîne contenant le nom du document.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode peut, par exemple, retourner le nom du document comme un titre ou en tant que nom de fichier ou même dans un nom de fichier.

## <a name="see-also"></a>Voir aussi
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)