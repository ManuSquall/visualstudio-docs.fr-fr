---
title: "IDebugCustomViewer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomViewer"
helpviewer_keywords: 
  - "Interface de IDebugCustomViewer"
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugCustomViewer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface permet à un évaluateur d' \(EE\)expression pour afficher une valeur de propriété dans le format auquel est nécessaire.  
  
## Syntaxe  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## Remarques à l'intention des implémenteurs  
 L'évaluateur d'expression implémente cette interface pour afficher une valeur de propriété dans un format personnalisé.  
  
## Remarques pour les appelants  
 Un appel à la fonction d' `CoCreateInstance` COM instancie cette interface.  `CLSID` passé à `CoCreateInstance` est obtenu à partir de le Registre.  un appel à [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) obtient l'emplacement dans le Registre.  Voir notes pour les détails ainsi que l'exemple.  
  
## méthodes en commande de Vtable  
 Cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Valeur d'affichage](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Fait quelle que soit nécessaire pour afficher une valeur donnée.|  
  
## Notes  
 Cette interface est utilisée lorsqu'une valeur de propriété ne peut pas être affichée par normale moyen\-pour l'exemple, avec une table de données ou un type de propriété complexe différent.  Une visionneuse personnalisée, telle qu'elle est représentée par l'interface d' `IDebugCustomViewer` , est différente d'un visualiseur de type, qui est un programme externe pour afficher des données d'un type spécifique indépendamment de l'évaluateur d'expression.  L'évaluateur d'expression implémente une visionneuse personnalisée qui est spécifique en cette EE.  Un utilisateur sélectionne le type du visualiseur à utiliser, qu'elles touchent un visualiseur de type ou une visionneuse personnalisée.  Consultez [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) pour plus d'informations sur ce processus.  
  
 Une visionneuse personnalisée est stockée de la même façon que l'évaluateur d'expression et, par conséquent, requiert un langage GUID et un fournisseur GUID.  Le nom métrique \(ou d'entrée du Registre\) exact est connu uniquement en EE.  Cette mesure est retourné dans la structure de [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) , qui est ensuite retournée par un appel à [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md).  La valeur signalée dans la métrique est `CLSID` passé à la fonction d' `CoCreateInstance` COM \(consultez l'exemple\).  
  
 La fonction de [« Helpers » du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , `SetEEMetric`, peut être utilisée pour stocker une visionneuse personnalisée.  Consultez la section de Registre « évaluateurs d'expression » d' `Debugging SDK Helpers` pour les clés de Registre spécifiques dont une visionneuse personnalisée a besoin.  Notez qu'une visionneuse personnalisée ne requiert qu'un métrique \(défini par l'implémenteur de l'évaluateur d'expression\) lorsqu'un évaluateur d'expression a besoin de plusieurs métriques prédéfinie.  
  
 Normalement, une visionneuse personnalisée propose une vue en lecture seule de données, étant donné que l'interface d' [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) fournie à [Valeur d'affichage](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) n'a aucune méthode pour modifier la valeur de propriété à l'exception comme une chaîne.  Pour prendre en charge la modification des blocs de données arbitraires, l'évaluateur d'expression implémente une interface personnalisée sur le même objet qui implémente l'interface d' `IDebugProperty3` .  Cette interface personnalisée fournit les méthodes nécessaires pour modifier un bloc arbitraire de données.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Exemple  
 cet exemple montre comment obtenir la première visionneuse personnalisée d'une propriété si cette propriété a des visionneuses personnalisées.  
  
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
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [« Helpers » du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)