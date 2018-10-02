---
title: IDebugProgramPublisher2::UnpublishProgram | Microsoft Docs
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
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eac934aa599d8b6ac3ff0b8779002620013f246a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493073"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugProgramPublisher2::UnpublishProgram](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram).  
  
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

