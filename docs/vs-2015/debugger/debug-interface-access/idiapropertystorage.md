---
title: IDiaPropertyStorage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage interface
ms.assetid: d3197a38-5973-4e56-873e-4f1b84c3f674
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 29832934b848729879ee1ba802c70f85117efd2a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60080376"
---
# <a name="idiapropertystorage"></a>IDiaPropertyStorage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous permet de lire les propriétés persistantes d’un jeu de propriétés DIA.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaPropertyStorage : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDiaPropertyStorage`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaPropertyStorage::Enum](../../debugger/debug-interface-access/idiapropertystorage-enum.md)|Obtient un pointeur vers un énumérateur pour les propriétés au sein de cet ensemble.|  
|[IDiaPropertyStorage::ReadBOOL](../../debugger/debug-interface-access/idiapropertystorage-readbool.md)|Lit `BOOL` valeurs dans un jeu de propriétés.|  
|[IDiaPropertyStorage::ReadBSTR](../../debugger/debug-interface-access/idiapropertystorage-readbstr.md)|Lit `BSTR` valeurs dans un jeu de propriétés.|  
|[IDiaPropertyStorage::ReadDWORD](../../debugger/debug-interface-access/idiapropertystorage-readdword.md)|Lit `DWORD` valeurs dans un jeu de propriétés.|  
|[IDiaPropertyStorage::ReadLONG](../../debugger/debug-interface-access/idiapropertystorage-readlong.md)|Lit `LONG` valeurs dans un jeu de propriétés.|  
|[IDiaPropertyStorage::ReadMultiple](../../debugger/debug-interface-access/idiapropertystorage-readmultiple.md)|Lit les valeurs de propriété dans un jeu de propriétés.|  
|[IDiaPropertyStorage::ReadPropertyNames](../../debugger/debug-interface-access/idiapropertystorage-readpropertynames.md)|Obtient correspondant de noms de chaîne pour donné des identificateurs de propriété.|  
|[IDiaPropertyStorage::ReadULONGLONG](../../debugger/debug-interface-access/idiapropertystorage-readulonglong.md)|Lit `ULONGLONG` valeurs dans un jeu de propriétés.|  
  
## <a name="remarks"></a>Notes  
 Chaque propriété dans un jeu de propriétés est identifiée par un identificateur (ID), de la propriété quatre octets `ULONG` valeur unique à cet ensemble. Les propriétés exposées par le biais du `IDiaPropertyStorage` interface correspondent à celles disponibles dans l’interface parente. Par exemple, les propriétés de la [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) interface peut être accédée par nom via la `IDiaPropertyStorage` interface (Notez toutefois que même si la propriété peut être accessible, cela ne signifie pas la propriété est valide pour un particulier `IDiaSymbol` objet).  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Obtenez cette interface en appelant le `QueryInterface` méthode sur une autre interface. Les interfaces suivantes peuvent être interrogées pour le `IDiaPropertyStorage` interface :  
  
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
  
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
  
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
  
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
  
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
  
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
  
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
  
## <a name="example"></a>Exemple  
 Cet exemple montre une fonction qui affiche toutes les propriétés exposées par le `IDiaPropertyStorage` objet. Consultez le [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interface pour obtenir un exemple montrant comment les `IDiaPropertyStorage` interface est obtenue à partir de la [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) interface.  
  
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
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (Kit SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
