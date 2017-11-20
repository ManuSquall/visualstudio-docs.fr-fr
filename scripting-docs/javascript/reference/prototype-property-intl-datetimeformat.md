---
title: "prototype, propriété (Intl.DateTimeFormat) | Documents Microsoft"
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
ms.assetid: e1e693ff-1775-407e-b655-18a60d238ded
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64dff17e4aaf62940f4c9c5f8b422fcbceb7212a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-intldatetimeformat"></a>prototype, propriété (Intl.DateTimeFormat)
Retourne une référence au prototype pour un formateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
dateTimeFormat.prototype  
```  
  
## <a name="remarks"></a>Remarques  
 Le `dateTimeFormat` argument est le nom d’un formateur.  
  
 Utilisez la propriété `prototype` pour fournir un ensemble de base de fonctionnalités à une classe d'objets. Les nouvelles instances d'un objet « héritent » du comportement du prototype attribué à cet objet.  
  
 Par exemple, pour ajouter une méthode à l'objet `Intl.DateTimeFormat` qui retourne la valeur de l'élément le plus grand de l'ensemble, déclarez la fonction, ajoutez-la à `Intl.DateTimeFormat.prototype`, puis utilisez-la.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]