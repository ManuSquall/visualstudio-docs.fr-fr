---
title: "IDiaImageData | Microsoft Docs"
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
  - "IDiaImageData (interface)"
ms.assetid: b696f350-fc08-4352-9287-a15e87512c1e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaImageData
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Expose les détails des offsets de base d'emplacement et de la mémoire du module ou de l'image.  
  
## Syntaxe  
  
```  
IDiaImageData : IUnknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDiaImageData`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaImageData::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-relativevirtualaddress.md)|Récupère l'emplacement dans la mémoire virtuelle du module relatif à l'application.|  
|[IDiaImageData::get\_virtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-virtualaddress.md)|Récupère l'emplacement dans la mémoire virtuelle de l'image.|  
|[IDiaImageData::get\_imageBase](../../debugger/debug-interface-access/idiaimagedata-get-imagebase.md)|Extrait l'emplacement mémoire où l'image doit être basée.|  
  
## Notes  
 Certains flux de données de débogage \(XDATA, PDATA\) contiennent des copies des données également stockées dans l'image.  ces objets de données de flux peuvent être interrogés pour l'interface d' `IDiaImageData` .  Consultez la section « remarques pour appelants » de cette rubrique pour plus de détails.  
  
## Remarques pour les appelants  
 obtenez cette interface en appelant `QueryInterface` sur un objet d' [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) .  Notez que tous les flux de données de débogage prennent en charge l'interface d' `IDiaImageData` .  Par exemple, les flux actuellement qu'de XDATA et de PDATA prennent en charge l'interface d' `IDiaImageData` .  
  
## Exemple  
 Cet exemple recherche tous les flux de données de débogage pour tout flux de données qui prend en charge l'interface d' `IDiaImageData` .  Si un tel flux de données est trouvé, certaines informations sur ce flux de données sont affichées.  
  
```cpp#  
void ShowImageData(IDiaSession *pSession)  
{  
    if (pSession != NULL)  
    {  
        CComPtr<IDiaEnumDebugStreams> pStreamsList;  
        HRESULT hr;  
  
        hr = pSession->getEnumDebugStreams(&pStreamsList);  
        if (SUCCEEDED(hr))  
        {  
            LONG numStreams = 0;  
            hr = pStreamsList->get_Count(&numStreams);  
            if (SUCCEEDED(hr))  
            {  
                ULONG fetched = 0;  
                for (LONG i = 0; i < numStreams; i++)  
                {  
                    CComPtr<IDiaEnumDebugStreamData> pStream;  
                    hr = pStreamsList->Next(1,&pStream,&fetched);  
                    if (fetched == 1)  
                    {  
                        CComPtr<IDiaImageData> pImageData;  
                        hr = pStream->QueryInterface(__uuidof(IDiaImageData),  
                                                     (void **)&pImageData);  
                        if (SUCCEEDED(hr))  
                        {  
                            CComBSTR name;  
                            hr = pStream->get_name(&name);  
                            if (SUCCEEDED(hr))  
                            {  
                                wprintf(L"Stream %s:\n",(BSTR)name);  
                            }  
                            else  
                            {  
                                wprintf(L"Failed to get name of stream\n");  
                            }  
  
                            ULONGLONG imageBase = 0;  
                            if (pImageData->get_imageBase(&imageBase) == S_OK)  
                            {  
                                wprintf(L"  image base = 0x%0I64x\n",imageBase);  
                            }  
  
                            DWORD relVA = 0;  
                            if (pImageData->get_relativeVirtualAddress(&relVA) == S_OK)  
                            {  
                                wprintf(L"  relative virtual address = 0x%08lx\n",relVA);  
                            }  
  
                            ULONGLONG va = 0;  
                            if (pImageData->get_virtualAddress(&va) == S_OK)  
                            {  
                                wprintf(L"  virtual address = 0x%0I64x\n", va);  
                            }  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## Voir aussi  
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)