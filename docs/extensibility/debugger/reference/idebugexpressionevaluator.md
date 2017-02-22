---
title: "IDebugExpressionEvaluator | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator"
helpviewer_keywords: 
  - "Interface de IDebugExpressionEvaluator"
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugExpressionEvaluator
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface représente l’évaluateur d’expression.  
  
## Syntaxe  
  
```  
IDebugExpressionEvaluator : IUnknown  
```  
  
## Notes relatives à l'attention des implémenteurs  
 L’évaluateur d’expression doit implémenter cette interface.  
  
## Remarques pour les appelants  
 Pour obtenir cette interface, instanciez l’évaluateur d’expression via la `CoCreateInstance` méthode à l’aide de l’ID de classe \(CLSID\) de l’évaluateur. Consultez l’exemple.  
  
## Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugExpressionEvaluator`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Convertit une chaîne d’expression en une expression analysée.|  
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Obtient les variables locales, arguments et autres propriétés d’une méthode.|  
|[GetMethodLocationProperty](../Topic/IDebugExpressionEvaluator::GetMethodLocationProperty.md)|Convertit un emplacement de la méthode et le décalage d’une adresse mémoire.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Détermine la langue à utiliser pour créer des résultats imprimables.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Définit la racine du Registre. Utilisé pour le débogage côte à côte.|  
  
## Notes  
 En général, le moteur de débogage \(DE\) instancie l’évaluateur d’expression \(EE\) à la suite d’un appel à [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Étant donné que le DE connaît la langue et le fournisseur de la EE qu’il souhaite utiliser, le D’obtient CLSID du EE à partir du Registre \(la [« Helpers » du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) fonction, `GetEEMetric`, facilite cette récupération\).  
  
 Une fois le EE est instancié, le D’appelle [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour analyser l’expression et le stocker dans un [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) objet. Plus tard, un appel à [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) évalue l’expression.  
  
## Configuration requise  
 En\-tête : ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Exemple  
 Cet exemple montre comment instancier l’évaluateur d’expression avec un fournisseur de symboles et d’une adresse dans le code source. Cet exemple utilise une fonction, `GetEEMetric`, à partir de la [« Helpers » du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) library, dbgmetric.lib.  
  
```cpp#  
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
  
## Voir aussi  
 [Interfaces de l'évaluation d'expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [« Helpers » du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)