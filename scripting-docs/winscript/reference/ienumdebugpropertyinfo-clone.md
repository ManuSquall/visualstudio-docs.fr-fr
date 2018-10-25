---
title: IEnumDebugPropertyInfo::Clone | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Clone
ms.assetid: ba6bdfdb-4c12-475c-bafc-efa6c109d7ee
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0d172200719a1fe2d95d657fc559f69f7b2ded8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937224"
---
# <a name="ienumdebugpropertyinfoclone"></a>IEnumDebugPropertyInfo::Clone
Crée un énumérateur qui contient le même état d’énumération que l’énumérateur en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Clone (  
   IEnumDebugPropertyInfo** ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppEnum`  
 [out] Retourne le cloné `IEnumDebugPropertyInfo` interface.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une liste valide `HRESULT`, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)