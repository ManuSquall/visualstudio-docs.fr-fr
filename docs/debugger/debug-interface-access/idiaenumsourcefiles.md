---
title: "IDiaEnumSourceFiles | Microsoft Docs"
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
  - "IDiaEnumSourceFiles (interface)"
ms.assetid: 5c0779a6-a2ea-408a-90da-ebdecf2b83c0
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaEnumSourceFiles
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Énumère les fichiers sources différents contenus dans la source de données.  
  
## Syntaxe  
  
```  
IDiaEnumSourceFiles : IUknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDiaEnumSourceFiles`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaEnumSourceFiles::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsourcefiles-get-newenum.md)|Récupère la version d' `IEnumVARIANT Interface` de cet énumérateur.|  
|[IDiaEnumSourceFiles::get\_Count](../Topic/IDiaEnumSourceFiles::get_Count.md)|Récupère le nombre de fichiers sources.|  
|[IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)|Extrait un fichier source au moyen d'un index.|  
|[IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)|Récupère un nombre spécifié de fichiers sources dans la séquence d'énumération.|  
|[IDiaEnumSourceFiles::Skip](../Topic/IDiaEnumSourceFiles::Skip.md)|Ignore un nombre spécifié de fichiers sources dans une séquence d'énumération.|  
|[IDiaEnumSourceFiles::Reset](../Topic/IDiaEnumSourceFiles::Reset.md)|réinitialise une séquence d'énumération au début.|  
|[IDiaEnumSourceFiles::Clone](../../debugger/debug-interface-access/idiaenumsourcefiles-clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
  
## Notes  
  
## Remarques pour les appelants  
 obtenez cette interface en appelant la méthode d' `QueryInterface` sur un objet d' [IDiaTable](../../debugger/debug-interface-access/idiatable.md) .  Consultez l'exemple pour plus de détails.  
  
## Exemple  
 Cet exemple montre comment obtenir l'interface d' `IDiaEnumSourceFiles` de la liste des tables dans un objet session de diamètre.  Pour obtenir un exemple des informations des fichiers sources d'accès, consultez l'interface d' [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) .  
  
```cpp#  
  
IDiaEnumSourceFiles* GetEnumSourceFiless(IDiaSession *pSession)  
{  
    IDiaEnumSourceFiles * pUnknown    = NULL;  
    REFIID                iid         = __uuidof(IDiaEnumSourceFiles);  
    IDiaEnumTables*       pEnumTables = NULL;  
    IDiaTable*            pTable      = NULL;  
    ULONG                 celt        = 0;  
  
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
```  
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## Voir aussi  
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)