---
title: IRemoteDebugApplication::EnumGlobalExpressionContexts | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.EnumGlobalExpressionContexts
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::EnumGlobalExpressionContexts
ms.assetid: 61598a34-f409-42a2-810d-a9e92e2f4861
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 92ab12dc9944c328e744c7f39252facb8e91a3f7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944270"
---
# <a name="iremotedebugapplicationenumglobalexpressioncontexts"></a>IRemoteDebugApplication::EnumGlobalExpressionContexts
Énumère les contextes d’expression globale pour tous les langages s’exécutant dans cette application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumGlobalExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppedec`  
 [out] Énumérateur qui répertorie les contextes d’expression globale pour tous les langages s’exécutant dans cette application.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode énumère les contextes d’expression globale pour tous les langages s’exécutant dans cette application.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)