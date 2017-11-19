---
title: IDebugPortPicker::SetSite | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4853d9ea3517cc5b589c6a9435b89a69738006d2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Définit le fournisseur de services.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetSite(  
   IServiceProvider * pSP  
);  
```  
  
```csharp  
public int SetSite(  
   IServiceProvider pSP  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pSP`  
 [in] Référence à l’interface du fournisseur de services.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est appelée avant que toutes les autres méthodes sont appelées.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)