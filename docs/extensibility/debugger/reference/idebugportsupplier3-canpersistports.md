---
title: IDebugPortSupplier3::CanPersistPorts | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords: IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 95e62f283d2ea0411162fb0406c712f0d17a1183
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Cette méthode détermine si le fournisseur de port peut être rendue persistante ports (en les écrivant sur le disque) entre les appels du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK`Si les ports peuvent être rendus persistants ou `S_FALSE` pour indiquer que les ports ne peut pas être persistante.  
  
## <a name="remarks"></a>Remarques  
 Si le fournisseur de port peut être rendue persistante des ports, il doit faire lorsqu’il est détruit et les recharger lorsqu’il est instancié à nouveau.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)