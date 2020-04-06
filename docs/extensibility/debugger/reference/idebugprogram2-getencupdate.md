---
title: IDebugProgram2::GetENCUpdate ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e90ff9f8a7a80913aec72b9fe2bb6fe470013d51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722834"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Cette méthode obtient la mise à jour Edit and Continue (ENC) pour ce programme. Un moteur de débogage personnalisé retourne toujours `E_NOTIMPL`.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetENCUpdate( 
   IUnknown** ppUpdate
);
```

```csharp
int GetENCUpdate(
   out object ppUpdate
);
```

## <a name="parameters"></a>Paramètres
`ppUpdate`\
[out] Retourne une interface interne qui peut être utilisée pour mettre à jour ce programme.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

> [!NOTE]
> Un moteur de débogé `E_NOTIMPL`personnalisé doit toujours revenir .

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
