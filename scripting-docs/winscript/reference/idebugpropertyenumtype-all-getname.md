---
title: IDebugPropertyEnumType_All::GetName | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All.GetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All::GetName
ms.assetid: 24bbe4d5-4263-48d0-8e8d-bff957ffcad2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49b90938630fa96ca91f3346a37a7147ec2b90e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertyenumtypeallgetname"></a>IDebugPropertyEnumType_All::GetName
Retourne une chaîne BSTR contenant le nom de la `EnumType`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetName(  
   BSTR*  pname  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pname`  
 [out] Une chaîne BSTR contenant le nom de la `EnumType`.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un élément valide `HRESULT`, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugPropertyEnumType_All](../../winscript/reference/idebugpropertyenumtype-all-interface.md)