---
title: IDebugExpressionEvaluator | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b54b8d4ab6c30bcefe99928409680ed5fa08cb0
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56449851"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Cette interface représente l’évaluateur d’expression.

## <a name="syntax"></a>Syntaxe

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
L’évaluateur d’expression doit implémenter cette interface.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
Pour obtenir cette interface, instanciez l’évaluateur d’expression via la `CoCreateInstance` méthode à l’aide de l’ID de classe (CLSID) de l’évaluateur. Consultez l’exemple.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant présente les méthodes de `IDebugExpressionEvaluator`.

|Méthode|Description|
|------------|-----------------|
|[Analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Convertit une chaîne d’expression en une expression analysée.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Obtient les variables locales, les arguments et les autres propriétés d’une méthode.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Convertit un emplacement de la méthode et le décalage en une adresse mémoire.|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Détermine la langue à utiliser pour créer des résultats imprimables.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Définit la racine du Registre. Utilisé pour le débogage côte à côte.|

## <a name="remarks"></a>Notes
En général, le moteur de débogage (dé) instancie l’évaluateur d’expression (EE) suite à un appel à [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Car le DE sait que la langue et le fournisseur de l’il souhaite utiliser Java EE, l’Allemagne obtient CLSID du EE à partir du Registre (la [aides SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) (fonction), `GetEEMetric`, permet de cette récupération).

Une fois que le EE est instancié, l’Allemagne appelle [analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour analyser l’expression et le stocker dans un [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) objet. Plus tard, un appel à [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) évalue l’expression.

## <a name="requirements"></a>Spécifications
En-tête : ee.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Exemple
Cet exemple montre comment instancier l’évaluateur d’expression étant donné un fournisseur de symboles et une adresse dans le code source. Cet exemple utilise une fonction, `GetEEMetric`, à partir de la [aides SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) library, dbgmetric.lib.

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
[Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)  
[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)  
[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)  
[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)  
[Aides SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
