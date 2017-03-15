---
title: "IDiaEnumDebugStreamData | Microsoft Docs"
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
  - "IDiaEnumDebugStreamData (interface)"
ms.assetid: e2023c32-4c05-4d0c-a0be-f016a230c788
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaEnumDebugStreamData
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

permet d'accéder aux enregistrements dans un flux de données de débogage.  
  
## Syntaxe  
  
```  
IDiaEnumDebugStreamData : IUnknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDiaEnumDebugStreamData`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaEnumDebugStreamData::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-newenum.md)|Récupère la version d' [IEnumVARIANT Interface](http://msdn.microsoft.com/fr-fr/139e3c93-faef-4003-9079-e0e94494db3e) de cet énumérateur.|  
|[IDiaEnumDebugStreamData::get\_Count](../Topic/IDiaEnumDebugStreamData::get_Count.md)|Récupère le nombre d'enregistrements dans le flux de données de débogage.|  
|[IDiaEnumDebugStreamData::get\_name](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-name.md)|extrait le nom du flux de données de débogage.|  
|[IDiaEnumDebugStreamData::Item](../../debugger/debug-interface-access/idiaenumdebugstreamdata-item.md)|extrait l'enregistrement spécifié.|  
|[IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)|Récupère le nombre d'enregistrements spécifié de la séquence énumérée.|  
|[IDiaEnumDebugStreamData::Skip](../Topic/IDiaEnumDebugStreamData::Skip.md)|Ignore un nombre d'enregistrements spécifié dans une séquence énumérée.|  
|[IDiaEnumDebugStreamData::Reset](../../debugger/debug-interface-access/idiaenumdebugstreamdata-reset.md)|réinitialise la séquence énumérée au début.|  
|[IDiaEnumDebugStreamData::Clone](../../debugger/debug-interface-access/idiaenumdebugstreamdata-clone.md)|Crée un énumérateur qui contient la même séquence énumérée que l'énumérateur actuel.|  
  
## Notes  
 cette interface représente un flux de données des enregistrements dans un flux de données de débogage.  La taille et la traduction de chaque enregistrement dépend du flux de données que l'enregistrement provient de.  Cette interface permet d'accéder efficacement à des octets de données brutes dans le fichier de symboles.  
  
## Remarques pour les appelants  
 appelez les méthodes d' [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md) ou d' [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md) pour obtenir un objet d' `IDiaEnumDebugStreamData` .  
  
## Exemple  
 Cet exemple montre comment accéder à un flux unique et à ses enregistrements.  
  
```cpp#  
void PrintStreamData(IDiaEnumDebugStreamData* pStream)  
{  
    BSTR  wszName;  
    LONG  dwElem;  
    ULONG celt    = 0;  
    DWORD cbData;  
    DWORD cbTotal = 0;  
    BYTE  data[1024];  
  
    if(pStream->get_name(&wszName) != S_OK)  
    {  
        wprintf_s(L"ERROR - PrintStreamData() get_name\n");  
    }  
    else  
    {  
        wprintf_s(L"Stream: %s", wszName);  
        SysFreeString(wszName);  
    }  
    if(pStream->get_Count(&dwElem) != S_OK)  
    {  
        wprintf(L"ERROR - PrintStreamData() get_Count\n");  
    }  
    else  
    {  
        wprintf(L"(%d)\n", dwElem);  
    }  
    while(pStream->Next(1, sizeof(data), &cbData, (BYTE *)&data, &celt) == S_OK)  
    {  
        DWORD i;  
        for (i = 0; i < cbData; i++)  
        {  
            wprintf(L"%02X ", data[i]);  
            if(i && i % 8 == 7 && i+1 < cbData)  
            {  
                wprintf(L"- ");  
            }  
        }  
        wprintf(L"| ");  
        for(i = 0; i < cbData; i++)  
        {  
            wprintf(L"%c", iswprint(data[i]) ? data[i] : '.');  
        }  
        wprintf(L"\n");  
        cbTotal += cbData;  
    }  
    wprintf(L"Summary :\n\tSizeof(Elem) = %d\n\tNo of Elems = %d\n\n",  
            cbTotal/dwElem, dwElem);  
}  
```  
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## Voir aussi  
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)