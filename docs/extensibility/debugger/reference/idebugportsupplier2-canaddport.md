---
title: IDebugPortSupplier2::CanAddPort | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00b1c1303be8ccc326a58a20d132ad38db3b426d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Vérifie qu’un fournisseur de port peut ajouter de nouveaux ports.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CanAddPort(   
   void   
);  
```  
  
```csharp  
int CanAddPort();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Si le port peut être ajouté, retourne `S_OK`; sinon, retourne `S_FALSE` pour indiquer le port n’est peut être ajouté à ce fournisseur de port.  
  
## <a name="remarks"></a>Notes  
 Appelez cette méthode avant d’appeler le [ajouter un port](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) méthode étant donné que la seconde méthode crée le port ainsi que l’ajout, qui peut être une opération longue.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [Ajouter un port](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)