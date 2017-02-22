---
title: "IDiaEnumDebugStreams | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumDebugStreams (interface)"
ms.assetid: 611caf4f-7a5f-4aa4-b909-52feeb3cc752
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaEnumDebugStreams
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

énumère les différents flux de données de débogage contenus dans la source de données.  
  
## Syntaxe  
  
```  
IDiaEnumDebugStreams : IUnknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDiaEnumDebugStreams`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaEnumDebugStreams::get\_\_NewEnum](../Topic/IDiaEnumDebugStreams::get__NewEnum.md)|Récupère la version d' `IEnumVARIANT` de cet énumérateur.|  
|[IDiaEnumDebugStreams::get\_Count](../../debugger/debug-interface-access/idiaenumdebugstreams-get-count.md)|Récupère le nombre de flux de données de débogage.|  
|[IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)|Récupère un flux de données de débogage à l'aide d'un index.|  
|[IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)|Récupère un nombre spécifié de flux de données de débogage dans la séquence d'énumération.|  
|[IDiaEnumDebugStreams::Skip](../../debugger/debug-interface-access/idiaenumdebugstreams-skip.md)|Ignore un nombre spécifié de flux de données de débogage dans une séquence d'énumération.|  
|[IDiaEnumDebugStreams::Reset](../../debugger/debug-interface-access/idiaenumdebugstreams-reset.md)|réinitialise une séquence d'énumération au début.|  
|[IDiaEnumDebugStreams::Clone](../../debugger/debug-interface-access/idiaenumdebugstreams-clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
  
## Notes  
 Le contenu des flux de données de débogage est implémentation\-dépendant et les formats de données ne sont pas documentés.  
  
## Remarques pour les appelants  
 appelez la méthode d' [IDiaSession::getEnumDebugStreams](../Topic/IDiaSession::getEnumDebugStreams.md) pour obtenir un objet d' `IDiaEnumDebugStreams` .  
  
## Exemple  
 Cet exemple montre comment accéder aux flux de données disponibles à cette interface.  Consultez l'interface d' [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) pour une implémentation d' `PrintStreamData` s'exécuter.  
  
```cpp#  
void DumpAllDebugStreams( IDiaSession* pSession)  
{  
    IDiaEnumDebugStreams* pEnumStreams;  
  
    wprintf(L"\n\n*** DEBUG STREAMS\n\n");  
    // Retrieve an enumerated sequence of debug data streams  
    if(pSession->getEnumDebugStreams(&pEnumStreams) == S_OK)  
    {  
        IDiaEnumDebugStreamData* pStream;  
        ULONG celt = 0;  
  
        for(; pEnumStreams->Next(1, &pStream, &celt) == S_OK; pStream = NULL)  
        {  
            PrintStreamData(pStream);  
            pStream->Release();  
        }  
        pEnumStreams->Release();  
    }  
    else  
    {  
      wprintf(L"Failed to get any debug streams!\n");  
    }  
    wprintf(L"\n");  
}  
```  
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## Voir aussi  
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaSession::getEnumDebugStreams](../Topic/IDiaSession::getEnumDebugStreams.md)