---
title: 'IDebugProcess2 :: GetAttachedSessionName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a4692fdbc08655553a829c0f44037221f2e8b410
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907861"
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

## <a name="return-value"></a>Valeur de retour
 Cette méthode doit toujours retourner `E_NOTIMPL` .

## <a name="see-also"></a>Voir aussi
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
