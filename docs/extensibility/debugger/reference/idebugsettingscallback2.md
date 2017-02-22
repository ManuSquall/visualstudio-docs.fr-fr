---
title: "IDebugSettingsCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugSettingsCallback2"
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSettingsCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Permet aux moteurs de débogage pour lire les paramètres métriques à distance.  
  
## Syntaxe  
  
```  
IDebugSettingsCallback2D : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Cette interface est implémentée par le rappel d'événement du gestionnaire de débogage de session et consommée par les moteurs de débogage.  Il peut également être utilisé localement au lieu de Dbgmetric \[d\] .lib.  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes d' `IDebugSettingsCallback2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Énumère les évaluateurs d'expression disponibles donnés les ID de langue et de fournisseur.|  
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Récupère un objet local évaluateur d'expression donné la métrique.|  
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Récupère une valeur qui correspond au métriques spécifié de l'évaluateur d'expression.|  
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Extrait le fichier métriques évaluateur d'expression donné le nom ou la métrique.|  
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Extrait l'identificateur unique pour une métrique évaluateur d'expression avec son nom.|  
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Extrait la chaîne de valeur d'un métriques évaluateur d'expression avec son nom.|  
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Extrait la valeur d'un métriques avec son nom.|  
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Extrait l'identificateur unique d'un métriques avec son nom.|  
|[GetMetricString](../Topic/IDebugSettingsCallback2::GetMetricString.md)|Extrait la chaîne de valeur de la métrique avec son nom.|  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Exemple  
 L'exemple suivant illustre une fonction qui prend un objet **IDebugSettingsCallback2** comme paramètre.  
  
```cpp#  
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppCallback )  
   {  
        if ( EVAL(m_pdec) )  
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```