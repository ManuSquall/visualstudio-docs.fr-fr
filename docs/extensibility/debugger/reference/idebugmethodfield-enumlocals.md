---
title: "IDebugMethodField::EnumLocals | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumLocals"
helpviewer_keywords: 
  - "IDebugMethodField::EnumLocals (méthode)"
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugMethodField::EnumLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crée un énumérateur pour les variables locales sélectionnées de la méthode.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### Paramètres  
 `pAddress`  
 \[in\]  Un objet d' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) représentant l'adresse de débogage qui sélectionne le contexte ou la portée dont pour obtenir les données locales.  
  
 `ppLocals`  
 \[out\]  Retourne un objet d' [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant une liste des variables locales ; sinon, retourne une valeur NULL s'il n'y a aucun local.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ou retourne S\_FALSE s'il n'y a aucun local.  Sinon, retourne un code d'erreur.  
  
## Notes  
 Seuls les variables définies dans le bloc qui contient l'adresse donnée de débogage sont énumérées.  Si toutes les heures locales notamment des variables locales générés par le compilateur sont nécessaires, appelez la méthode d' [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) .  
  
 Une méthode peut contenir plusieurs contextes ou blocs de portée.  par exemple, la méthode conçue suivante contient trois portées, les deux blocs internes et le corps de la méthode elle\-même.  
  
```c#  
public void func(int index)  
{  
    // Method body scope  
    int a = 0;  
    if (index == 1)  
    {  
        // Inner scope 1  
        int temp1 = a;  
    }  
    else  
    {  
        // Inner scope 2  
        int temp2 = a;  
    }  
}  
```  
  
 l'objet d' [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) représente la méthode d' `func` elle\-même.  Appelant la méthode d' `EnumLocals` avec [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) défini à l'adresse d' `Inner Scope 1` retourne une énumération contenant la variable d' `temp1` , par exemple.  
  
## Voir aussi  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)