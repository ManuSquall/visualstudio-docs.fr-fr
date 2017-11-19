---
title: IDiaInjectedSource | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaInjectedSource interface
ms.assetid: 75192c5c-812d-4675-9dc5-4c2cff3ba503
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7beda305bbe0673b6e1b47f0e11eb641ab8aa0d5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiainjectedsource"></a>IDiaInjectedSource
Accède à injection de code source stocké dans la source de données DIA.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaInjectedSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDiaInjectedSource`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaInjectedSource::get_crc](../../debugger/debug-interface-access/idiainjectedsource-get-crc.md)|Récupère une vérification de redondance cyclique (CRC) calculée à partir d’octets du code source.|  
|[IDiaInjectedSource::get_length](../../debugger/debug-interface-access/idiainjectedsource-get-length.md)|Récupère le nombre d’octets de code.|  
|[IDiaInjectedSource::get_filename](../../debugger/debug-interface-access/idiainjectedsource-get-filename.md)|Récupère le nom de fichier pour la source.|  
|[IDiaInjectedSource::get_objectFilename](../../debugger/debug-interface-access/idiainjectedsource-get-objectfilename.md)|Récupère le nom de fichier objet sur lequel la source a été compilée.|  
|[IDiaInjectedSource::get_virtualFilename](../../debugger/debug-interface-access/idiainjectedsource-get-virtualfilename.md)|Récupère le nom donné au code de la source de fichier non ; Autrement dit, le code injecté.|  
|[IDiaInjectedSource::get_sourceCompression](../../debugger/debug-interface-access/idiainjectedsource-get-sourcecompression.md)|Récupère l’indicateur de la compression de la source utilisée.|  
|[IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)|Récupère les octets de code source.|  
  
## <a name="remarks"></a>Remarques  
 Source injecté est le texte qui est injecté pendant la compilation. Cela ne signifie pas que le préprocesseur `#include` utilisé dans C++.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Obtenez cette interface en appelant le [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md) ou [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md) méthodes. Consultez le [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interface pour obtenir un exemple d’obtention de la `IDiaInjectedSource` interface.  
  
## <a name="example"></a>Exemple  
 Cet exemple affiche les données disponibles à partir de la `IDiaInjectedSource` interface. Pour une approche alternative à l’aide de la [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md) l’interface, consultez l’exemple dans le [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interface.  
  
```C++  
void PrintInjectedSource(IDiaInjectedSource* pSource)  
{  
    ULONGLONG codeLength      = 0;  
    DWORD     crc             = 0;  
    DWORD     compressionType = 0;  
    BSTR      sourceFilename  = NULL;  
    BSTR      objectFilename  = NULL;  
    BSTR      virtualFilename = NULL;  
  
    std::cout << "Injected Source:" << std::endl;  
    if (pSource != NULL)  
    {  
        if (pSource->get_crc(&crc) == S_OK &&  
            pSource->get_sourceCompression(&compressionType) == S_OK &&  
            pSource->get_length(&codeLength) == S_OK)  
        {  
            wprintf(L"  crc = %lu\n", crc);  
            wprintf(L"  code length = %I64u\n",codeLength);  
            wprintf(L"  compression type code = %lu\n", compressionType);  
        }  
  
        wprintf(L"  source filename: ");  
        if (pSource->get_filename(&sourceFilename) == S_OK)  
        {  
            wprintf(L"%s", sourceFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        wprintf(L"  object filename: ");  
        if (pSource->get_filename(&objectFilename) == S_OK)  
        {  
            wprintf(L"%s", objectFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        wprintf(L"  virtual filename: ");  
        if (pSource->get_filename(&virtualFilename) == S_OK)  
        {  
            wprintf(L"%s", virtualFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        SysFreeString(sourceFilename);  
        SysFreeString(objectFilename);  
        SysFreeString(virtualFilename);  
    }  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)   
 [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)