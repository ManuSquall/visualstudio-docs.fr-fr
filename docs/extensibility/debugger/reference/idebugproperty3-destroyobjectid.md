---
title: IDebugProperty3::DestroyObjectID | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty3::DestroyObjectID
helpviewer_keywords: IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5fdc38d8b337a653b9f8d1481a505dbe8e0cfaa4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Détruit l’ID unique associé à cette propriété, qui indique que l’appelant n’a plus besoin d’identifier cette propriété identifie de façon unique à partir de toutes les autres propriétés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```csharp  
int DestroyObjectID();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Si le moteur de débogage n’a pas besoin prendre en charge des ID uniques pour une propriété (car il déjà suit les identifie de façon unique en interne), puis elle peut simplement retourner `E_NOTIMPL` pour cette méthode.  
  
 Les ID uniques sont créés avec un appel à la [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) méthode lorsque l’appelant veut s’assurer que cette propriété est identifiée de manière unique parmi toutes les autres propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)