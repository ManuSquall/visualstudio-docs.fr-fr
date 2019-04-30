---
title: Ne peut pas avoir 'continue' en dehors de la boucle | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d2d95259-b2bc-4069-9876-60c30ad600a3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 421cc23fb807a571b2b36f5f1def5df46a99492b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946613"
---
# <a name="cant-have-continue-outside-of-loop"></a>Impossible d'utiliser une instruction 'continue' en dehors d'une boucle
Vous avez tenté d’utiliser le **continuer** instruction en dehors d’une boucle. Le **continuer** instruction peut être utilisée uniquement dans le corps des éléments suivants :  
  
- `do-while` boucle,  
  
- `while` boucle,  
  
- **pour** boucle,  
  
- **pour/dans** boucle.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Assurez-vous que le **continuer** instruction apparaît au sein des éléments suivants :  
  
    - `do-while` boucle,  
  
    - `while` boucle,  
  
    - **pour** boucle,  
  
    - **pour/dans** boucle.  
  
## <a name="see-also"></a>Voir aussi  
 [continue (instruction)](../../javascript/reference/continue-statement-javascript.md)   
 [Contrôle du flux de programme](../../javascript/controlling-program-flow-javascript.md)   
 [Résolution des problèmes liés aux scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)
