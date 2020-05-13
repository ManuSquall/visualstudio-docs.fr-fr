---
title: IDebugExpressionEvaluator Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8dd910e4edc110abb40dde14b4cb85ff54a70a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729373"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, veuillez consulter [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

Cette interface représente l’évaluateur d’expression.

## <a name="syntax"></a>Syntaxe

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
L’évaluateur d’expression doit implémenter cette interface.

## <a name="notes-for-callers"></a>Notes pour les appelants
Pour obtenir cette interface, instantanéisez l’évaluateur d’expression à travers la `CoCreateInstance` méthode en utilisant l’ID de classe (CLSID) de l’évaluateur. Voir l’exemple.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant montre `IDebugExpressionEvaluator`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Convertit une chaîne d’expression en une expression analysée.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Obtient les variables locales, les arguments, et d’autres propriétés d’une méthode.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Convertit l’emplacement d’une méthode et se compense en une adresse mémoire.|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Détermine la langue à utiliser pour créer des résultats imprimables.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Définit la racine du registre. Utilisé pour le débogage côte à côte.|

## <a name="remarks"></a>Notes
Dans une situation typique, le moteur de débogé (DE) instantanéise l’évaluateur d’expression (EE) à la suite d’un appel à [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Parce que le DE connaît la langue et le vendeur de l’EE qu’il veut utiliser, le DE obtient le `GetEEMetric`CLSID de l’EE du registre (les aides SDK pour la fonction [Debugging,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , aide à cette récupération).

Une fois l’EE instantanée, le DE appelle [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour analyser l’expression et la stocker dans un objet [IDebugParsedExpression.](../../../extensibility/debugger/reference/idebugparsedexpression.md) Plus tard, un appel à [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) évalue l’expression.

## <a name="requirements"></a>Spécifications
En-tête: ee.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Exemple
Cet exemple montre comment instantané l’évaluateur d’expression donné un fournisseur de symbole et une adresse dans le code source. Cet exemple utilise `GetEEMetric`une fonction, à partir de la [SDK Helpers pour la bibliothèque Debugging,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) dbgmetric.lib.

```cpp
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,
                                                 IDebugAddress *pSourceAddress)
{
    // This is typically defined globally but is specified here just
    // for this example.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";

    IDebugExpressionEvaluator *pEE = NULL;
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {
        HRESULT hr         = S_OK;
        GUID  languageGuid = { 0 };
        GUID  vendorGuid   = { 0 };

        hr = pSymbolProvider->GetLanguage(pSourceAddress,
                                          &languageGuid,
                                          &vendorGuid);
        if (SUCCEEDED(hr)) {
            CLSID clsidEE = { 0 };
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;
            // Get the expression evaluator's CLSID from the registry.
            ::GetEEMetric(languageGuid,
                          vendorGuid,
                          metricCLSID,
                          &clsidEE,
                          strRegistrationRoot);
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {
                // Instantiate the expression evaluator.
                spExpressionEvaluator.CoCreateInstance(clsidEE);
            }
            if (spExpressionEvaluator != NULL) {
                pEE = spExpressionEvaluator.Detach();
            }
        }
    }
    return pEE;
}
```

## <a name="see-also"></a>Voir aussi
- [Interfaces d’évaluation des expressions](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [Programmes d’assistance SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
