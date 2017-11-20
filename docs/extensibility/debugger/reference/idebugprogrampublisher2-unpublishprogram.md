---
title: IDebugProgramPublisher2::UnpublishProgram | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords: IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 17a2bde6cf83df906a50c4683e0455978060ae22
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
 [in] Un `IUnknown` interface au programme. Cela correspond à la valeur fournie pour le [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) (méthode) et identifie de façon unique le programme en cours de suppression (autrement dit, il est utilisé en tant que cookie).  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Pour rendre un programme disponible pour les moteurs de débogage et le Gestionnaire de session de débogage, utilisez le [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)