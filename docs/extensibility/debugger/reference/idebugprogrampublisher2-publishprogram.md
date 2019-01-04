---
title: IDebugProgramPublisher2::PublishProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eeaa86ae2a740a1a31147f7294fd91bdbf5872d2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53991043"
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
Cette méthode effectue un programme est disponible pour les moteurs de débogage (DEs) et le Gestionnaire de session de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   LPCOLESTR        szFriendlyName,  
   IUnknown*        pDebuggeeInterface  
);  
```  
  
```csharp  
int PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   string           szFriendlyName,  
   object           pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Engines`  
 [in] Un tableau de GUID pour DEs qui peut lancer ou à associer à ce programme.  
  
 `szFriendlyName`  
 [in] Nom convivial pour le programme (apparaît dans les menus ou les boîtes de dialogue présentées à l’utilisateur).  
  
 `pDebuggeeInterface`  
 [in] `IUnknown` interface pour le programme (cette valeur est utilisée en tant que cookie pour identifier le programme ; cette même valeur est utilisée pour « annuler la publication « le programme)  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Pour un programme n’est plus disponible pour le débogage, appelez [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)