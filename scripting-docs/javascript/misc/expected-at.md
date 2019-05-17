---
title: Attendu ' @' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa2728306d9e650bf7f8b446b6af5a409a39d0e0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935248"
---
# <a name="expected-"></a>Attendu '\@'
Vous avez tenté de créer une variable qui doit être utilisé avec les instructions de compilation conditionnelle à l’aide de la `@set` instruction, mais ne pas placer une arobase « **@** » avant le nom de variable.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Ajouter un signe « **@** « juste avant le nom de variable. Exemple :  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [@set Instruction](../../javascript/reference/at-set-statement-javascript.md)   
 [Compilation conditionnelle](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilation conditionnelle](../../javascript/advanced/conditional-compilation-variables-javascript.md)
