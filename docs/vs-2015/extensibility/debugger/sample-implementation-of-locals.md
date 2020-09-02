---
title: Exemple d’implémentation de variables locales | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e943fd7ba27fe21029bab4d818803186147476e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704890"
---
# <a name="sample-implementation-of-locals"></a>Exemple d’implémentation de variables locales
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Voici une vue d’ensemble de la façon dont Visual Studio obtient les variables locales pour une méthode à partir de l’évaluateur d’expression (EE) :  
  
1. Visual Studio appelle le [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) du moteur de débogage pour récupérer un objet [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) qui représente toutes les propriétés du frame de pile, y compris les variables locales.  
  
2. `IDebugStackFrame2::GetDebugProperty` appelle [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) pour obtenir un objet qui décrit la méthode dans laquelle le point d’arrêt s’est produit. La classe DE fournit un fournisseur de symboles ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), une adresse ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) et un Binder ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3. `IDebugExpressionEvaluator::GetMethodProperty` appelle [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) avec l' `IDebugAddress` objet fourni pour recevoir un [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) représentant la méthode contenant l’adresse spécifiée.  
  
4. L' `IDebugContainerField` interface est interrogée pour l’interface [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) . C’est cette interface qui donne accès aux variables locales de la méthode.  
  
5. `IDebugExpressionEvaluator::GetMethodProperty` instancie une classe (appelée `CFieldProperty` dans l’exemple) qui implémente l' `IDebugProperty2` interface pour représenter les variables locales de la méthode. L' `IDebugMethodField` objet est placé dans cet `CFieldProperty` objet avec les `IDebugSymbolProvider` objets, `IDebugAddress` et `IDebugBinder` .  
  
6. Lorsque l' `CFieldProperty` objet est initialisé, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) est appelé sur l' `IDebugMethodField` objet pour obtenir une structure [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) qui contient toutes les informations affichables sur la méthode elle-même.  
  
7. `IDebugExpressionEvaluator::GetMethodProperty` retourne l' `CFieldProperty` objet sous la forme d’un `IDebugProperty2` objet.  
  
8. Visual Studio appelle [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) sur l' `IDebugProperty2` objet retourné avec le filtre `guidFilterLocalsPlusArgs` . Cela retourne un objet [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contenant les variables locales de la méthode. Cette énumération est remplie par les appels à [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) et [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Visual Studio appelle [Next](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) pour obtenir une structure [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) pour chaque local. Cette structure contient un pointeur vers une `IDebugProperty2` interface pour un local.  
  
10. Visual Studio appelle [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) pour chaque local afin d’obtenir le nom, la valeur et le type de la locale. Il s’agit des informations qui s’affichent dans la fenêtre **variables locales** .  
  
## <a name="in-this-section"></a>Dans cette section  
 [Implémentation de GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Décrit une implémentation de [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Énumération de variables locales](../../extensibility/debugger/enumerating-locals.md)  
 Décrit comment le moteur DE débogage effectue un appel pour énumérer des variables locales ou des arguments.  
  
 [Obtention des propriétés locales](../../extensibility/debugger/getting-local-properties.md)  
 Décrit comment le DE effectue un appel pour obtenir le nom, le type et la valeur d’un ou de plusieurs variables locales.  
  
 [Obtention des valeurs locales](../../extensibility/debugger/getting-local-values.md)  
 Explique comment obtenir la valeur de l’objet local, qui requiert les services d’un objet Binder donné par le contexte d’évaluation.  
  
 [Évaluation des variables locales](../../extensibility/debugger/evaluating-locals.md)  
 Explique comment les variables locales sont évaluées.  
  
## <a name="related-sections"></a>Sections connexes  
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md)  
 Fournit les arguments passés lorsque l’appel DE l’évaluateur d’expression (EE) est passé.  
  
 [Exemple MyCEE](https://msdn.microsoft.com/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Illustre une approche d’implémentation de la création d’un évaluateur d’expression pour le langage MyC.  
  
## <a name="see-also"></a>Voir aussi  
 [Affichage des variables locales](../../extensibility/debugger/displaying-locals.md)
