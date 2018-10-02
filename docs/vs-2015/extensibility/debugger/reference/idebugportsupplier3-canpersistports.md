---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4f3799e4003edca0ce2722ad1365777f6be7e43c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504322"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugPortSupplier3::CanPersistPorts](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportsupplier3-canpersistports).  
  
Cette méthode détermine si le fournisseur de port peut conserver les ports (en les écrivant sur le disque) entre les appels du débogueur.  
  
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
 `S_OK` Si les ports peuvent être rendus persistants ou `S_FALSE` pour indiquer que les ports ne peut pas être rendue persistante.  
  
## <a name="remarks"></a>Notes  
 Si le fournisseur de port peut conserver les ports, il doit faire lorsqu’il est détruit et les recharger lorsqu’il est instancié une fois encore.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)

