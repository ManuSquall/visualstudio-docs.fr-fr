---
title: "IDiaEnumInjectedSources | Microsoft Docs"
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
  - "IDiaEnumInjectedSources (interface)"
ms.assetid: f97e2392-22e1-48da-b7ce-ad94c8b684b0
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaEnumInjectedSources
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

énumérez les différentes sources injectées contenues dans la source de données.  
  
## Syntaxe  
  
```  
IDiaEnumInjectedSources : IUnknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDiaEnumInjectedSources`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaEnumInjectedSources::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenuminjectedsources-get-newenum.md)|Récupère la version d' [IEnumVARIANT Interface](http://msdn.microsoft.com/fr-fr/139e3c93-faef-4003-9079-e0e94494db3e) de cet énumérateur.|  
|[IDiaEnumInjectedSources::get\_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md)|Récupère le nombre de sources injectées.|  
|[IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)|Extrait une source injectée au moyen d'un index.|  
|[IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)|Récupère un nombre spécifié de sources injectées dans la séquence d'énumération.|  
|[IDiaEnumInjectedSources::Skip](../Topic/IDiaEnumInjectedSources::Skip.md)|Ignore un nombre spécifié de sources injectées dans une séquence d'énumération.|  
|[IDiaEnumInjectedSources::Reset](../../debugger/debug-interface-access/idiaenuminjectedsources-reset.md)|réinitialise une séquence d'énumération au début.|  
|[IDiaEnumInjectedSources::Clone](../../debugger/debug-interface-access/idiaenuminjectedsources-clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
  
## Notes  
  
## Remarques pour les appelants  
 Cette interface est obtenue en appelant la méthode d' [IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md) avec le nom d'un fichier source spécifique ou en appelant la méthode d' [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) avec un GUID de l'interface d' `IDiaEnumInjectedSources` .  
  
## Exemple  
 cet exemple montre comment obtenir \(la fonction d' `GetEnumInjectedSources` \) et utiliser \(la fonction d' `DumpAllInjectedSources` \) l'interface d' `IDiaEnumInjectedSources` .  Consultez l'interface d' [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md) pour une implémentation d' `PrintPropertyStorage` s'exécuter.  Pour un autre sortie, consultez l'interface d' [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) .  
  
```cpp#  
  
IDiaEnumInjectedSources* GetEnumInjectedSources(IDiaSession *pSession)  
{  
    IDiaEnumInjectedSources* pUnknown    = NULL;  
    REFIID                   iid         = __uuidof(IDiaEnumInjectedSources);  
    IDiaEnumTables*          pEnumTables = NULL;  
    IDiaTable*               pTable      = NULL;  
    ULONG                    celt        = 0;  
  
    if (pSession->getEnumTables(&pEnumTables) != S_OK)  
    {  
        wprintf(L"ERROR - GetTable() getEnumTables\n");  
        return NULL;  
    }  
    while (pEnumTables->Next(1, &pTable, &celt) == S_OK && celt == 1)  
    {  
        // There is only one table that matches the given iid  
        HRESULT hr = pTable->QueryInterface(iid, (void**)&pUnknown);  
        pTable->Release();  
        if (hr == S_OK)  
        {  
            break;  
        }  
    }  
    pEnumTables->Release();  
    return pUnknown;  
}  
  
void DumpAllInjectedSources( IDiaSession* pSession)  
{  
    IDiaEnumInjectedSources* pEnumInjSources;  
  
    pEnumInjSources = GetEnumInjectedSources(pSession);  
    if (pEnumInjSources != NULL)  
    {  
        IDiaInjectedSource* pInjSource;  
        ULONG celt = 0;  
  
        while(pEnumInjSources->Next(1, &pInjSource, &celt) == S_OK &&  
              celt == 1)  
        {  
            IDiaPropertyStorage *pPropertyStorage;  
            if (pInjSource->QueryInterface(__uuidof(IDiaPropertyStorage),  
                                           (void **)&pPropertyStorage) == S_OK)  
            {  
                PrintPropertyStorage(pPropertyStorage);  
                pPropertyStorage->Release();  
            }  
            pInjSource->Release();  
        }  
        pEnumInjSources->Release();  
    }  
}  
```  
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## Voir aussi  
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)