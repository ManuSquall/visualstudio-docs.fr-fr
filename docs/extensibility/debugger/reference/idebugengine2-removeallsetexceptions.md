---
title: IDebugEngine2::RemoveAllSetExceptions | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords: IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1412022d5eefffcaab74a33cb76f1580bc910c0d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
Supprime la liste des exceptions, que l’IDE a définie pour un langage ou une architecture d’exécution particulière.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RemoveAllSetExceptions(   
   REFGUID guidType  
);  
```  
  
```csharp  
int RemoveAllSetExceptions(   
   ref Guid guidType  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `guidType`  
 [in] Le GUID pour la langue ou le GUID pour le moteur de débogage est spécifique à une architecture d’exécution.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Les exceptions supprimées par cette méthode ont été définies par des appels antérieurs à la [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) (méthode).  
  
 Pour supprimer une exception spécifique, appelez le [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)