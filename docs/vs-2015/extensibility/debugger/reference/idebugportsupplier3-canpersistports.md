---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: edc989771b41cc4a5cc5b4710de4cbb5632873e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188188"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode détermine si le fournisseur de port peut conserver les ports (en les écrivant sur le disque) entre les appels du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucune.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` Si les ports peuvent être rendus persistants ou `S_FALSE` pour indiquer que les ports ne peut pas être rendue persistante.  
  
## <a name="remarks"></a>Notes  
 Si le fournisseur de port peut conserver les ports, il doit faire lorsqu’il est détruit et les recharger lorsqu’il est instancié une fois encore.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
