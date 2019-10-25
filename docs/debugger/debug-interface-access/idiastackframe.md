---
title: IDiaStackFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame interface
ms.assetid: 486d25b8-a590-41c1-bdb5-faff3ae35632
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a54bd52f3783bb0bedc279cffafab2f21e0b0f39
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741559"
---
# <a name="idiastackframe"></a>IDiaStackFrame
Expose les propriétés d’un frame de pile.

## <a name="syntax"></a>Syntaxe

```
IDiaStackFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Voici les méthodes prises en charge par cette interface :

|Méthode|Description|
|------------|-----------------|
|[IDiaStackFrame::get_allocatesBasePointer](../../debugger/debug-interface-access/idiastackframe-get-allocatesbasepointer.md)|Récupère un indicateur qui spécifie que le pointeur de base est alloué pour le code de cette plage d’adresses. Cette méthode est dépréciée.|
|[IDiaStackFrame::get_base](../../debugger/debug-interface-access/idiastackframe-get-base.md)|Récupère la base d’adresse du frame.|
|[IDiaStackFrame::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)|Récupère un indicateur qui spécifie C++ que la gestion des exceptions est en vigueur.|
|[IDiaStackFrame::get_functionStart](../../debugger/debug-interface-access/idiastackframe-get-functionstart.md)|Récupère un indicateur qui spécifie que le bloc contient le point d’entrée d’une fonction.|
|[IDiaStackFrame::get_lengthLocals](../../debugger/debug-interface-access/idiastackframe-get-lengthlocals.md)|Récupère le nombre d’octets de variables locales faisant l’objet d’un push sur la pile.|
|[IDiaStackFrame::get_lengthParams](../../debugger/debug-interface-access/idiastackframe-get-lengthparams.md)|Récupère le nombre d’octets de paramètres faisant l’objet d’un push sur la pile.|
|[IDiaStackFrame::get_lengthProlog](../../debugger/debug-interface-access/idiastackframe-get-lengthprolog.md)|Récupère le nombre d’octets du code de prologue dans le bloc|
|[IDiaStackFrame::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiastackframe-get-lengthsavedregisters.md)|Récupère le nombre d’octets de registres enregistrés ayant fait l’objet d’un push sur la pile.|
|[IDiaStackFrame::get_localsBase](../../debugger/debug-interface-access/idiastackframe-get-localsbase.md)|Récupère la base d’adresse des variables locales.|
|[IDiaStackFrame::get_maxStack](../../debugger/debug-interface-access/idiastackframe-get-maxstack.md)|Récupère le nombre maximal d’octets ayant fait l’objet d’un push sur la pile dans le frame.|
|[IDiaStackFrame::get_rawLVarInstanceValue](../../debugger/debug-interface-access/idiastackframe-get-rawlvarinstancevalue.md)|Récupère la valeur de la variable locale spécifiée comme octets bruts.|
|[IDiaStackFrame::get_registerValue](../../debugger/debug-interface-access/idiastackframe-get-registervalue.md)|Récupère la valeur d’un registre spécifié.|
|[IDiaStackFrame::get_returnAddress](../../debugger/debug-interface-access/idiastackframe-get-returnaddress.md)|Récupère l’adresse de retour du frame.|
|[IDiaStackFrame::get_size](../../debugger/debug-interface-access/idiastackframe-get-size.md)|Récupère la taille du frame en octets.|
|[IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)|Récupère un indicateur qui spécifie que la gestion des exceptions système est en vigueur.|
|[IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)|Récupère le type de frame.|

## <a name="remarks"></a>Notes
Un frame de pile est une abstraction d’un appel de fonction pendant son exécution.

## <a name="notes-for-callers"></a>Notes pour les appelants
Obtenez cette interface en appelant la méthode [IDiaEnumStackFrames :: Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md) . Pour obtenir un exemple d’obtention de l’interface `IDiaStackFrame`, consultez l’interface [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) .

## <a name="example"></a>Exemple
Cet exemple affiche différents attributs d’un frame de pile.

```C++
void PrintStackFrame(IDiaStackFrame* pFrame)
{
    if (pFrame != NULL)
    {
        ULONGLONG bottom = 0;
        ULONGLONG top    = 0;

        if (pFrame->get_base(&bottom) == S_OK &&
            pFrame->get_registerValue( CV_REG_ESP, &top ) == S_OK )
        {
            printf("range = 0x%08I64x - 0x%08I64x\n", bottom, top);
        }

        ULONGLONG returnAddress = 0;
        if (pFrame->get_returnAddress(&returnAddress) == S_OK)
        {
            printf("return address = 0x%08I64x\n", returnAddress);
        }

        DWORD lengthFrame     = 0;
        DWORD lengthLocals    = 0;
        DWORD lengthParams    = 0;
        DWORD lengthProlog    = 0;
        DWORD lengthSavedRegs = 0;
        if (pFrame->get_size(&lengthFrame) == S_OK &&
            pFrame->get_lengthLocals(&lengthLocals) == S_OK &&
            pFrame->get_lengthParams(&lengthParams) == S_OK &&
            pFrame->get_lengthProlog(&lengthProlog) == S_OK &&
            pFrame->get_lengthSavedRegisters(&lengthSavedRegs) == S_OK)
        {
            printf("stack frame size          = 0x%08lx bytes\n", lengthFrame);
            printf("length of locals          = 0x%08lx bytes\n", lengthLocals);
            printf("length of parameters      = 0x%08lx bytes\n", lengthParams);
            printf("length of prolog          = 0x%08lx bytes\n", lengthProlog);
            printf("length of saved registers = 0x%08lx bytes\n", lengthSavedRegs);
        }
    }
}
```

## <a name="requirements"></a>spécifications
En-tête : Dia2. h

Bibliothèque : diaguids. lib

DLL : Msdia80. dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
