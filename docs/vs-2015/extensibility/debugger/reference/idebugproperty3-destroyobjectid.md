---
title: IDebugProperty3::DestroyObjectID | Microsoft Docs
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
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 012a4fcc8b5ada9208a3d2b4cd65e5e7ae5c225d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494053"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugProperty3::DestroyObjectID](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty3-destroyobjectid).  
  
Détruit l’ID unique associé à cette propriété, indiquant que l’appelant n’a plus besoin d’identifier cette propriété identifie de façon unique à partir de toutes les autres propriétés.  
  
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
 Si le moteur de débogage n’a pas besoin prendre en charge des ID uniques pour une propriété (car il déjà suit les identifie de façon unique en interne), il peut simplement retourner `E_NOTIMPL` pour cette méthode.  
  
 ID uniques est créés avec un appel à la [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) méthode lorsque l’appelant veut s’assurer que cette propriété est identifiée de manière unique parmi toutes les autres propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)

