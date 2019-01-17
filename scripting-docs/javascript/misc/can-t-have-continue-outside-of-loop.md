---
title: Ne peut pas avoir 'continue' en dehors de la boucle | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d2d95259-b2bc-4069-9876-60c30ad600a3
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d4939635b69cf5b49e36c7168dcf3c1a786821f
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348553"
---
# <a name="cant-have-continue-outside-of-loop"></a>Impossible d'utiliser une instruction 'continue' en dehors d'une boucle
Vous avez tenté d’utiliser le **continuer** instruction en dehors d’une boucle. Le **continuer** instruction peut être utilisée uniquement dans le corps des éléments suivants :  
  
-   `do-while` boucle,  
  
-   `while` boucle,  
  
-   **pour** boucle,  
  
-   **pour/dans** boucle.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Assurez-vous que le **continuer** instruction apparaît au sein des éléments suivants :  
  
    -   `do-while` boucle,  
  
    -   `while` boucle,  
  
    -   **pour** boucle,  
  
    -   **pour/dans** boucle.  
  
## <a name="see-also"></a>Voir aussi  
 [continue (instruction)](../../javascript/reference/continue-statement-javascript.md)   
 [Contrôle du flux de programme](../../javascript/controlling-program-flow-javascript.md)   
 [Résolution des problèmes liés aux scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)
