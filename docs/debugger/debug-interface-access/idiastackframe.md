---
title: "IDiaStackFrame | Microsoft Docs"
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
  - "IDiaStackFrame (interface)"
ms.assetid: 486d25b8-a590-41c1-bdb5-faff3ae35632
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# IDiaStackFrame
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

expose les propriétés d'un frame de pile.  
  
## Syntaxe  
  
```  
IDiaStackFrame : IUnknown  
```  
  
## méthodes en commande de Vtable  
 Voici les méthodes prises en charge par cette interface :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDiaStackFrame::get\_allocatesBasePointer](../../debugger/debug-interface-access/idiastackframe-get-allocatesbasepointer.md)|Extrait une balise qui indique que le pointeur de base est alloué pour le code dans cette plage d'adresses.  Cette méthode est déconseillée.|  
|[IDiaStackFrame::get\_base](../../debugger/debug-interface-access/idiastackframe-get-base.md)|Extrait la base de l'adresse du frame.|  
|[IDiaStackFrame::get\_cplusplusExceptionHandling](../Topic/IDiaStackFrame::get_cplusplusExceptionHandling.md)|Extrait une balise qui indique cette gestion des exceptions C\+\+ est appliquée.|  
|[IDiaStackFrame::get\_functionStart](../../debugger/debug-interface-access/idiastackframe-get-functionstart.md)|Extrait une balise qui indique que le bloc contient le point d'entrée d'une fonction.|  
|[IDiaStackFrame::get\_lengthLocals](../../debugger/debug-interface-access/idiastackframe-get-lengthlocals.md)|Récupère le nombre d'octets de variables locales qui font l'objet d'un push sur la pile.|  
|[IDiaStackFrame::get\_lengthParams](../../debugger/debug-interface-access/idiastackframe-get-lengthparams.md)|Récupère le nombre d'octets de paramètres l'objet d'un push sur la pile.|  
|[IDiaStackFrame::get\_lengthProlog](../../debugger/debug-interface-access/idiastackframe-get-lengthprolog.md)|Récupère le nombre d'octets du code de prologue dans le bloc|  
|[IDiaStackFrame::get\_lengthSavedRegisters](../Topic/IDiaStackFrame::get_lengthSavedRegisters.md)|Récupère le nombre d'octets de registres stockés l'objet d'un push sur la pile.|  
|[IDiaStackFrame::get\_localsBase](../../debugger/debug-interface-access/idiastackframe-get-localsbase.md)|Extrait la base de l'adresse des variables locales.|  
|[IDiaStackFrame::get\_maxStack](../../debugger/debug-interface-access/idiastackframe-get-maxstack.md)|Récupère le nombre maximal d'octets l'objet d'un push sur la pile dans le frame.|  
|[IDiaStackFrame::get\_rawLVarInstanceValue](../../debugger/debug-interface-access/idiastackframe-get-rawlvarinstancevalue.md)|Récupère la valeur de la variable locale spécifiée en tant qu'octets bruts.|  
|[IDiaStackFrame::get\_registerValue](../../debugger/debug-interface-access/idiastackframe-get-registervalue.md)|extrait la valeur d'un registre spécifié.|  
|[IDiaStackFrame::get\_returnAddress](../../debugger/debug-interface-access/idiastackframe-get-returnaddress.md)|Récupère l'adresse de retour du frame.|  
|[IDiaStackFrame::get\_size](../Topic/IDiaStackFrame::get_size.md)|Extrait la taille du cadre en octets.|  
|[IDiaStackFrame::get\_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)|Extrait une balise qui indique cette gestion des exceptions du système est appliquée.|  
|[IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)|Récupère le type de frame.|  
  
## Notes  
 un frame de pile est une abstraction d'un appel de fonction pendant son exécution.  
  
## Remarques pour les appelants  
 obtenez cette interface en appelant la méthode d' [IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md) .  Consultez l'interface d' [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) pour obtenir un exemple de l'obtention `IDiaStackFrame` pour relier.  
  
## Exemple  
 Cet exemple affiche divers attributs d'un frame de pile.  
  
```cpp#  
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
  
## Configuration requise  
 en\-tête : Dia2.h  
  
 bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## Voir aussi  
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)