---
title: IDebugCustomViewer - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c44d2289180ece35725b9258e9d20abeb3a4cac3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732418"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Cette interface permet à un évaluateur d’expression (EE) d’afficher la valeur d’une propriété dans n’importe quel format nécessaire.

## <a name="syntax"></a>Syntaxe

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
Une EE implémente cette interface pour afficher la valeur d’une propriété dans un format personnalisé.

## <a name="notes-for-callers"></a>Notes pour les appelants
Un appel à `CoCreateInstance` la fonction de COM instantanément cette interface. Le `CLSID` passage `CoCreateInstance` est obtenu du registre. Un appel à [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) obtient l’emplacement dans le registre. Voir Remarques pour plus de détails ainsi que l’exemple.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Fait tout ce qui est nécessaire pour afficher une valeur donnée.|

## <a name="remarks"></a>Notes
Cette interface est utilisée lorsque la valeur d’une propriété ne peut pas être affichée par des moyens normaux, par exemple, avec une table de données ou un autre type de propriété complexe. Un visualiseur personnalisé, `IDebugCustomViewer` tel que représenté par l’interface, est différent d’un visualisateur de type, qui est un programme externe pour afficher des données d’un type spécifique indépendamment de l’EE. L’EE implémente un visualiseur personnalisé qui est spécifique à celui EE. Un utilisateur sélectionne le type de visualiseur à utiliser, qu’il s’agit d’un visualiseur de type ou d’un visualiseur personnalisé. Voir [Visualizing and Viewing Data](../../../extensibility/debugger/visualizing-and-viewing-data.md) pour plus de détails sur ce processus.

Un visualiseur personnalisé est enregistré de la même manière qu’un EE et, par conséquent, nécessite un GUID de langue et un GUID fournisseur. La mesure exacte (ou nom d’entrée de registre) n’est connue que de l’EE. Cette mesure est retournée dans la structure [DEBUG_CUSTOM_VIEWER,](../../../extensibility/debugger/reference/debug-custom-viewer.md) qui à son tour est retourné par un appel à [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). La valeur stockée dans `CLSID` la mesure est celle `CoCreateInstance` qui est transmise à la fonction de COM (voir l’exemple).

La fonction [SDK Helpers for Debugging,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetEEMetric`peut être utilisée pour enregistrer un visualiseur personnalisé. Consultez la section de registre `Debugging SDK Helpers` des « évaluateurs d’expression » pour les clés de registre spécifiques dont un spectateur personnalisé a besoin. Notez qu’un visualiseur personnalisé n’a besoin que d’une seule mesure (qui est définie par l’implémentateur de l’EE) alors qu’un évaluateur d’expression nécessite plusieurs mesures prédéfinies.

Normalement, un visualiseur personnalisé fournit une vue de lecture uniquement des données, puisque [l’interface IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) fournie à [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) n’a pas de méthodes pour changer la valeur de la propriété, sauf comme une chaîne. Afin de prendre en charge l’évolution des blocs arbitraires de données, l’EE implémente une interface personnalisée sur le même objet qui implémente l’interface. `IDebugProperty3` Cette interface personnalisée fournirait alors les méthodes nécessaires pour modifier un bloc arbitraire de données.

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Exemple
Cet exemple montre comment obtenir le premier spectateur personnalisé à partir d’une propriété si cette propriété a des téléspectateurs personnalisés.

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
