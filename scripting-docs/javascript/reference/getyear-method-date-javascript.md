---
title: "getYear, méthode (Date) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- getYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- GetYear method
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0e08fae8da1b102918de70650d09080a7ff7ebd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="getyear-method-date-javascript"></a>getYear, méthode (Date) (JavaScript)
Obtient l’année d’une `Date` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.getYear()   
```  
  
#### <a name="parameters"></a>Paramètres  
 La référence `dateObj` nécessaire est un objet `Date` .  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’année.  
  
## <a name="remarks"></a>Remarques  
  
> [!IMPORTANT]
>  Cette méthode est obsolète et il est fournie pour la compatibilité descendante uniquement. Utilisez plutôt la méthode `getFullYear`.  
  
 Dans [!INCLUDE[jsv1textspecific](../../javascript/reference/includes/jsv1textspecific-md.md)], puis dans les versions d’Internet Explorer en commençant par [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], la valeur retournée est l’année stockée moins 1900. Par exemple, l’année 1899 est retournée en tant que -1 et l’année 2000 est retournée en tant que 100.  
  
 Dans [!INCLUDE[jsv3textspecific](../../javascript/reference/includes/jsv3textspecific-md.md)] via [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)], la formule dépend de l’année. Pour les années 1900 à 1999, la valeur retournée est une valeur de 2 chiffres représentant l’année stockée moins 1900. Pour les dates en dehors de cette plage, l’année en 4 chiffres est retournée. Par exemple, 1996 valeur retournée est 96, mais 1825 et 2025 sont retournées en l’état.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getFullYear, méthode (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear, méthode (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear, méthode (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear, méthode (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [Méthode setYear (Date)](../../javascript/reference/setyear-method-date-javascript.md)