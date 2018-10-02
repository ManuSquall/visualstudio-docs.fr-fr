---
title: IDebugProcess2::Terminate | Microsoft Docs
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
- IDebugProcess2::Terminate
helpviewer_keywords:
- IDebugProcess2::Terminate
ms.assetid: 5e6bf373-0fe9-4321-b04a-473a65f664d9
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a8bdecaf6b9aa0b978affdd653ba9d982f6e2002
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508649"
---
# <a name="idebugprocess2terminate"></a>IDebugProcess2::Terminate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugProcess2::Terminate](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocess2-terminate).  
  
Met fin au processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Lorsqu’un processus est terminé, tous les programmes au sein de ce processus sont terminent ; Aucun sont autorisés à exécuter le code plus.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

