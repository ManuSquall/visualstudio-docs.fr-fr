---
title: 'IEnumDebugExtendedPropertyInfo :: Clone | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Clone
ms.assetid: dd645cf6-bfb3-486c-829e-bb91a6639665
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d11aa307342fbb6029f3bc2aed6b652417f4f52d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568905"
---
# <a name="ienumdebugextendedpropertyinfoclone"></a>IEnumDebugExtendedPropertyInfo::Clone
Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Clone (  
   IEnumDebugExtendedPropertyInfo** ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppEnum`  
 à Retourne l’interface de `IEnumDebugExtendedPropertyInfo` clonée.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un `HRESULT` valide, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumDebugExtendedPropertyInfo](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)