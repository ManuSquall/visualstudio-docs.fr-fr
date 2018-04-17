---
title: IDebugCustomViewer | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fb70365304883abe99a87cfec5e78bbed89f2dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Cette interface permet l’évaluateur d’expression (EE) pour afficher une valeur de propriété dans le format n’est nécessaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un EE implémente cette interface pour afficher une valeur de propriété dans un format personnalisé.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Un appel à COM `CoCreateInstance` fonction instancie cette interface. Le `CLSID` transmis à `CoCreateInstance` est obtenue à partir du Registre. Un appel à [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Obtient l’emplacement dans le Registre. Pour plus d’informations, ainsi que l’exemple, consultez la section Notes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[Valeur d’affichage](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Fait le nécessaire pour afficher une valeur donnée.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est utilisée lorsqu’une valeur de propriété ne peut pas être affichée par des moyens normaux, par exemple, avec une table de données ou un autre type de propriété complexe. Une visionneuse personnalisée, comme représenté par la `IDebugCustomViewer` l’interface, diffère d’un visualiseur de type, qui est un programme externe pour afficher les données d’un type spécifique, quelle que soit la EE. Le EE implémente une visionneuse personnalisée qui est spécifique à cette EE. Un utilisateur sélectionne le type de visualiseur à utiliser, soit un visualiseur de type ou une visionneuse personnalisée. Consultez [Visualizing et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) pour plus d’informations sur ce processus.  
  
 Une visionneuse personnalisée est enregistrée dans la même façon qu’une EE et, par conséquent, requiert une langue GUID et un GUID du fournisseur. La mesure exacte (ou le nom de l’entrée du Registre) est connue uniquement du EE. Cette mesure est retournée dans le [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) structure, qui à son tour, est retourné par un appel à [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). La valeur stockée dans la métrique est la `CLSID` qui est passé à COM `CoCreateInstance` (voir l’exemple).  
  
 Le [programmes d’assistance du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) fonction, `SetEEMetric`, peut être utilisé pour inscrire une visionneuse personnalisée. Consultez la section de Registre « Évaluateurs d’Expression » de `Debugging SDK Helpers` pour les clés de Registre spécifique qui a besoin d’une visionneuse personnalisée. Notez qu’une visionneuse personnalisée doit uniquement une métrique (qui est définie par le responsable de l’implémentation de la EE) alors que l’évaluateur d’expression requiert plusieurs mesures prédéfinies.  
  
 En règle générale, une visionneuse personnalisée fournit une vue en lecture seule des données, depuis le [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface fournie à [une valeur d’affichage](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) n’a aucune méthode permettant de modifier la valeur de propriété, sauf en tant que chaîne. Pour prendre en charge la modification des blocs de données arbitraires, le EE implémente une interface personnalisée sur le même objet qui implémente le `IDebugProperty3` interface. Cette interface personnalisée est ensuite fournir les méthodes nécessaires pour modifier un bloc arbitraire de données.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment obtenir la première visionneuse personnalisée à partir d’une propriété, si cette propriété a les visionneuses personnalisées.  
  
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
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [Programmes d’assistance du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)