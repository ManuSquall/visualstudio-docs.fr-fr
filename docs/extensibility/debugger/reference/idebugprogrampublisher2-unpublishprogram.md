---
title: IDebugProgramPublisher2::UnpublishProgram | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2daec6615f98d6e253e65bdc66cb7f1f545f9857
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822213"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Rend indisponible à déboguer.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UnpublishProgram(  
   IUnknown* pDebuggeeInterface  
);  
```  
  
```csharp  
int UnpublishProgram(  
   object pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pDebuggeeInterface`  
 [in] Un `IUnknown` interface au programme. C’est la même valeur fournie à la [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) (méthode) et identifie de façon unique le programme en cours de suppression (autrement dit, il est utilisé en tant que cookie).  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Pour rendre un programme les moteurs de débogage et le Gestionnaire de session de débogage, utilisez le [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)