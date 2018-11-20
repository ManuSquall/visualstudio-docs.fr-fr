---
title: IDebugAlias::GetICorDebugValue | Microsoft Docs
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
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e052a720f73ff6df3f716932dba2a1f8ea87c94
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807671"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Récupère une interface en code managé qui représente la valeur associée à cet alias.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppUnk`  
 [out] `IUnknown` interface qui représente la valeur associée à cet alias. Cette interface peut être interrogée pour la `ICorDebugValue` interface.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode s’applique uniquement aux valeurs gérés (les `ICorDebugValue` une interface n’est disponible dans le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] et est défini dans le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK dans le fichier cordebug.idl).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

