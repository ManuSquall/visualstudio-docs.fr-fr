---
title: JsDebugPropertyInfo Structure | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugPropertyInfo
apilocation:
- jscript9diag.dll
ms.assetid: 3a5463a7-2013-4846-9ab2-8beb675a5a6a
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8aeb2dcfc116c8c735cda95fc9d7ab9da97cab3b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154567"
---
# <a name="jsdebugpropertyinfo-structure"></a>Structure JsDebugPropertyInfo
Indique des informations sur une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef struct tagJsDebugPropertyInfo{   BSTR name;   BSTR type;   BSTR value;   BSTR fullName;   JS_PROPERTY_ATTRIBUTES attr;} JsDebugPropertyInfo;  
```  
  
## <a name="members"></a>Membres  
 `name`  
 Nom de la propriété.  
  
 `type`  
 Type de la propriété.  
  
 `value`  
 Valeur de la propriété.  
  
 `fullName`  
 Le nom complet de la propriété.  
  
 `attr`  
 Énumération qui représente les attributs de propriété.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)