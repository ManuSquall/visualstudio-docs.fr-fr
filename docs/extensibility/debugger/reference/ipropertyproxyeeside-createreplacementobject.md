---
title: IPropertyProxyEESide::CreateReplacementObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eb1c2c5478bb24f80646dcaacf64a9e6efb2e425
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988322"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Crée une copie d’un objet de données spécifiques à l’évaluateur d’expression (EE).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dataIn`  
 [in] Un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objet contenant les données à copier.  
  
 `dataOut`  
 [out] Retourne un nouvel `IEEDataStorage` objet.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode reçoit un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objet qui représente un tableau d’octets. Cet objet de données entrantes n’est pas généralement implémenté par le EE. Toutefois, l’objet retourné par cette méthode est toujours implémentée par EE, ce qui vous permet de l’implémenter EE la `IEEDataStorage` interface sur toute classe est souhaitée.  
  
 Notez que les données fournies en entrant `IEEDataStorage` objet doit être les mêmes données dans sortant `IEEDataStorage` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)