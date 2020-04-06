---
title: Exemple de mise en œuvre des sections locales ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b70e0f9091d40ed6b5fc44934606f42ccd84b21
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713076"
---
# <a name="sample-implementation-of-locals"></a>Exemple de mise en œuvre des habitants
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, consultez [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Voici un aperçu de la façon dont Visual Studio obtient les habitants pour une méthode de l’évaluateur d’expression (EE):

1. Visual Studio appelle le moteur de déboug (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) pour obtenir un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet qui représente toutes les propriétés du cadre de pile, y compris les habitants.

2. `IDebugStackFrame2::GetDebugProperty`appelle [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) pour obtenir un objet qui décrit la méthode dans laquelle le point d’arrêt s’est produit. Le DE fournit un fournisseur de symboles ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), une adresse ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)), et un liant ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).

3. `IDebugExpressionEvaluator::GetMethodProperty`appelle [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) avec `IDebugAddress` l’objet fourni pour obtenir un [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) qui représente la méthode contenant l’adresse spécifiée.

4. L’interface `IDebugContainerField` est demandée pour l’interface [IDebugMethodField.](../../extensibility/debugger/reference/idebugmethodfield.md) C’est cette interface qui donne accès aux habitants de la méthode.

5. `IDebugExpressionEvaluator::GetMethodProperty`instantanés une classe `CFieldProperty` (appelée dans l’échantillon) qui exécute l’interface `IDebugProperty2` pour représenter les habitants de la méthode. L’objet `IDebugMethodField` est `CFieldProperty` placé dans `IDebugSymbolProvider`cet `IDebugAddress`objet `IDebugBinder` avec le , , et des objets.

6. Lorsque `CFieldProperty` l’objet est parasécé, `IDebugMethodField` [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) est appelé sur l’objet pour obtenir une structure [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) qui contient toutes les informations displayables sur la méthode elle-même.

7. `IDebugExpressionEvaluator::GetMethodProperty`retourne `CFieldProperty` l’objet `IDebugProperty2` comme objet.

8. Visual Studio appelle [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) sur l’objet retourné `IDebugProperty2` avec le filtre `guidFilterLocalsPlusArgs`, qui renvoie un objet [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contenant les habitants de la méthode. Cette énumération est remplie par des appels à [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) et [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).

9. Visual Studio appelle [Ensuite](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) pour obtenir une structure [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) pour chaque local. Cette structure contient un `IDebugProperty2` pointeur à une interface pour un local.

10. Visual Studio appelle [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) pour chaque local pour obtenir le nom, la valeur et le type du local. Ces informations sont **affichées** dans la fenêtre local.

## <a name="in-this-section"></a>Contenu de cette section
 [Implémentez GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md) Décrit une mise en œuvre de [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Énumérer les habitants](../../extensibility/debugger/enumerating-locals.md) Décrit comment le moteur de débogé (DE) fait un appel pour énumérer les variables locales ou des arguments.

 [Obtenez des propriétés locales](../../extensibility/debugger/getting-local-properties.md) Décrit comment le DE fait un appel pour obtenir le nom, le type et la valeur d’un ou plusieurs habitants.

 [Obtenir des valeurs locales](../../extensibility/debugger/getting-local-values.md) Discute d’obtenir la valeur du local, qui nécessite les services d’un objet de reliure donné par le contexte de l’évaluation.

 [Évaluer les habitants](../../extensibility/debugger/evaluating-locals.md) Explique comment les habitants sont évalués.

## <a name="related-sections"></a>Sections connexes
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md) Fournit les arguments qui sont adoptés lorsque le DE appelle l’évaluateur d’expression (EE).

 [Échantillon MyCEE](https://msdn.microsoft.com/library/624a018b-9179-402f-9d48-3aec87b48f4f) Démontre une approche de mise en œuvre pour créer un évaluateur d’expression pour la langue MyC.

## <a name="see-also"></a>Voir aussi
- [Affichage des habitants](../../extensibility/debugger/displaying-locals.md)
