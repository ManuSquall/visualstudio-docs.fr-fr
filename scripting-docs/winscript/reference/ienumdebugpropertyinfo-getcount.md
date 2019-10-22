---
title: 'IEnumDebugPropertyInfo :: GetCount | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.GetCount
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::GetCount
ms.assetid: 83a3becd-8533-4880-9c4f-193227ff25a9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fea4872761dbc67a297400dba77f660ae2e3076b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574206"
---
# <a name="ienumdebugpropertyinfogetcount"></a>IEnumDebugPropertyInfo::GetCount
Obtient le nombre de structures de `DebugPropertyInfo` dans l’énumérateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetCount (  
   ULONG* pcelt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pcelt`  
 à Retourne le nombre de structures de `DebugPropertyInfo` dans l’énumérateur.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un `HRESULT` valide, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)  
 [Structure DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)