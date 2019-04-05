---
title: IDiaEnumSourceFiles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles interface
ms.assetid: 5c0779a6-a2ea-408a-90da-ebdecf2b83c0
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8b095515be5e3c032667c96d8b13d92aa5995c7f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951350"
---
# <a name="idiaenumsourcefiles"></a>IDiaEnumSourceFiles
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Énumère les différents fichiers sources contenus dans la source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaEnumSourceFiles : IUknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDiaEnumSourceFiles`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaEnumSourceFiles::get__NewEnum](../../debugger/debug-interface-access/idiaenumsourcefiles-get-newenum.md)|Récupère le `IEnumVARIANT Interface` version de cet énumérateur.|  
|[IDiaEnumSourceFiles::get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md)|Récupère le nombre de fichiers sources.|  
|[IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)|Récupère un fichier source au moyen d’un index.|  
|[IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)|Récupère un nombre spécifié de fichiers sources dans la séquence d’énumération.|  
|[IDiaEnumSourceFiles::Skip](../../debugger/debug-interface-access/idiaenumsourcefiles-skip.md)|Ignore un nombre spécifié de fichiers sources dans une séquence d’énumération.|  
|[IDiaEnumSourceFiles::Reset](../../debugger/debug-interface-access/idiaenumsourcefiles-reset.md)|Réinitialise une séquence d’énumération au début.|  
|[IDiaEnumSourceFiles::Clone](../../debugger/debug-interface-access/idiaenumsourcefiles-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur en cours.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Obtenez cette interface en appelant le `QueryInterface` méthode sur un [IDiaTable](../../debugger/debug-interface-access/idiatable.md) objet. Consultez l’exemple pour plus d’informations.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment obtenir le `IDiaEnumSourceFiles` interface à partir de la liste des tables dans un objet de session DIA. Pour obtenir un exemple d’accès aux informations du fichier source, consultez la [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) interface.  
  
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
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (Kit SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
