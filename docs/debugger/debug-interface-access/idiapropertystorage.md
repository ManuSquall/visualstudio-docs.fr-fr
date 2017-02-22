---
title: "IDiaPropertyStorage | Microsoft Docs"
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
  - "IDiaPropertyStorage (interface)"
ms.assetid: d3197a38-5973-4e56-873e-4f1b84c3f674
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaPropertyStorage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Permet de lire les propriétés persistantes dans un jeu de propriétés de diamètre.  
  
## Syntaxe  
  
```  
IDiaPropertyStorage : IUnknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDiaPropertyStorage`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaPropertyStorage::Enum](../../debugger/debug-interface-access/idiapropertystorage-enum.md)|Obtient un pointeur vers un énumérateur pour les propriétés de cet ensemble.|  
|[IDiaPropertyStorage::ReadBOOL](../../debugger/debug-interface-access/idiapropertystorage-readbool.md)|Lit les valeurs d' `BOOL` dans un jeu de propriétés.|  
|[IDiaPropertyStorage::ReadBSTR](../../debugger/debug-interface-access/idiapropertystorage-readbstr.md)|Lit les valeurs d' `BSTR` dans un jeu de propriétés.|  
|[IDiaPropertyStorage::ReadDWORD](../../debugger/debug-interface-access/idiapropertystorage-readdword.md)|Lit les valeurs d' `DWORD` dans un jeu de propriétés.|  
|[IDiaPropertyStorage::ReadLONG](../../debugger/debug-interface-access/idiapropertystorage-readlong.md)|Lit les valeurs d' `LONG` dans un jeu de propriétés.|  
|[IDiaPropertyStorage::ReadMultiple](../../debugger/debug-interface-access/idiapropertystorage-readmultiple.md)|Lit les valeurs de propriété dans un jeu de propriétés.|  
|[IDiaPropertyStorage::ReadPropertyNames](../../debugger/debug-interface-access/idiapropertystorage-readpropertynames.md)|Obtient les noms de chaîne correspondants pour les identificateurs donnés de propriété.|  
|[IDiaPropertyStorage::ReadULONGLONG](../../debugger/debug-interface-access/idiapropertystorage-readulonglong.md)|Lit les valeurs d' `ULONGLONG` dans un jeu de propriétés.|  
  
## Notes  
 chaque propriété dans un jeu de propriétés est identifiée par un identificateur de propriété \(ID\), une valeur de quatre octets d' `ULONG` unique à celle définit.  Les propriétés exposées via l'interface d' `IDiaPropertyStorage` correspondent aux propriétés disponibles dans l'interface parente.  Par exemple, les propriétés de l'interface d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) sont accessibles par nom via l'interface d' `IDiaPropertyStorage` \(notez, cependant, qui bien que la propriété puisse être accessible, il ne signifie pas la propriété est valide pour un objet particulier d' `IDiaSymbol` \).  
  
## Remarques pour les appelants  
 obtenez cette interface en appelant la méthode d' `QueryInterface` sur une autre interface.  les interfaces suivantes peuvent être interrogées pour l'interface d' `IDiaPropertyStorage` :  
  
-   [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
  
-   [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
  
-   [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
  
-   [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
  
-   [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
  
-   [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
  
-   [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
  
## Exemple  
 Cet exemple illustre une fonction qui affiche toutes les propriétés exposées par l'objet d' `IDiaPropertyStorage` .  Consultez l'interface d' [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) pour obtenir un exemple de la façon dont l'interface d' `IDiaPropertyStorage` est fournie par l'interface d' [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) .  
  
```cpp#  
void PrintPropertyStorage(IDiaPropertyStorage* pPropertyStorage)  
{  
    IEnumSTATPROPSTG* pEnumProps;  
    STATPROPSTG       prop;  
    DWORD             celt = 1;  
  
    if (pPropertyStorage->Enum(&pEnumProps) == S_OK)  
    {  
        while (pEnumProps->Next(celt, &prop, &celt) == S_OK)  
        {  
            PROPSPEC pspec = { PRSPEC_PROPID, prop.propid };  
            PROPVARIANT vt = { VT_EMPTY };  
  
            if (pPropertyStorage->ReadMultiple( 1, &pspec, &vt) == S_OK)  
            {  
                switch( vt.vt ){  
                    case VT_BOOL:  
                        wprintf( L"%32s:\t %s\n", prop.lpwstrName, vt.bVal ? L"true" : L"false" );  
                        break;  
                    case VT_I2:  
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.iVal );  
                        break;  
                    case VT_UI2:  
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.uiVal );  
                        break;  
                    case VT_I4:  
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.intVal );  
                        break;  
                    case VT_UI4:  
                        wprintf( L"%32s:\t 0x%0x\n", prop.lpwstrName, vt.uintVal );  
                        break;  
                    case VT_UI8:  
                        wprintf( L"%32s:\t 0x%x\n", prop.lpwstrName, vt.uhVal.QuadPart );  
                        break;  
                    case VT_BSTR:  
                        wprintf( L"%32s:\t %s\n", prop.lpwstrName, vt.bstrVal );  
                        break;  
                    case VT_UNKNOWN:  
                        wprintf( L"%32s:\t %p\n", prop.lpwstrName, vt.punkVal );  
                        break;  
                    case VT_SAFEARRAY:  
                        break;  
                    default:  
                       break;  
                }  
                VariantClear((VARIANTARG*) &vt);  
            }  
        }  
        pEnumProps->Release();  
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
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)