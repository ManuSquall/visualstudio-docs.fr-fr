---
description: Obtient une représentation dépendante de l’ordinateur de la plage d’adresses physiques associée à un frame de pile.
title: 'IDebugStackFrame2 :: GetPhysicalStackRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 41664f0e59b0eba6ae8a98599c74bd91fe26cf2a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145922"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Obtient une représentation dépendante de l’ordinateur de la plage d’adresses physiques associée à un frame de pile.

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
à Retourne l’adresse physique la plus basse associée à ce frame de pile.

`paddrMax`\
à Retourne l’adresse physique la plus élevée associée à ce frame de pile.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Les informations retournées par cette méthode sont utilisées par le gestionnaire de débogage de session (SDM) pour trier les frames de pile.

 Il est supposé que la pile des appels augmente, c’est-à-dire que les nouveaux frames de pile sont ajoutés à des adresses mémoire plus basses. Une architecture au moment de l’exécution doit fournir des plages de piles physiques qui correspondent à cette hypothèse.

## <a name="see-also"></a>Voir aussi
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
