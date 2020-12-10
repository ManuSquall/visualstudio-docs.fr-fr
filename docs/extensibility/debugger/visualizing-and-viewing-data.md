---
title: Visualisation et affichage des données | Microsoft Docs
description: Découvrez comment les visualiseurs de type et les visionneuses personnalisées présentent des données à un développeur. L’évaluateur d’expression prend en charge les visualiseurs de types tiers.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 856788546e10e69a8bb7e2787558505937f9effd
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995457"
---
# <a name="visualizing-and-viewing-data"></a>Visualisation et affichage des données
Les visualiseurs de type et les visionneuses personnalisées présentent des données d’une manière qui est rapidement significative pour un développeur. L’évaluateur d’expression (EE) peut prendre en charge des visualiseurs de type tiers et fournir ses propres visionneuses personnalisées.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] détermine le nombre de visualiseurs de type et de visionneuses personnalisées associés au type de l’objet en appelant la méthode [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) . Si au moins un visualiseur de type ou une visionneuse personnalisée est disponible, Visual Studio appelle la méthode [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) pour récupérer une liste de ces visualiseurs et visionneuses (en fait, une liste de s qui implémente les visualiseurs et les visionneuses) et les présente à l’utilisateur.

## <a name="supporting-type-visualizers"></a>Visualiseurs de type de prise en charge
 Il y a un certain nombre d’interfaces que l’EE doit implémenter pour prendre en charge les visualiseurs de type. Ces interfaces peuvent être divisées en deux grandes catégories : les interfaces qui répertorient les visualiseurs de type et les interfaces qui accèdent aux données de propriété.

### <a name="listing-type-visualizers"></a>Affichage des visualiseurs de types
 EE prend en charge la liste des visualiseurs de types dans son implémentation de `IDebugProperty3::GetCustomViewerCount` et `IDebugProperty3::GetCustomViewerList` . Ces méthodes passent l’appel aux méthodes correspondantes [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) et [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).

 Le [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) est obtenu en appelant [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Cette méthode requiert l’interface [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) , qui est obtenue à partir de l’interface [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) passée à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` requiert également les interfaces [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) et [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) , qui ont été passées à `IDebugParsedExpression::EvaluateSync` . La dernière interface requise pour créer l' `IEEVisualizerService` interface est l’interface [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) , que l’EE implémente. Cette interface permet d’apporter des modifications à la propriété en cours de visualisation. Toutes les données de propriété sont encapsulées dans une interface [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) , qui est également implémentée par EE.

### <a name="accessing-property-data"></a>Accès aux données de propriété
 L’accès aux données de propriété s’effectue par le biais de l’interface [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Pour obtenir cette interface, Visual Studio appelle [QueryInterface](/cpp/atl/queryinterface) sur l’objet de propriété pour obtenir l’interface [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) (implémentée sur le même objet qui implémente l’interface [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) ), puis appelle la méthode [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) pour obtenir l' `IPropertyProxyEESide` interface.

 Toutes les données transmises dans et en dehors de l' `IPropertyProxyEESide` interface sont encapsulées dans l’interface [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) . Cette interface représente un tableau d’octets et est implémentée par Visual Studio et le EE. Lorsque les données d’une propriété doivent être modifiées, Visual Studio crée un `IEEDataStorage` objet contenant les nouvelles données et appelle [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) avec cet objet de données afin d’obtenir un nouvel `IEEDataStorage` objet qui, à son tour, est passé à [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) pour mettre à jour les données de la propriété. `IPropertyProxyEESide::CreateReplacementObject` permet à EE d’instancier sa propre classe qui implémente l' `IEEDataStorage` interface.

## <a name="supporting-custom-viewers"></a>Prise en charge des visionneuses personnalisées
 L’indicateur `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` est défini dans le `dwAttrib` champ de la structure [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) (retourné par un appel à [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) pour indiquer que l’objet est associé à une visionneuse personnalisée. Lorsque cet indicateur est défini, Visual Studio obtient l’interface [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) à partir de l’interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) à l’aide de [QueryInterface](/cpp/atl/queryinterface).

 Si l’utilisateur sélectionne une visionneuse personnalisée, Visual Studio instancie la visionneuse personnalisée à l’aide de la visionneuse `CLSID` fournie par la `IDebugProperty3::GetCustomViewerList` méthode. Visual Studio appelle ensuite [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) pour afficher la valeur pour l’utilisateur.

 Normalement, `IDebugCustomViewer::DisplayValue` présente une vue en lecture seule des données. Pour permettre la modification des données, EE doit implémenter une interface personnalisée qui prend en charge la modification des données sur un objet de propriété. La `IDebugCustomViewer::DisplayValue` méthode utilise cette interface personnalisée pour prendre en charge la modification des données. La méthode recherche l’interface personnalisée sur l' `IDebugProperty2` interface passée comme `pDebugProperty` argument.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Prise en charge des visualiseurs de type et des visionneuses personnalisées
 Un EE peut prendre en charge des visualiseurs de type et des visionneuses personnalisées dans les méthodes [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) et [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) . Premièrement, l’EE ajoute le nombre de visionneuses personnalisées qu’il fournit à la valeur retournée par la méthode [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) . Deuxièmement, le EE ajoute à la `CLSID` liste retournée par la méthode [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) les s de ses propres observateurs personnalisés.

## <a name="see-also"></a>Voir aussi
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
- [Visualiseur de type et visionneuse personnalisée](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
