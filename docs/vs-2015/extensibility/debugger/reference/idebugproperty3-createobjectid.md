---
title: 'IDebugProperty3 :: CreateObjectID | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0035faad9078acd70886d597f039c0d8de5ee12f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839414"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crée un ID unique pour cette propriété afin de s’assurer qu’elle est unique parmi toutes les autres propriétés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est appelée lorsque le gestionnaire de débogage de session souhaite s’assurer que cette propriété est identifiée de manière unique parmi toutes les autres propriétés. Le moteur DE débogage (DE) prend en charge cette méthode, sauf si les propriétés qu’elle traite sont déjà identifiées de manière unique. Si le DE ne prend pas en charge cette méthode, il retourne `E_NOTIMPL` .  
  
 Tout ID unique créé avec `CreateObjectID` est détruit lorsque la méthode [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) est appelée ; cela signale également la fin de la nécessité d’identifier cette propriété de manière unique.  
  
> [!NOTE]
> Il n’existe aucune méthode pour récupérer cet ID unique, DE sorte que le peut faire tout ce qu’il souhaite pour des ID uniques lorsque la `CreateObjectID` méthode est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
