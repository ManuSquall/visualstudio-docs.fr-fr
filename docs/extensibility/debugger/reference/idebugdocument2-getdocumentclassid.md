---
title: IDebugDocument2::GetDocumentClassID (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetDocumentClassID
helpviewer_keywords:
- IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71683c91082f477da530ec1be1fdc7627d6a7635
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732028"
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
Obtient l’identifiant de classe du document.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDocumentClassID( 
   CLSID* pclsid
);
```

```csharp
int GetDocumentClassID( 
   out Guid pclsid
);
```

## <a name="parameters"></a>Paramètres
`pclsid`[out] Renvoie un GUID qui est l’ID de classe du document.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 La classe GUID peut être utilisée pour instantanéer les classes individuelles de chacune d’entre elles représente un document.

## <a name="see-also"></a>Voir aussi
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
