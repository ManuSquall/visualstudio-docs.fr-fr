---
description: Expose les détails d’un frame de pile.
title: IDiaFrameData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData interface
ms.assetid: 2f1b4986-341b-4641-89a4-226e261e9d93
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 66899ff42c870606f6d41d17d920a21f84031eee
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148457"
---
# <a name="idiaframedata"></a>IDiaFrameData
Expose les détails d’un frame de pile.

## <a name="syntax"></a>Syntaxe

```
IDiaFrameData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant présente les méthodes de `IDiaFrameData` .

|Méthode|Description|
|------------|-----------------|
|[IDiaFrameData::get_addressSection](../../debugger/debug-interface-access/idiaframedata-get-addresssection.md)|Récupère la partie de la section de l’adresse de code du frame.|
|[IDiaFrameData::get_addressOffset](../../debugger/debug-interface-access/idiaframedata-get-addressoffset.md)|Récupère la partie d’offset de l’adresse de code pour le frame.|
|[IDiaFrameData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaframedata-get-relativevirtualaddress.md)|Récupère l’adresse virtuelle relative (RVA) de l’image du code pour le frame.|
|[IDiaFrameData::get_virtualAddress](../../debugger/debug-interface-access/idiaframedata-get-virtualaddress.md)|Récupère l’adresse virtuelle (VA) du code du frame.|
|[IDiaFrameData::get_lengthBlock](../../debugger/debug-interface-access/idiaframedata-get-lengthblock.md)|Récupère la longueur, en octets, du bloc de code décrit par le frame.|
|[IDiaFrameData::get_lengthLocals](../../debugger/debug-interface-access/idiaframedata-get-lengthlocals.md)|Récupère le nombre d’octets de variables locales faisant l’objet d’un push sur la pile.|
|[IDiaFrameData::get_lengthParams](../../debugger/debug-interface-access/idiaframedata-get-lengthparams.md)|Récupère le nombre d’octets de paramètres faisant l’objet d’un push sur la pile.|
|[IDiaFrameData::get_maxStack](../../debugger/debug-interface-access/idiaframedata-get-maxstack.md)|Récupère le nombre maximal d’octets ayant fait l’objet d’un push sur la pile dans le frame.|
|[IDiaFrameData::get_lengthProlog](../../debugger/debug-interface-access/idiaframedata-get-lengthprolog.md)|Récupère le nombre d’octets du code de prologue dans le bloc.|
|[IDiaFrameData::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiaframedata-get-lengthsavedregisters.md)|Récupère le nombre d’octets de registres enregistrés ayant fait l’objet d’un push sur la pile.|
|[IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)|Récupère la chaîne de programme utilisée pour calculer le jeu de registres avant l’appel à la fonction active.|
|[IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)|Récupère un indicateur qui indique que la gestion des exceptions système est en vigueur.|
|[IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)|Récupère un indicateur qui indique que la gestion des exceptions C++ est en vigueur.|
|[IDiaFrameData::get_functionStart](../../debugger/debug-interface-access/idiaframedata-get-functionstart.md)|Récupère un indicateur qui indique que le bloc contient le point d’entrée d’une fonction.|
|[IDiaFrameData::get_allocatesBasePointer](../../debugger/debug-interface-access/idiaframedata-get-allocatesbasepointer.md)|Récupère un indicateur qui indique que le pointeur de base est alloué pour le code de cette plage d’adresses. Cette méthode est déconseillée.|
|[IDiaFrameData::get_type](../../debugger/debug-interface-access/idiaframedata-get-type.md)|Récupère le type de frame spécifique au compilateur.|
|[IDiaFrameData::get_functionParent](../../debugger/debug-interface-access/idiaframedata-get-functionparent.md)|Récupère l’interface de données de frame pour la fonction englobante.|
|[IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)|Effectue le déroulement de la pile et retourne l’état actuel des registres dans une interface de frame de parcours de la pile.|

## <a name="remarks"></a>Notes
 Les détails disponibles pour un cadre sont ceux des points d’exécution dans la plage d’adresses indiquée par l’adresse et la longueur du bloc.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Obtenez cette interface en appelant les méthodes [IDiaEnumFrameData :: Next](../../debugger/debug-interface-access/idiaenumframedata-next.md) ou [IDiaEnumFrameData :: Item](../../debugger/debug-interface-access/idiaenumframedata-item.md) . Pour plus d’informations, consultez l’interface [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) .

## <a name="example"></a>Exemple
 Cet exemple imprime les propriétés d’un `IDiaFrameData` objet. Pour obtenir un exemple d’obtention de l’interface, consultez l’interface [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) `IDiaFrameData` .

```C++
void PrintFrameData(IDiaFrameData* pFrameData){
    DWORD dwSect;
    DWORD dwOffset;
    DWORD cbBlock;
    DWORD cbLocals; // Number of bytes reserved for the function locals
    DWORD cbParams; // Number of bytes reserved for the function arguments
    DWORD cbMaxStack;
    DWORD cbProlog;
    DWORD cbSavedRegs;
    BOOL  bSEH;
    BOOL  bEH;
    BOOL  bStart;
    BSTR  wszProgram;

    if(pFrameData->get_addressSection(&dwSect) == S_OK &&
       pFrameData->get_addressOffset(&dwOffset) == S_OK &&
       pFrameData->get_lengthBlock(&cbBlock) == S_OK &&
       pFrameData->get_lengthLocals(&cbLocals) == S_OK &&
       pFrameData->get_lengthParams(&cbParams) == S_OK &&
       pFrameData->get_maxStack(&cbMaxStack) == S_OK &&
       pFrameData->get_lengthProlog(&cbProlog) == S_OK &&
       pFrameData->get_lengthSavedRegisters(&cbSavedRegs) == S_OK &&
       pFrameData->get_systemExceptionHandling(&bSEH) == S_OK &&
       pFrameData->get_cplusplusExceptionHandling(&bEH) == S_OK &&
       pFrameData->get_functionStart(&bStart) == S_OK )
    {
        wprintf(L"Frame address  : %04X:%08X\n", dwSect, dwOffset);
        wprintf(L"Block size     : 0x%8X\n", cbBlock);
        wprintf(L"Locals size    : 0x%8X\n", cbLocals);
        wprintf(L"Parms size     : 0x%8X\n", cbParams);
        wprintf(L"Max stack used : 0x%8X\n", cbMaxStack);
        wprintf(L"Prolog size    : 0x%8X\n", cbProlog);
        wprintf(L"Saved regs size: 0x%8X\n", cbSavedRegs);
        wprintf(L"System Exception Handling: %c\n", bSEH ? L'Y' : L'N');
        wprintf(L"C++ Exception Handling   : %c\n", bEH ? L'Y' : L'N');
        wprintf(L"Function starts in block : %c\n", bStart ? L'Y' : L'N');

        if (pFrameData->get_program(&wszProgram) == S_OK)
        {
            wprintf(L"Program used for register set: %s\n", wszProgram);
            SysFreeString(wszProgram);
        }
        else
        {
            wprintf(L"\n");
        }
    }
}
```

## <a name="requirements"></a>Configuration requise
En-tête : Dia2. h

Bibliothèque : diaguids. lib

DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)
- [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)
