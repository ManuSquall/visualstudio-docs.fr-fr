---
title: "prototype, propriété (Intl.NumberFormat) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7f6a7e26-108b-4b32-97c2-7f96b9252c50
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b037ce7476574252966e17fcf64246beeaaea1e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-intlnumberformat"></a>prototype, propriété (Intl.NumberFormat)
Retourne une référence au prototype pour un formateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
numberFormat.prototype  
```  
  
## <a name="remarks"></a>Remarques  
 Le `numberFormat` argument est le nom d’un formateur.  
  
 Utilisez la propriété `prototype` pour fournir un ensemble de base de fonctionnalités à une classe d'objets. Les nouvelles instances d'un objet « héritent » du comportement du prototype attribué à cet objet.  
  
 Par exemple, pour ajouter une méthode à l'objet `Intl.NumberFormat` qui retourne la valeur de l'élément le plus grand de l'ensemble, déclarez la fonction, ajoutez-la à `Intl.NumberFormat.prototype`, puis utilisez-la.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]