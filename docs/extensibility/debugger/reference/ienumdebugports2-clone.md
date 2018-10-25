---
title: IEnumDebugPorts2::Clone | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPorts2::Clone
helpviewer_keywords:
- IEnumDebugPorts2::Clone
ms.assetid: d5ce77e8-bb99-409a-98fa-20fe5a0de25e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 907fbe3c5ffe6626579d69f86cadc3845107466a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905179"
---
# <a name="ienumdebugports2clone"></a>IEnumDebugPorts2::Clone
Retourne une copie de l’énumération actuelle comme un objet distinct.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Clone(  
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppEnum`  
 [out] Retourne une copie de cette énumération en tant qu’objet distinct.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 La copie de l’énumération a le même état que l’original au moment de que cette méthode est appelée. Toutefois, les États de la copie et la version d’origine sont distincts et peuvent être modifiées individuellement.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)