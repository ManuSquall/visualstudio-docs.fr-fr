---
title: Visualisation et visualisation des données (en anglais seulement) Microsoft Docs
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
ms.openlocfilehash: 2b5f984e6c6a3c1c8f3835dfa93a8679ae16680a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712379"
---
# <a name="visualizing-and-viewing-data"></a>Visualisation et visualisation des données
Les visualisateurs de type et les téléspectateurs personnalisés présentent des données d’une manière qui est rapidement significative pour un développeur. L’évaluateur d’expression (EE) peut prendre en charge des visualisateurs de type tiers et fournir ses propres téléspectateurs personnalisés.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]détermine le nombre de visualisateurs de type et de visionneuses personnalisées associés au type de l’objet en appelant la méthode [GetCustomViewerCount.](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) S’il y a au moins un visualiseur de type ou un visualiseur personnalisé disponible, Visual Studio appelle la méthode [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) pour récupérer une liste de ces visualisateurs et téléspectateurs (en fait, une liste de s qui implémente les visualisateurs et les téléspectateurs) et les présente à l’utilisateur.

## <a name="supporting-type-visualizers"></a>Visualisateurs de type de soutien
 Il existe un certain nombre d’interfaces que l’EE doit mettre en œuvre pour prendre en charge les visualisateurs de type. Ces interfaces peuvent être divisées en deux grandes catégories : les interfaces qui répertorient les visualisateurs et les interfaces de type qui accèdent aux données de la propriété.

### <a name="listing-type-visualizers"></a>Liste des visualisateurs de type
 L’EE prend en charge l’inscription `IDebugProperty3::GetCustomViewerCount` `IDebugProperty3::GetCustomViewerList`des visualisateurs de type dans sa mise en œuvre et . Ces méthodes passent l’appel aux méthodes correspondantes [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) et [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).

 [L’IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) est obtenu en appelant [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Cette méthode nécessite l’interface [IDebugBinder3,](../../extensibility/debugger/reference/idebugbinder3.md) qui est obtenue à partir de l’interface [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) passé à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService`nécessite également les interfaces [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) et [IDebugAddress,](../../extensibility/debugger/reference/idebugaddress.md) qui ont été transmises à `IDebugParsedExpression::EvaluateSync`. L’interface finale requise `IEEVisualizerService` pour créer l’interface est l’interface [IEEVisualizerDataProvider,](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) que l’EE met en œuvre. Cette interface permet d’apporter des modifications à la propriété en cours de visualisation. Toutes les données de propriété sont encapsulées dans une interface [IDebugObject,](../../extensibility/debugger/reference/idebugobject.md) qui est également implémentée par l’EE.

### <a name="accessing-property-data"></a>Accès aux données de la propriété
 L’accès aux données de propriété se fait via l’interface [IPropertyProxyEESide.](../../extensibility/debugger/reference/ipropertyproxyeeside.md) Pour obtenir cette interface, Visual Studio appelle [QueryInterface](/cpp/atl/queryinterface) sur l’objet de propriété pour obtenir [l’interface IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) (implémentée sur le même objet qui `IPropertyProxyEESide` implémente [l’interface IDebugProperty3)](../../extensibility/debugger/reference/idebugproperty3.md) et appelle ensuite la méthode [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) pour obtenir l’interface.

 Toutes les données transmises `IPropertyProxyEESide` dans et hors de l’interface sont encapsulées dans l’interface [IEEDataStorage.](../../extensibility/debugger/reference/ieedatastorage.md) Cette interface représente un éventail d’octets et est implémentée par Visual Studio et eE. Lorsque les données d’une propriété doivent être `IEEDataStorage` modifiées, Visual Studio crée un objet contenant les nouvelles données `IEEDataStorage` et appelle [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) avec cet objet de données afin d’obtenir un nouvel objet qui, à son tour, est passé à [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) pour mettre à jour les données de la propriété. `IPropertyProxyEESide::CreateReplacementObject`permet à l’EE d’instantanéiser sa `IEEDataStorage` propre classe qui implémente l’interface.

## <a name="supporting-custom-viewers"></a>Soutenir les téléspectateurs personnalisés
 Le `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` drapeau est `dwAttrib` placé dans le champ de la structure [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) (retourné par un appel à [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) pour indiquer que l’objet a un spectateur personnalisé associé à elle. Lorsque ce drapeau est défini, Visual Studio obtient [l’interface IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) à partir de [l’interface IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) à l’aide [de QueryInterface](/cpp/atl/queryinterface).

 Si l’utilisateur sélectionne un visualiseur personnalisé, Visual Studio instantanéise le visualiseur personnalisé en utilisant le spectateur `CLSID` fourni par la `IDebugProperty3::GetCustomViewerList` méthode. Visual Studio appelle ensuite [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) pour montrer la valeur à l’utilisateur.

 Normalement, `IDebugCustomViewer::DisplayValue` présente une vue de lecture uniquement des données. Pour permettre des modifications des données, l’EE doit implémenter une interface personnalisée qui prend en charge la modification des données sur un objet de propriété. La `IDebugCustomViewer::DisplayValue` méthode utilise cette interface personnalisée pour prendre en charge la modification des données. La méthode recherche l’interface `IDebugProperty2` personnalisée sur `pDebugProperty` l’interface passée en tant qu’argument.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Soutenir à la fois les visualisateurs de type et les téléspectateurs personnalisés
 Une EE peut prendre en charge les deux visualisateurs de type et les téléspectateurs personnalisés dans les méthodes [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) et [GetCustomViewerList.](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Tout d’abord, l’EE ajoute le nombre de téléspectateurs personnalisés qu’il fournit à la valeur retournée par la méthode [GetCustomViewerCount.](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) Deuxièmement, l’EE `CLSID`joint le s de ses propres téléspectateurs personnalisés à la liste retournée par la méthode [GetCustomViewerList.](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)

## <a name="see-also"></a>Voir aussi
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
- [Type visualisateur et visualiseur personnalisé](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
