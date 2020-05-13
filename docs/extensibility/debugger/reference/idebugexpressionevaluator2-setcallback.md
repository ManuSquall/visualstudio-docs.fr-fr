---
title: IDebugExpressionEvaluator2::SetCallback Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 907fdaa928b3f84f6ff37490d5c54a9d48515053
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729337"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Permet à l’évaluateur d’expression (EE) de spécifier l’interface de rappel que le moteur de débogénaire (DE) utilisera pour lire les paramètres métriques.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetCallback (
    IDebugSettingsCallback2* pCallback
);
```

```csharp
int SetCallback (
    IDebugSettingsCallback2 pCallback
);
```

## <a name="parameters"></a>Paramètres
`pCallback`\
[dans] Interface à utiliser pour les paramètres de rappel.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
Cette méthode fournit une interface au gestionnaire de débogé de session qu’un évaluateur d’expression peut utiliser pour lire les paramètres métriques. Il est utile dans le débogage [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] à distance pour lire les mesures sur l’ordinateur.

## <a name="example"></a>Exemple
Les exemples suivants montrent comment implémenter cette méthode pour un objet **CEE** qui expose [l’interface IDebugSettingsCallback2.](../../../extensibility/debugger/reference/idebugsettingscallback2.md)

```cpp
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)
{
    // precondition
    INVARIANT( this );

    // function body
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)
    {
        EEDomain::fSetCallback DomainVal =
        {
            in_pCallback
        };

        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);
        ENSURE( bSuccess );
    }

    // postcondition
    INVARIANT( this );

    return S_OK;
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
