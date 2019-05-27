---
title: IDebugProcess2::GetAttachedSessionName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 84a0969eb93fc2e95449364521662c27bf6f750d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202639"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Obtient le nom de la session qui est le débogage de ce processus. Un IDE peut afficher ces informations à un utilisateur qui est un processus particulier sur un ordinateur particulier de débogage.

> [!NOTE]
> Cette méthode est déconseillée, et son implémentation doit toujours retourner `E_NOTIMPL`.

## <a name="syntax"></a>Syntaxe

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>Paramètres
`pbstrSessionName`\

## <a name="return-value"></a>Valeur de retour
 Cette méthode doit toujours retourner `E_NOTIMPL`.

## <a name="see-also"></a>Voir aussi
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)