---
title: IDebugProperty2::SetValueAsString | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1fb87f1ad075c0bae10c4d154b2c0e0fa2ceb999
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Définit la valeur d’une propriété à partir d’une chaîne donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```csharp  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszValue`  
 [in] Chaîne contenant la valeur à définir.  
  
 `nRadix`  
 [in] Radical d’être utilisé pour interpréter les informations numériques. Cela peut être 0 pour tenter de déterminer la base automatiquement.  
  
 `dwTimeout`  
 [in] Spécifie la durée maximale, en millisecondes, à attendre avant de retourner à partir de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne le code d’erreur. Le tableau suivant répertorie les autres valeurs possibles.  
  
|Value|Description|  
|-----------|-----------------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|La chaîne n’a pas pu être convertie en une valeur de propriété, ou la valeur de propriété ne peut pas définir.|  
|`E_SETVALUE_VALUE_IS_READONLY`|La propriété doit être en lecture seule.|  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)