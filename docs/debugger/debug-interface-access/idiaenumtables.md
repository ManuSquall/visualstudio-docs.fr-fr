---
title: "IDiaEnumTables | Microsoft Docs"
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
  - "IDiaEnumTables (interface)"
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaEnumTables
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Énumère les différents tables contenues dans la source de données.  
  
## Syntaxe  
  
```  
IDiaEnumTables : IUnknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDiaEnumTables`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaEnumTables::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|Récupère la version d' [IEnumVARIANT Interface](http://msdn.microsoft.com/fr-fr/139e3c93-faef-4003-9079-e0e94494db3e) de cet énumérateur.|  
|[IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|Récupère le nombre de tables.|  
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|Récupère un tableau à l'aide d'un index ou d'une étiquette.|  
|[IDiaEnumTables::Next](../Topic/IDiaEnumTables::Next.md)|Récupère un nombre spécifié de tables dans la séquence d'énumération.|  
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|Ignore un nombre spécifié de tables dans une séquence d'énumération.|  
|[IDiaEnumTables::Reset](../Topic/IDiaEnumTables::Reset.md)|réinitialise une séquence d'énumération au début.|  
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
  
## Notes  
  
## Remarques pour les appelants  
 obtenez cette interface en appelant la méthode d' [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) .  
  
## Exemple  
 cet exemple montre comment obtenir l'interface d' `IDiaEnumTables` d'une session.  Pour un exemple plus complet d'utiliser les tableaux, consultez l'interface d' [IDiaTable](../../debugger/debug-interface-access/idiatable.md) .  
  
```cpp#  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    // Do something with table  
}  
```  
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## Voir aussi  
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)