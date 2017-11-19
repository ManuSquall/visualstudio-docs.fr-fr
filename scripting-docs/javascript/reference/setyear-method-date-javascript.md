---
title: "setYear, méthode (Date) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setYear method
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a9318de4a9420e0518dcd7f00a51c7161a8f92c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="setyear-method-date-javascript"></a>setYear, méthode (Date) (JavaScript)
Définit la valeur de l’année dans le `Date` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Tout objet `Date`.  
  
 `numYear`  
 Obligatoire. Pour les années 1900 à 1999, il s’agit d’une valeur numérique égale à l’année moins 1900. Pour les dates en dehors de cette plage, il s’agit d’une valeur numérique de 4 chiffres.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est obsolète et est conservée pour descendante de compatibilité. Utilisez plutôt la méthode `setFullYear`.  
  
 Pour définir l’année d’une `Date` objet 1997, appel **setYear(97)**. Pour définir l’année 2010, appelez **setYear(2010)**. Enfin, pour définir l’année d’une année dans la plage 0-99, utilisez le `setFullYear` (méthode).  
  
> [!NOTE]
>  Pour [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] version 1.0, `setYear` utilise une valeur qui est le résultat de l’addition de 1900 à la valeur d’année fournie par `numYear`, quelle que soit la valeur de l’année. Par exemple, pour définir l’année à 1899 `numYear` est -1 et pour définir l’année 2000 `numYear` est 100.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getFullYear, méthode (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear, méthode (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [getYear, méthode (Date)](../../javascript/reference/getyear-method-date-javascript.md)   
 [setFullYear, méthode (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Méthode setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)