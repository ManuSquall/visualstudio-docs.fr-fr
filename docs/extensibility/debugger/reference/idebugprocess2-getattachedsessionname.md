---
description: Obtient le nom de la session qui débogue ce processus.
title: 'IDebugProcess2 :: GetAttachedSessionName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 426904f777d65a25b92871767649cb26041e2af8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071543"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Obtient le nom de la session qui débogue ce processus. Un IDE peut afficher ces informations à un utilisateur qui débogue un processus particulier sur un ordinateur particulier.

> [!NOTE]
> Cette méthode est déconseillée et son implémentation doit toujours retourner `E_NOTIMPL` .

## <a name="syntax"></a>Syntaxe

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>Paramètres
`pbstrSessionName`\

## <a name="return-value"></a>Valeur renvoyée
 Cette méthode doit toujours retourner `E_NOTIMPL` .

## <a name="see-also"></a>Voir aussi
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
