---
title: IDebugAlias::GetICorDebugValue | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAlias::GetICorDebugValue
helpviewer_keywords: IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4e23641f246d064dc65c01788bdfb780c0f09869
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Récupère une interface en code managé qui représente la valeur associée à cet alias.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppUnk`  
 [out] `IUnknown` interface qui représente la valeur associée à cet alias. Cette interface peut être interrogée pour la `ICorDebugValue` interface.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode s’applique uniquement aux valeurs managés (le `ICorDebugValue` une interface n’est disponible dans le [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] et est défini dans le [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK dans le fichier cordebug.idl).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)