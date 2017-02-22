---
title: "IDebugProgramProvider2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2"
helpviewer_keywords: 
  - "Interface de IDebugProgramProvider2"
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugProgramProvider2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface stockée permet au gestionnaire de débogage de session \(SDM\) pour obtenir des informations sur les programmes qui « ont été émis » via l'interface d' [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) .  
  
## Syntaxe  
  
```  
IDebugProgramProvider2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage implémente cette interface pour fournir des informations sur les programmes en cours.  Cette interface est stockée dans LE section du Registre à l'aide de `metricProgramProvider`métriques, comme décrit dans [« Helpers » du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## Remarques pour les appelants  
 Fonction d' `CoCreateInstance` COM d'appel avec `CLSID` du fournisseur de programme qui est obtenu à partir de le Registre.  Consultez l'exemple.  
  
## méthodes en commande de Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Obtient des informations sur les programmes exécutés, filtré de diverses manières.|  
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Obtient un nœud de programme, donné un identificateur de processus spécifique|  
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Génère un rappel pour le surveiller les événements de fournisseur associés à des genres spécifiques de processus.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Génère des paramètres régionaux pour toutes les ressources spécifiques à une langue requises par le De.|  
  
## Notes  
 Normalement, un processus utilise cette interface pour déterminer sur les programmes s'exécutant dans ce processus.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Exemple  
  
```cpp#  
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)  
{  
    // This is typically defined globally.  For this example, it is  
    // defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugProgramProvider2 *pProvider = NULL;  
    if (pDebugEngineGuid != NULL) {  
        CLSID clsidProvider = { 0 };  
        ::GetMetric(NULL,  
                    metrictypeEngine,  
                    *pDebugEngineGuid,  
                    metricProgramProvider,  
                    &clsidProvider,  
                    strRegistrationRoot);  
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {  
            CComPtr<IDebugProgramProvider2> spProgramProvider;  
            spProgramProvider.CoCreateInstance(clsidProvider);  
            if (spProgramProvider != NULL) {  
                pProvider = spProgramProvider.Detach();  
            }  
        }  
    }  
    return(pProvider);  
}  
```  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [« Helpers » du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)