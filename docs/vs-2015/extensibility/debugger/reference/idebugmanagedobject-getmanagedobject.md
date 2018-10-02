---
title: IDebugManagedObject::GetManagedObject | Microsoft Docs
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
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 13a69db8e3b8a892a441c65f2752607814221667
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506943"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugManagedObject::GetManagedObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmanagedobject-getmanagedobject).  
  
Retourne une interface qui représente l’objet managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetManagedObject(   
   IUnknown** ppManagedObject  
);  
```  
  
```cpp#  
int GetManagedObject(  
   out object ppManagedObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppManagedObject`  
 [out] Retourne une interface qui représente l’objet managé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 L’interface retournée par cette méthode peut être interrogée pour n’importe quelle interface implémentée par la classe managée, ce qui permet de ses méthodes à appeler.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)

