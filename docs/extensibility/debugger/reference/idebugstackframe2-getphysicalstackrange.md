---
title: IDebugStackFrame2::GetPhysicalStackRange (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3df924c6c8a4373082d61575e4ad8a7ec3f161d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719673"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Obtient une représentation dépendante de la machine de la gamme d’adresses physiques associées à un cadre de pile.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPhysicalStackRange ( 
   UINT64* paddrMin,
   UINT64* paddrMax
);
```

```csharp
int GetPhysicalStackRange ( 
   out ulong paddrMin,
   out ulong paddrMax
);
```

## <a name="parameters"></a>Paramètres
`paddrMin`\
[out] Retourne l’adresse physique la plus basse associée à ce cadre de pile.

`paddrMax`\
[out] Retourne l’adresse physique la plus élevée associée à ce cadre de pile.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 L’information retournée par cette méthode est utilisée par le gestionnaire de déboiffage de session (SDM) pour trier les cadres de pile.

 On suppose que la pile d’appel se développe vers le bas, c’est-à-dire que de nouveaux cadres de pile sont ajoutés à des adresses de mémoire de plus en plus inférieures. Une architecture de temps de course doit fournir des plages de pile physique qui correspondent à cette hypothèse.

## <a name="see-also"></a>Voir aussi
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
