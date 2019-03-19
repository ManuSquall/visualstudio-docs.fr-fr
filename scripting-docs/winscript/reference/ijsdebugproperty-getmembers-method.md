---
title: Méthode IJsDebugProperty::GetMembers | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProperty.GetMembers
apilocation:
- jscript9diag.dll
ms.assetid: a32b5372-d9cb-4b9a-9bc2-81b5e1df365c
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3be31a0f02869ea740809fb68dbddf48843b2f3e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146966"
---
# <a name="ijsdebugpropertygetmembers-method"></a>IJsDebugProperty::GetMembers, méthode
Obtient les membres de cet objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetMembers(  
   JS_PROPERTY_MEMBERS members,  
   IJsEnumDebugProperty **ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `members`  
 [in] Indicateurs pour spécifier ce qui est inclus dans les informations de membre.  
  
 `ppEnum`  
 [out] Les membres de l’objet.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugProperty](../../winscript/reference/ijsdebugproperty-interface.md)