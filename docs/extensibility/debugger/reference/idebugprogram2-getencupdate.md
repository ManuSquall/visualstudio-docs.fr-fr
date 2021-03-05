---
description: Cette méthode obtient la mise à jour de modifier & Continuer (ENC) pour ce programme.
title: 'IDebugProgram2 :: GetENCUpdate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 02446dba5450b89b769e773563f77cd6d8c1659f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159898"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Cette méthode obtient la mise à jour de modifier & Continuer (ENC) pour ce programme. Un moteur de débogage personnalisé retourne toujours `E_NOTIMPL`.

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
à Retourne une interface interne qui peut être utilisée pour mettre à jour ce programme.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

> [!NOTE]
> Un moteur de débogage personnalisé doit toujours retourner `E_NOTIMPL` .

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
