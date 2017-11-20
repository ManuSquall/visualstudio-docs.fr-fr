---
title: IDebugAlias::Dispose | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAlias::Dispose
helpviewer_keywords: IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d10b1e45f9970b2bf331b590f709ef0d8cd15bcd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
Marque cet alias pour la suppression.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Dispose();  
```  
  
```csharp  
int Dispose();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Une fois que cette méthode est appelée, l’alias n’est plus disponible.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)