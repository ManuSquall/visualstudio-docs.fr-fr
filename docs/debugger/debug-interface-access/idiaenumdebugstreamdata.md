---
title: IDiaEnumDebugStreamData | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumDebugStreamData interface
ms.assetid: e2023c32-4c05-4d0c-a0be-f016a230c788
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3b2424f62db5c77de2030e641093802593f7094
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumdebugstreamdata"></a>IDiaEnumDebugStreamData
Fournit l’accès aux enregistrements dans un flux de données de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaEnumDebugStreamData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDiaEnumDebugStreamData`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaEnumDebugStreamData::get__NewEnum](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-newenum.md)|Récupère le [IEnumVARIANT Interface](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) version de cet énumérateur.|  
|[IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)|Récupère le nombre d’enregistrements dans le flux de données de débogage.|  
|[IDiaEnumDebugStreamData::get_name](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-name.md)|Récupère le nom du flux de données de débogage.|  
|[IDiaEnumDebugStreamData::Item](../../debugger/debug-interface-access/idiaenumdebugstreamdata-item.md)|Récupère l’enregistrement spécifié.|  
|[IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)|Récupère le nombre spécifié d’enregistrements à partir de la séquence d’énumération.|  
|[IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)|Ignore un nombre spécifié d’enregistrements dans une séquence d’énumération.|  
|[IDiaEnumDebugStreamData::Reset](../../debugger/debug-interface-access/idiaenumdebugstreamdata-reset.md)|Réinitialise la séquence d’énumération au début.|  
|[IDiaEnumDebugStreamData::Clone](../../debugger/debug-interface-access/idiaenumdebugstreamdata-clone.md)|Crée un énumérateur qui contient la même séquence énumérée que l’énumérateur actuel.|  
  
## <a name="remarks"></a>Remarques  
 Cette interface représente un flux d’enregistrements dans un flux de données de débogage. La taille et l’interprétation de chaque enregistrement est dépendante sur le flux de données provient de l’enregistrement. Cette interface fournit efficacement l’accès vers les octets de données brutes dans le fichier de symboles.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appelez le [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md) ou [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md) méthodes pour obtenir un `IDiaEnumDebugStreamData` objet.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment accéder à un flux de données et de ses enregistrements.  
  
```C++  
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
  
## <a name="requirements"></a>Spécifications  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)