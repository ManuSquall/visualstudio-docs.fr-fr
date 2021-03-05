---
description: Obtient le nom d’utilisateur du fournisseur de port.
title: 'IDebugProcessSecurity :: GetUserName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04ad8bf6ba572a1f9e14e26ef2ca37d021f6e3a0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166201"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Obtient le nom d’utilisateur du fournisseur de port.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetUserName(
    BSTR *pbstrUserName
);
```

```csharp
int GetUserName (
    string pbstrUserName
);
```

## <a name="parameters"></a>Paramètres
`pbstrUserName`\
à Chaîne contenant le nom d’utilisateur.

## <a name="return-value"></a>Valeur renvoyée
 Si la méthode réussit, retourne `S_OK`. Sinon, elle retourne un code d’erreur.

## <a name="remarks"></a>Notes
 `GetUserName` retourne le nom d’utilisateur affiché dans la colonne **nom d’utilisateur** de la boîte de dialogue **attacher au processus** . Pour afficher la boîte de dialogue **attacher au processus** , cliquez sur **attacher au processus** dans le menu **Outils** de l' [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE).

## <a name="see-also"></a>Voir aussi
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
