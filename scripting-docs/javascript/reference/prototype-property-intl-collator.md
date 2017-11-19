---
title: "prototype, propriété (Intl.Collator) | Documents Microsoft"
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
ms.assetid: c1bbb523-fb55-4395-b357-34d91cf5bba0
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 696535afde8c497bc98fc2c81a03854d66add6f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-intlcollator"></a>prototype, propriété (Intl.Collator)
Retourne une référence au prototype pour un assembleur.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
collator.prototype  
```  
  
## <a name="remarks"></a>Remarques  
 Le `collator` argument est le nom d’un assembleur.  
  
 Utilisez la propriété `prototype` pour fournir un ensemble de base de fonctionnalités à une classe d'objets. Les nouvelles instances d'un objet « héritent » du comportement du prototype attribué à cet objet.  
  
 Par exemple, pour ajouter une méthode à l'objet `Intl.Collator` qui retourne la valeur de l'élément le plus grand de l'ensemble, déclarez la fonction, ajoutez-la à `Intl.Collator.prototype`, puis utilisez-la.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]