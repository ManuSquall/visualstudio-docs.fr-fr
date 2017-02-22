---
title: "IDiaInjectedSource | Microsoft Docs"
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
  - "IDiaInjectedSource (interface)"
ms.assetid: 75192c5c-812d-4675-9dc5-4c2cff3ba503
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaInjectedSource
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les accès sont injecté code source enregistré dans la source de données de diamètre.  
  
## Syntaxe  
  
```  
IDiaInjectedSource : IUnknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDiaInjectedSource`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaInjectedSource::get\_crc](../../debugger/debug-interface-access/idiainjectedsource-get-crc.md)|Récupère un contrôle de \(CRC\) redondance cyclique calculé des octets de code source.|  
|[IDiaInjectedSource::get\_length](../../debugger/debug-interface-access/idiainjectedsource-get-length.md)|Récupère le nombre d'octets du code.|  
|[IDiaInjectedSource::get\_filename](../../debugger/debug-interface-access/idiainjectedsource-get-filename.md)|Extrait le nom de fichier de la source.|  
|[IDiaInjectedSource::get\_objectFilename](../../debugger/debug-interface-access/idiainjectedsource-get-objectfilename.md)|Récupère le nom de fichier objet auquel la source a été compilée.|  
|[IDiaInjectedSource::get\_virtualFilename](../../debugger/debug-interface-access/idiainjectedsource-get-virtualfilename.md)|Extrait le nom donné au code source non ; autrement dit, le code qui a été injecté.|  
|[IDiaInjectedSource::get\_sourceCompression](../Topic/IDiaInjectedSource::get_sourceCompression.md)|Récupère l'indicateur de la compression de source utilisée.|  
|[IDiaInjectedSource::get\_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)|Récupère les octets de code source.|  
  
## Notes  
 la source injectée est un texte qui est injecté pendant la compilation.  Cela ne signifie pas le préprocesseur `#include` utilisé en C\+\+.  
  
## Remarques pour les appelants  
 obtenez cette interface en appelant les méthodes d' [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md) ou d' [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md) .  Consultez l'interface d' [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) pour obtenir un exemple d'obtenir `IDiaInjectedSource` pour relier.  
  
## Exemple  
 Cet exemple affiche les données disponibles dans l'interface d' `IDiaInjectedSource` .  Pour une approche alternative à l'aide de l'interface d' [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md) , consultez l'exemple de l'interface d' [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) .  
  
```cpp#  
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
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## Voir aussi  
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)   
 [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)