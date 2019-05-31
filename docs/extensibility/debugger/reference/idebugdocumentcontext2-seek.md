---
title: IDebugDocumentContext2::Seek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 413b1416adcd4b20231666e25f6a8044e632198b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325430"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
Déplace le contexte de document en un nombre donné d’instructions ou des lignes.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Seek( 
   int                      nCount,
   IDebugDocumentContext2** ppDocContext
);
```

```cpp
int Seek( 
   int                        nCount,
   out IDebugDocumentContext2 ppDocContext
);
```

## <a name="parameters"></a>Paramètres
`nCount`\
[in] Nombre d’instructions ou des lignes pour passer, en fonction du contexte de document.

`ppDocContext`\
[out] Retourne un nouvel [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objet avec la nouvelle position.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)