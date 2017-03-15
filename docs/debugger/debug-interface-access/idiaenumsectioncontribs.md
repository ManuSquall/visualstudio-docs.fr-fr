---
title: "IDiaEnumSectionContribs | Microsoft Docs"
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
  - "IDiaEnumSectionContribs (interface)"
ms.assetid: 0d6c0632-310f-4a99-8921-58149a1817e3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaEnumSectionContribs
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

énumère les différentes contributions de section contenues dans la source de données.  
  
## Syntaxe  
  
```  
IDiaEnumSectionContribs : IUnknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDiaEnumSectionContribs`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaEnumSectionContribs::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-newenum.md)|Récupère la version d' [IEnumVARIANT Interface](http://msdn.microsoft.com/fr-fr/139e3c93-faef-4003-9079-e0e94494db3e) de cet énumérateur.|  
|[IDiaEnumSectionContribs::get\_Count](../Topic/IDiaEnumSectionContribs::get_Count.md)|Récupère le nombre de contributions de section.|  
|[IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)|Récupère les contributions de section à l'aide d'un index.|  
|[IDiaEnumSectionContribs::Next](../Topic/IDiaEnumSectionContribs::Next.md)|Récupère un nombre spécifié de contributions de section dans la séquence d'énumération.|  
|[IDiaEnumSectionContribs::Skip](../Topic/IDiaEnumSectionContribs::Skip.md)|Ignore un nombre spécifié de contributions de section dans une séquence d'énumération.|  
|[IDiaEnumSectionContribs::Reset](../../debugger/debug-interface-access/idiaenumsectioncontribs-reset.md)|réinitialise une séquence d'énumération au début.|  
|[IDiaEnumSectionContribs::Clone](../../debugger/debug-interface-access/idiaenumsectioncontribs-clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
  
## Notes  
  
## Remarque pour les appelants  
 obtenez cette interface de la méthode d' [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) .  Consultez l'exemple pour plus de détails.  
  
## Exemple  
 cet exemple montre comment obtenir \(la fonction d' `GetEnumSectionContribs` \) et utiliser \(la fonction d' `ShowSectionContribs` \) l'interface d' `IDiaEnumSectionContribs` .  Pour un exemple plus complet d'utiliser des contributions de sections, consultez l'interface d' [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) .  
  
```cpp#  
  
      IDiaEnumSectionContribs* GetEnumSectionContribs(IDiaSession *pSession)  
{  
    IDiaEnumSectionContribs* pUnknown    = NULL;  
    REFIID                   iid         = __uuidof(IDiaEnumSectionContribs);  
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
  
void ShowSectionContribs(IDiaSession *pSession)  
{  
    IDiaEnumSectionContribs* pEnumSectionContribs;  
  
    pEnumSectionContribs = GetEnumSectionContribs(pSession);  
    if (pSectionContrib != NULL)  
    {  
        IDiaSectionContrib* pSectionContrib;  
        ULONG celt = 0;  
  
        while(pEnumSectionContribs->Next(1, &pSectionContrib, &celt) == S_OK &&  
              celt == 1)  
        {  
            PrintSectionContrib(pSectionContrib, pSession);  
            pSectionContrib->Release();  
        }  
        pSectionContrib->Release();   
    }  
}  
```  
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## Voir aussi  
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)