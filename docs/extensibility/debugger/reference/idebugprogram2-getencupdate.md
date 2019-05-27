---
title: IDebugProgram2::GetENCUpdate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 363018d13cfeee1691881f4d8b814cdd0b2dfa35
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212346"
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
[out] Retourne une interface interne qui peut être utilisée pour mettre à jour de ce programme.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

> [!NOTE]
> Un moteur de débogage personnalisé doit toujours retourner `E_NOTIMPL`.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)