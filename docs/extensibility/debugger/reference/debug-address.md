---
title: DEBUG_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 420f8d6e065fc68077a134f6d7bb677690dc2b57
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972519"
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
Cette structure représente une adresse.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```csharp  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## <a name="terms"></a>Termes  
 ulAppDomainID  
 L’ID de processus.  
  
 guidModule  
 Le GUID du module qui contient cette adresse.  
  
 tokClass  
 Le jeton identifiant la classe ou un type de cette adresse.  
  
> [!NOTE]
>  Cette valeur est spécifique à un fournisseur de symboles et ne possède donc aucun sens général différent en tant qu’identificateur pour un type de classe.  
  
 addr  
 Un [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) structure qui contient une union de structures qui décrivent les types d’adresses individuelles. La valeur `addr`.`dwKind` provient de la [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération, qui explique comment interpréter l’union.  
  
## <a name="remarks"></a>Notes  
 Cette structure est passée à la [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) méthode doit être renseigné.  
  
 **Avertissement (C++ uniquement)**  
  
 Si `addr.dwKind` est `ADDRESS_KIND_METADATA_LOCAL` et si `addr.addr.addrLocal.pLocal` n’est pas une valeur null, vous devez l’appeler `Release` sur le pointeur de jeton :  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)