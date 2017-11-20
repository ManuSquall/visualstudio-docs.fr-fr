---
title: IDebugField::GetKind | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::GetKind
helpviewer_keywords: IDebugField::GetKind method
ms.assetid: e7c9c60a-8e55-4ecc-aa63-0c814a1e92cc
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3c1e1a97284bdc7864a9148e451cff5528ea6eb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfieldgetkind"></a>IDebugField::GetKind
Cette méthode obtient le type de champ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetKind(   
   FIELD_KIND* pdwKind  
);  
```  
  
```csharp  
int GetKind(  
   out enum_FIELD_KIND pdwKind  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwKind`  
 [out] Retourne le type de champ sous la forme d’une combinaison de [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) constantes.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)