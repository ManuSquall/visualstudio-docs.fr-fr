---
title: IEnumDebugPropertyInfo2::Clone | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugPropertyInfo2::Clone
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Clone
ms.assetid: 0ede1667-1071-4aa4-b887-260ea103d724
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7f41f3da2088fa4ec51c048461854333b4d940bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809660"
---
# <a name="ienumdebugpropertyinfo2clone"></a>IEnumDebugPropertyInfo2::Clone
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Retourne une copie de l’énumération actuelle comme un objet distinct.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugPropertyInfo2 ppEnum  
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
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)

