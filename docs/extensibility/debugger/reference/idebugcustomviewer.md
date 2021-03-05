---
description: Cette interface permet à un évaluateur d’expression (EE) d’afficher la valeur d’une propriété dans le format requis.
title: IDebugCustomViewer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8d262869d24c50c543159952506a40be753b4be4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150690"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Cette interface permet à un évaluateur d’expression (EE) d’afficher la valeur d’une propriété dans le format requis.

## <a name="syntax"></a>Syntaxe

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
Un EE implémente cette interface pour afficher la valeur d’une propriété dans un format personnalisé.

## <a name="notes-for-callers"></a>Notes pour les appelants
Un appel à la fonction de COM `CoCreateInstance` instancie cette interface. Le `CLSID` passé à `CoCreateInstance` est obtenu à partir du Registre. Un appel à [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) obtient l’emplacement dans le registre. Consultez la section Notes pour plus d’informations, ainsi que l’exemple.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Fait tout ce qui est nécessaire pour afficher une valeur donnée.|

## <a name="remarks"></a>Notes
Cette interface est utilisée quand la valeur d’une propriété ne peut pas être affichée par le biais d’une méthode normale, par exemple avec une table de données ou un autre type de propriété complexe. Une visionneuse personnalisée, telle qu’elle est représentée par l' `IDebugCustomViewer` interface, est différente d’un visualiseur de type, qui est un programme externe permettant d’afficher les données d’un type spécifique indépendamment du EE. Le EE implémente une visionneuse personnalisée qui est spécifique à cette EE. Un utilisateur sélectionne le type de visualiseur à utiliser, qu’il s’agit d’un visualiseur de type ou d’une visionneuse personnalisée. Pour plus d’informations sur ce processus [, consultez visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

Une visionneuse personnalisée est inscrite de la même façon qu’un EE et, par conséquent, requiert un GUID de langage et un GUID de fournisseur. La métrique exacte (ou le nom de l’entrée de registre) est connue uniquement du EE. Cette métrique est retournée dans la structure [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) , qui à son tour est retournée par un appel à [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). La valeur stockée dans la mesure est le `CLSID` qui est passé à la `CoCreateInstance` fonction de com (Voir l’exemple).

Les [applications auxiliaires du kit de développement logiciel (SDK) pour la fonction de débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , `SetEEMetric` , peuvent être utilisées pour inscrire une visionneuse personnalisée. Consultez la section Registre « évaluateur d’expression » de `Debugging SDK Helpers` pour connaître les clés de Registre spécifiques dont a besoin une visionneuse personnalisée. Notez qu’une visionneuse personnalisée n’a besoin que d’une seule mesure (définie par l’implémenteur de EE) tandis qu’un évaluateur d’expression nécessite plusieurs mesures prédéfinies.

Normalement, une visionneuse personnalisée fournit une vue en lecture seule des données, étant donné que l’interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) fournie à [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) n’a aucune méthode permettant de modifier la valeur de la propriété, sauf en tant que chaîne. Afin de prendre en charge la modification des blocs de données arbitraires, EE implémente une interface personnalisée sur le même objet qui implémente l' `IDebugProperty3` interface. Cette interface personnalisée fournit ensuite les méthodes nécessaires pour modifier un bloc de données arbitraire.

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Exemple
Cet exemple montre comment obtenir la première visionneuse personnalisée à partir d’une propriété si cette propriété a des visionneuses personnalisées.

```cpp
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)
{
    // This string is typically defined globally.  For this example, it
    // is defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugCustomViewer *pViewer = NULL;
    if (pProperty != NULL) {
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);
        if (pProperty3 != NULL) {
            HRESULT hr;
            ULONG viewerCount = 0;
            hr = pProperty3->GetCustomViewerCount(&viewerCount);
            if (viewerCount > 0) {
                ULONG viewersFetched = 0;
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };
                hr = pProperty3->GetCustomViewerList(0,
                                                     1,
                                                     &viewerInfo,
                                                     &viewersFetched);
                if (viewersFetched == 1) {
                    CLSID clsidViewer = { 0 };
                    CComPtr<IDebugCustomViewer> spCustomViewer;
                    // Get the viewer's CLSID from the registry.
                    ::GetEEMetric(viewerInfo.guidLang,
                                  viewerInfo.guidVendor,
                                  viewerInfo.bstrMetric,
                                  &clsidViewer,
                                  strRegistrationRoot);
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {
                        // Instantiate the custom viewer.
                        spCustomViewer.CoCreateInstance(clsidViewer);
                        if (spCustomViewer != NULL) {
                            pViewer = spCustomViewer.Detach();
                        }
                    }
                }
            }
        }
    }
    return(pViewer);
}
```

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [Programmes d’assistance SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
