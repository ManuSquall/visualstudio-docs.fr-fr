---
title: 'IDebugExpressionEvaluator2 :: SetCallback | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c9411bc7c3963636c8ad80e5a2bf94dd49bf3e5b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926278"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Active l’évaluateur d’expression (EE) pour spécifier l’interface de rappel que le moteur du débogueur utilisera pour lire les paramètres de métrique.

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
dans Interface à utiliser pour le rappel de paramètres.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
Cette méthode fournit une interface au gestionnaire de débogage de session qu’un évaluateur d’expression peut utiliser pour lire les paramètres de métriques. Il est utile dans le débogage distant pour lire les métriques sur l' [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ordinateur.

## <a name="example"></a>Exemple
Les exemples suivants montrent comment implémenter cette méthode pour un objet **CEE** qui expose l’interface [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) .

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
