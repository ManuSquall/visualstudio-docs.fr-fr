---
title: IDebugMethodField::EnumLocals | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField::EnumLocals
helpviewer_keywords: IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 451c2ccad7d817946bd3d2c2e83ed27279124f2b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Crée un énumérateur pour les variables locales sélectionnés de la méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pAddress`  
 [in] Un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objet représentant l’adresse de débogage qui sélectionne le contexte ou la portée à partir duquel obtenir les variables locales.  
  
 `ppLocals`  
 [out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) l’objet qui représente une liste des variables locales ; sinon, retourne une valeur null s’il n’y a aucuns variables locales.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ou retourne S_FALSE, s’il n’y a aucuns variables locales. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Uniquement les variables définies dans le bloc qui contient l’adresse de débogage donné sont énumérées. Si toutes les variables locales, y compris les variables locales générées par le compilateur sont nécessaires, appelez le [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) (méthode).  
  
 Une méthode peut contenir plusieurs contextes ou des blocs de portée. Par exemple, la méthode conçue suivante contient trois étendues, les deux blocs internes et le corps de la méthode.  
  
```csharp  
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
  
 Le [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) objet représente le `func` méthode proprement dite. Appel de la `EnumLocals` méthode avec une [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) définie sur le `Inner Scope 1` adresse retourne une énumération qui contient le `temp1` variable, par exemple.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)