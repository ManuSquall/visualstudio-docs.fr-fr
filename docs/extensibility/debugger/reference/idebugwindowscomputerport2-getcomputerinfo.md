---
description: Récupère des informations sur l’ordinateur sur lequel le débogueur est en cours d’exécution.
title: 'IDebugWindowsComputerPort2 :: GetComputerInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetComputerInfo
- IDebugWindowsComputerPort2::GetComputerInfo
ms.assetid: 654910b2-c239-44c8-92fc-317680a5672f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2afc91ee00137889a22763c024b10d5d7788d49c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083464"
---
# <a name="idebugwindowscomputerport2getcomputerinfo"></a>IDebugWindowsComputerPort2::GetComputerInfo
Récupère des informations sur l’ordinateur sur lequel le débogueur est en cours d’exécution.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetComputerInfo(
   COMPUTER_INFO * pInfo
);
```

```csharp
public int GetComputerInfo(
   out COMPUTER_INFO[] pInfo
);
```

## <a name="parameters"></a>Paramètres
`pInfo`\
à Référence à une structure qui contient les informations sur l’ordinateur.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)
- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)
