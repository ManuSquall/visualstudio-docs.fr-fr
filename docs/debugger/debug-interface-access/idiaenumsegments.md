---
title: "IDiaEnumSegments | Microsoft Docs"
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
  - "IDiaEnumSegments (interface)"
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaEnumSegments
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

énumère les différents segments contenus dans la source de données.  
  
## Syntaxe  
  
```  
IDiaEnumSegments : IUnknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDiaEnumSegments`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaEnumSegments::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|Récupère la version d' [IEnumVARIANT Interface](http://msdn.microsoft.com/fr-fr/139e3c93-faef-4003-9079-e0e94494db3e) de cet énumérateur.|  
|[IDiaEnumSegments::get\_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|Récupère le nombre de segments.|  
|[IDiaEnumSegments::Item](../Topic/IDiaEnumSegments::Item.md)|Récupère un segment au moyen d'un index.|  
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|Récupère un nombre spécifié de segments de la séquence d'énumération.|  
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|Ignore un nombre spécifié de segments dans une séquence d'énumération.|  
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|réinitialise une séquence d'énumération au début.|  
|[IDiaEnumSegments::Clone](../Topic/IDiaEnumSegments::Clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
  
## Notes  
  
## Remarques pour les appelants  
 obtenez cette interface en appelant la méthode d' `QueryInterface` sur un objet d' [IDiaTable](../../debugger/debug-interface-access/idiatable.md) .  Consultez l'exemple pour plus de détails.  
  
## Exemple  
 Cet exemple montre comment obtenir l'interface d' `IDiaEnumSections` d'une table.  Pour un exemple plus complet d'utiliser des segments, consultez l'interface d' [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) .  
  
```cpp#  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                __uuidof( IDiaEnumSegments ),  
                                (void**)&pSegments )  
                  )  
       )  
    {  
        // Do something with this enumeration  
    }  
}  
```  
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## Voir aussi  
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)