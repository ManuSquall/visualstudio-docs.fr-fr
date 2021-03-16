---
description: Vous avez tenté d’utiliser instanceof pour déterminer si un objet a été dérivé d’une classe de fonction particulière, mais vous avez redéfini la propriété de prototype de l’objet comme étant null ou un type d’objet externe (à la fois des objets JavaScript non valides).
title: La fonction n’a pas d’objet prototype valide | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0356ac9ef7c63c77c0cc0dfca623ff24d3de24af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571413"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>La fonction ne possède pas d'objet prototype valide
Vous avez tenté d’utiliser **instanceof** pour déterminer si un objet a été dérivé d’une classe de fonction particulière, mais vous avez redéfini la propriété de l’objet `prototype` en tant que, ou en tant que `null` type d’objet externe (à la fois les objets non valides [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ). Un objet externe peut être un objet du modèle objet hôte (par exemple, l’objet document ou fenêtre d’Internet Explorer) ou un objet COM externe.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Vérifiez que la propriété de la fonction `prototype` fait référence à un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objet valide.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de fonction](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [Propriété prototype (Object)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)
