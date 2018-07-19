---
title: IPropertyProxyEESide::CreateReplacementObject | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56e5001d7abd498982361a51d0386db4b2624cf7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135594"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Crée une copie d’un objet de données spécifiques à l’évaluateur d’expression (EE).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dataIn`  
 [in] Un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objet contenant les données à copier.  
  
 `dataOut`  
 [out] Retourne un nouveau `IEEDataStorage` objet.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode reçoit un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objet qui représente un tableau d’octets. Cet objet de données entrantes n’est pas généralement implémenté par le Java EE. Toutefois, l’objet retourné par cette méthode est toujours implémenté par EE, ce qui vous permet du mettre en œuvre EE la `IEEDataStorage` interface sur toute classe est souhaitée.  
  
 Notez que les données fournies en entrant `IEEDataStorage` objet doit être les mêmes données dans la sortie `IEEDataStorage` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)