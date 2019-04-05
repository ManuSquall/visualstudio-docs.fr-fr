---
title: IDebugSettingsCallback2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c3e962c00d6c9230cab765ed56e7607cbfd91765
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952188"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Permet de déboguer les moteurs pour lire les paramètres de mesure à distance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugSettingsCallback2D : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Cette interface est implémentée par le rappel d’événement du Gestionnaire de débogage de session et consommée par les moteurs de débogage. Il peut également servir localement au lieu de Dbgmetric [d] .lib.  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant présente les méthodes de `IDebugSettingsCallback2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Énumère les évaluateurs d’expression disponible étant données les identificateurs de langue et le fournisseur.|  
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Récupère un objet local évaluateur d’expression étant donné la métrique.|  
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Récupère une valeur qui correspond à la mesure spécifiée de l’évaluateur d’expression.|  
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Récupère le fichier de métrique évaluateur expression étant donné le nom ou la mesure.|  
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Récupère l’identificateur unique pour une métrique d’évaluateur d’expression étant donnée son nom.|  
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Récupère la chaîne de valeur d’une métrique d’évaluateur d’expression étant donné son nom.|  
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Récupère la valeur d’une fonction de son nom de métrique.|  
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Récupère l’identificateur unique d’une fonction de son nom de métrique.|  
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Récupère la chaîne de valeur de la métrique de fonction de son nom.|  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une fonction qui accepte un **IDebugSettingsCallback2** objet en tant que paramètre.  
  
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
