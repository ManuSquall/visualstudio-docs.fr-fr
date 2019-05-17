---
title: IDebugProcessSecurity::GetUserName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8340e9fd9e5f38963a9de78e2974404f600deef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917451"
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

#### <a name="parameters"></a>Paramètres
 `pbstrUserName`

 [out] Chaîne contenant le nom d’utilisateur.

## <a name="return-value"></a>Valeur de retour
 Si la méthode réussit, elle retourne `S_OK`. Sinon, elle retourne un code d’erreur.

## <a name="remarks"></a>Notes
 `GetUserName` Retourne le nom d’utilisateur qui s’affiche dans le **nom d’utilisateur** colonne de la **attacher au processus** boîte de dialogue. Pour afficher le **attacher au processus** boîte de dialogue, cliquez sur **attacher au processus** sur le **outils** menu dans le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE).

## <a name="see-also"></a>Voir aussi
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)