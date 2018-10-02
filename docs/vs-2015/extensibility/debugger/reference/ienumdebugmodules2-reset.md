---
title: IEnumDebugModules2::Reset | Microsoft Docs
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
- IEnumDebugModules2::Reset
helpviewer_keywords:
- IEnumDebugModules2::Reset
ms.assetid: f6ff364c-2644-4919-b950-3cb82eb6f601
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: af060c0375eaf18c3b7bc22e839ddd39fb647248
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508810"
---
# <a name="ienumdebugmodules2reset"></a>IEnumDebugModules2::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IEnumDebugModules2::Reset](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugmodules2-reset).  
  
Réinitialise l’énumération au premier élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Une fois que cette méthode est appelée, l’appel suivant à la [suivant](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) méthode retourne le premier élément de l’énumération.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)

