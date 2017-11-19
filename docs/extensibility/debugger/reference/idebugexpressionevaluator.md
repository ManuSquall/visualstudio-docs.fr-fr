---
title: IDebugExpressionEvaluator | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpressionEvaluator
helpviewer_keywords: IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b7cc2e6c0d25ceebd41648b227405978d1fb67d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface représente l’évaluateur d’expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugExpressionEvaluator : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 L’évaluateur d’expression doit implémenter cette interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Pour obtenir cette interface, l’évaluateur d’expression par le biais d’instancier le `CoCreateInstance` méthode à l’aide de l’ID de classe (CLSID) de l’évaluateur. Consultez l’exemple.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugExpressionEvaluator`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Convertit une chaîne d’expression en une expression analysée.|  
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Obtient les variables locales, arguments et autres propriétés d’une méthode.|  
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Convertit un emplacement de la méthode et le décalage en une adresse mémoire.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Détermine la langue à utiliser pour créer des résultats imprimables.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Définit la racine du Registre. Utilisé pour le débogage côte-à-côte.|  
  
## <a name="remarks"></a>Remarques  
 En général, le moteur de débogage (DE) instancie l’évaluateur d’expression (EE) suite à un appel à [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Car le DE connaît la langue et le fournisseur de l’il souhaite utiliser Java EE, le D’obtient CLSID du EE à partir du Registre (la [programmes d’assistance du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) fonction, `GetEEMetric`, permet de cette récupération).  
  
 Une fois le EE est instancié, le D’appelle [analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour analyser l’expression et les stocker dans un [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) objet. Une version ultérieure, un appel à [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) évalue l’expression.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment instancier l’évaluateur d’expression donné d’un fournisseur de symboles et une adresse dans le code source. Cet exemple utilise une fonction, `GetEEMetric`, à partir de la [programmes d’assistance du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) library, dbgmetric.lib.  
  
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
            CLSID clsidEE      = { 0 };  
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
 [Interfaces de l’évaluation d’expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [Aides SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)