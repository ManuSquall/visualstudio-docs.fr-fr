---
title: getVarDate, méthode (Date) (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- getVarDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- getVarDate method
- dates, VT_DATE format
ms.assetid: 561238de-5c91-45a3-b839-a16910d3a1cf
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d21394a5381653997a6b406537a6bde4f5266b97
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637129"
---
# <a name="getvardate-method-date-javascript"></a>getVarDate, méthode (Date) (JavaScript)
Retourne une valeur VT_DATE d’un objet `Date` .  
  
> [!WARNING]
>  Cette méthode est prise en charge seulement dans Internet Explorer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.getVarDate()   
```  
  
#### <a name="parameters"></a>Paramètres  
 La référence `dateObj` nécessaire est un objet `Date` .  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur VT_DATE.  
  
## <a name="remarks"></a>Remarques  
 La méthode `getVarDate` est utilisée quand du code JavaScript interagit avec des objets COM, des objets ActiveX ou d’autres objets qui acceptent et retournent des valeurs de date au format VT_DATE. Il s’agit notamment d’objets dans Visual Basic et Visual Basic Scripting Edition (VBScript). Le format réel de la valeur retournée dépend des paramètres régionaux.  
  
## <a name="requirements"></a>Spécifications  
 Pris en charge dans les modes de document suivants : Quirks, Internet Explorer 6 (mode standard), Internet Explorer 7 (mode standard), Internet Explorer 8 (mode standard), Internet Explorer 9 (mode standard) et Internet Explorer 10 (mode standard). Non pris en charge dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Voir [Informations de version](../../javascript/reference/javascript-version-information.md).  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getDate, méthode (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Fonction Date.parse](../../javascript/reference/date-parse-function-javascript.md)