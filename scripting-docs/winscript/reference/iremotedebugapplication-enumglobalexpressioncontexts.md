---
title: IRemoteDebugApplication::EnumGlobalExpressionContexts | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a7e4f3e7cffe7c127b7ad4fdde47e58e6bc2a31c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091271"
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