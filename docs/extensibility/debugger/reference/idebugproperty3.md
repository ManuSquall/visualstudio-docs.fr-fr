---
title: "IDebugProperty3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3"
helpviewer_keywords: 
  - "Interface de IDebugProperty3"
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProperty3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface fournit une prise en charge pour :  
  
-   Extrayant arbitrairement une longue chaîne associée à la propriété.  
  
-   Associer un identificateur unique à la propriété.  
  
-   Récupérer une liste de visionneuses personnalisées pour la propriété.  
  
-   Définir la valeur d'une propriété avec la capacité à stocker toutes erreurs résultante  
  
## Syntaxe  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage implémente cette interface sur le même objet qui implémente [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) de fournir une prise en charge des chaînes longues, les identificateurs de propriété, et des visionneuses personnalisées.  
  
## Remarques pour les appelants  
 Appelez [QueryInterface](/visual-cpp/atl/queryinterface) à une interface de `IDebugProperty2` pour obtenir cette interface.  
  
## méthodes en commande de Vtable  
 Outre les méthodes héritées de `IDebugProperty2`, l'interface `IDebugProperty3` expose les méthodes suivantes.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Retourne la longueur de la chaîne associée à la propriété.|  
|[GetStringChars](../Topic/IDebugProperty3::GetStringChars.md)|Retourne la chaîne dans une mémoire tampon fournie par l'utilisateur.|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|crée un identificateur unique pour cette propriété.|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|détruit l'identificateur unique pour cette propriété.|  
|[GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md)|retourne le nombre de visionneuses personnalisées que cette propriété peut être affichée avec.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Retourne la liste des visionneuses personnalisées que cette propriété peut être affichée avec.|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Définit la valeur de cette propriété, qui retourne un message d'erreur si un élément disparaissait erroné.|  
  
## Notes  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) est la meilleure méthode pour que le gestionnaire de débogage de session \(SDM\) afin de définir une valeur de propriété.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)