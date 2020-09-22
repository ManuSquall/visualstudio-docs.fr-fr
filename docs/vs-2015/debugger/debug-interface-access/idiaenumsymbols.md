---
title: IDiaEnumSymbols | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols interface
ms.assetid: 649f7bfd-86ac-49a5-8533-aff77e1bc62e
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fae39270cfbbbb93b106de65b3b01210ffc61d29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839490"
---
# <a name="idiaenumsymbols"></a>IDiaEnumSymbols
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Énumère les différents symboles contenus dans la source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaEnumSymbols : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDiaEnumSymbols` .  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaEnumSymbols::get__NewEnum](../../debugger/debug-interface-access/idiaenumsymbols-get-newenum.md)|Récupère la `IEnumVARIANT Interface` version de cet énumérateur.|  
|[IDiaEnumSymbols::get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)|Récupère le nombre de symboles.|  
|[IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)|Récupère un symbole au moyen d’un index.|  
|[IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)|Récupère un nombre spécifié de symboles dans la séquence d’énumération.|  
|[IDiaEnumSymbols::Skip](../../debugger/debug-interface-access/idiaenumsymbols-skip.md)|Ignore un nombre spécifié de symboles dans une séquence d’énumération.|  
|[IDiaEnumSymbols::Reset](../../debugger/debug-interface-access/idiaenumsymbols-reset.md)|Réinitialise une séquence d'énumération.|  
|[IDiaEnumSymbols::Clone](../../debugger/debug-interface-access/idiaenumsymbols-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
  
## <a name="remarks"></a>Remarques  
 Cette interface fournit des symboles regroupés par un type spécifique de symbole, par exemple, `SymTagUDT` (types définis par l’utilisateur) ou `SymTagBaseClass` . Pour travailler avec des symboles regroupés par adresse, utilisez l’interface [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) .  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Obtenez cette interface en appelant les méthodes suivantes :  
  
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
- [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)  
  
## <a name="example"></a> Exemple  
 Cet exemple montre comment obtenir l' `IDiaEnumSymbols` interface, puis utiliser cette énumération pour répertorier les types définis par l’utilisateur (UDT).  
  
> [!NOTE]
> `CDiaBSTR` est une classe qui encapsule un `BSTR` et gère automatiquement la libération de la chaîne lorsque l’instanciation est hors de portée.  
  
```cpp#  
void ShowUDTs(IDiaSymbol *pGlobals)  
{  
    CComPtr<IDiaEnumSymbols> pEnum;  
    CComPtr<IDiaSymbol> pSymbol;  
    HRESULT hr;  
  
    hr = pGlobals->findChildren(SymTagUDT,  
                                NULL,  
                                nsfCaseInsensitive | nsfUndecoratedName,  
                                &pEnum);  
    if (hr == S_OK)  
    {  
        while ( SUCCEEDED( hr = pEnum->Next( 1, &pSymbol, &celt ) ) &&  
                celt == 1 )  
        {  
            CDiaBSTR name;  
            if ( pSymbol->get_name( &name ) != S_OK )  
                Fatal( "get_name" );  
            printf( "Found UDT: %ws\n", name );  
            pSymbol = 0;  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Dia2. h  
  
 Bibliothèque : diaguids. lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (kit de développement logiciel de debug interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession :: Findchildren (](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSourceFile :: get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
