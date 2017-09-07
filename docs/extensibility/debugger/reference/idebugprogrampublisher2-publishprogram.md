---
title: IDebugProgramPublisher2::PublishProgram | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 3f573f35ed0130eb020ac2e8e19a0391050ec06e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
Cette méthode rend un programme disponible pour les moteurs de débogage (DEs) et le Gestionnaire de session de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   LPCOLESTR        szFriendlyName,  
   IUnknown*        pDebuggeeInterface  
);  
```  
  
```csharp  
int PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   string           szFriendlyName,  
   object           pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Engines`  
 [in] Un tableau de GUID pour DEs qui peuvent lancer ou attacher à ce programme.  
  
 `szFriendlyName`  
 [in] Nom convivial du programme (il apparaît dans les menus ou les boîtes de dialogue présentées à l’utilisateur).  
  
 `pDebuggeeInterface`  
 [in] `IUnknown` interface du programme (cette valeur est utilisée en tant que cookie pour identifier le programme ; cette même valeur est utilisée pour « annuler la publication » le programme)  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Pour qu’un programme n’est plus disponible pour le débogage, appelez [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)
