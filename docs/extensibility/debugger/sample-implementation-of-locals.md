---
title: "Exemple d’implémentation de variables locales | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3e8157d6ecede516ca1dcb2900cf081c11a2b790
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="sample-implementation-of-locals"></a>Exemple d’implémentation des variables locales
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Voici une vue d’ensemble de la façon dont Visual Studio obtient les variables locales pour une méthode à partir de l’évaluateur d’expression (EE) :  
  
1.  Visual Studio appelle le moteur de débogage (Allemagne) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) pour obtenir un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet qui représente toutes les propriétés du frame de pile, y compris les variables locales.  
  
2.  `IDebugStackFrame2::GetDebugProperty`appels [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) pour obtenir un objet qui décrit la méthode dans laquelle le point d’arrêt s’est produite. Le DE fournit un fournisseur de symboles ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), une adresse ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) et un classeur ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty`appels [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) avec fourni `IDebugAddress` objet à obtenir un [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) représentant la méthode qui contient l’adresse spécifiée.  
  
4.  Le `IDebugContainerField` interface est interrogé pour déterminer le [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interface. Il est cette interface permet d’accéder aux variables locales de la méthode.  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty`instancie une classe (appelée `CFieldProperty` dans l’exemple) qui implémente le `IDebugProperty2` interface pour représenter les variables locales de la méthode. Le `IDebugMethodField` objet est placé dans cette `CFieldProperty` de l’objet avec la `IDebugSymbolProvider`, `IDebugAddress` et `IDebugBinder` objets.  
  
6.  Lorsque le `CFieldProperty` objet est initialisé, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) est appelée sur le `IDebugMethodField` pour obtenir un [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) structure qui contient toutes les informations peut être affichées sur la méthode elle-même .  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty`Retourne le `CFieldProperty` de l’objet en un `IDebugProperty2` objet.  
  
8.  Appels de Visual Studio [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) sur retourné `IDebugProperty2` objet avec le filtre `guidFilterLocalsPlusArgs`. Cette opération retourne un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objet contenant des variables locales de la méthode. Cette énumération est renseignée par les appels à [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) et [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Appels de Visual Studio [suivant](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) pour obtenir un [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) structure pour chaque local. Cette structure contient un pointeur vers un `IDebugProperty2` interface pour une variable locale.  
  
10. Appels de Visual Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) pour chaque local obtenir le nom de l’ordinateur local, valeur et type. Ce sont les informations qui s’affiche dans le **variables locales** fenêtre.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Implémentation de GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Décrit une implémentation de [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Énumération de variables locales](../../extensibility/debugger/enumerating-locals.md)  
 Explique comment le moteur de débogage (DE) permet à un appel à énumérer les variables locales ou les arguments.  
  
 [Obtention des propriétés locales](../../extensibility/debugger/getting-local-properties.md)  
 Décrit comment le D’effectue un appel pour obtenir le nom, le type et la valeur des variables locales d’un ou plusieurs.  
  
 [Obtention des valeurs locales](../../extensibility/debugger/getting-local-values.md)  
 Décrit l’obtention de la valeur de la variable locale, ce qui nécessite les services d’un objet de classeur fourni par le contexte d’évaluation.  
  
 [Évaluation des variables locales](../../extensibility/debugger/evaluating-locals.md)  
 Explique comment les variables locales sont évaluées.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md)  
 Fournit les arguments qui sont passées au moment de la D’appelle l’évaluateur d’expression (EE).  
  
 [Exemple de MyCEE](http://msdn.microsoft.com/en-us/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Illustre une approche d’implémentation à la création d’un évaluateur d’expression pour la langue MyC.  
  
## <a name="see-also"></a>Voir aussi  
 [Affichage des variables locales](../../extensibility/debugger/displaying-locals.md)