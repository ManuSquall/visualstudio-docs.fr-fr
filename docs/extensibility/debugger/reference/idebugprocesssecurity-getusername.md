---
title: IDebugProcessSecurity::GetUserName (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef00a0b7489c3e5cb709520546f3d3f26c8a4eba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723261"
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
[out] Une chaîne contenant le nom d’utilisateur.

## <a name="return-value"></a>Valeur de retour
 Si la méthode réussit, retourne `S_OK`. Sinon, il renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 `GetUserName`renvoie le nom d’utilisateur qui s’affiche dans la colonne nom de **l’utilisateur** de la boîte de dialogue **Attach to Process.** Pour voir la boîte de dialogue **Attach to Process,** cliquez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] sur Attach to **Process** sur le menu **Tools** dans l’environnement de développement intégré (IDE).

## <a name="see-also"></a>Voir aussi
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
