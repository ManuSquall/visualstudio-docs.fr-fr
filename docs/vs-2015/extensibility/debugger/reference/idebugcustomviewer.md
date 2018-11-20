---
title: IDebugCustomViewer | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6b9e068591961e7eafa9d4fdc588da2694532463
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759510"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface permet à un évaluateur d’expression (EE) pour afficher la valeur d’une propriété dans le format est nécessaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Un EE implémente cette interface pour afficher la valeur d’une propriété dans un format personnalisé.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Un appel à de COM `CoCreateInstance` fonction instancie cette interface. Le `CLSID` transmis à `CoCreateInstance` est obtenu à partir du Registre. Un appel à [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Obtient l’emplacement dans le Registre. Consultez la section Notes pour plus d’informations, ainsi que l’exemple.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Fait le nécessaire pour afficher une valeur donnée.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est utilisée lors de la valeur d’une propriété ne peut pas être affichée par des moyens normaux, par exemple, avec une table de données ou un autre type de propriété complexe. Une visionneuse personnalisée, comme représenté par la `IDebugCustomViewer` l’interface, diffère d’un visualiseur de type, qui est un programme externe pour afficher les données d’un type spécifique, quel que soit le EE. Le EE implémente une visionneuse personnalisée qui est spécifique à ce EE. Un utilisateur sélectionne le type de visualiseur à utiliser, qu’il s’agisse d’un visualiseur de type ou une visionneuse personnalisée. Consultez [visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) pour plus d’informations sur ce processus.  
  
 Une visionneuse personnalisée est inscrit dans la même façon qu’un EE et, par conséquent, requiert un GUID de langage et un GUID de fournisseur. La mesure exacte (ou le nom de l’entrée du Registre) est connue uniquement du EE. Cette mesure est retournée dans le [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) structure, qui à son tour est retourné par un appel à [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). La valeur stockée dans la mesure est la `CLSID` qui est passée à du COM `CoCreateInstance` fonction (voir l’exemple).  
  
 Le [aides SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) (fonction), `SetEEMetric`, peut être utilisé pour inscrire une visionneuse personnalisée. Consultez la section de Registre « Évaluateurs d’Expression » de `Debugging SDK Helpers` pour les clés de Registre spécifique qui a besoin d’une visionneuse personnalisée. Notez qu’une visionneuse personnalisée doit uniquement une métrique (qui est définie par le responsable de l’implémentation de la EE) alors qu’un évaluateur d’expression requiert plusieurs métriques prédéfinies.  
  
 En règle générale, une visionneuse personnalisée fournit une vue en lecture seule des données, puisque le [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface fournie à [une valeur d’affichage](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) ne possède aucune méthode pour la modification de la valeur de propriété, sauf sous forme de chaîne. Pour prendre en charge la modification des blocs arbitraires de données, le EE implémente une interface personnalisée sur le même objet qui implémente le `IDebugProperty3` interface. Cette interface personnalisée puis fournit les méthodes nécessaires pour modifier un bloc de données arbitraire.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment obtenir la première visionneuse personnalisée à partir d’une propriété, si cette propriété a des visionneuses personnalisées.  
  
```cpp#  
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
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [Aides SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)

