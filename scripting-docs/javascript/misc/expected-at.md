---
title: Attendu ' @' | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 73e7e8fb43bb45e4c97b6bb5ec6c739c16a4423a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349854"
---
# <a name="expected-"></a>'@' attendu
Vous avez tenté de créer une variable qui doit être utilisé avec les instructions de compilation conditionnelle à l’aide de la `@set` instruction, mais ne pas placer une arobase «**@**» avant le nom de variable.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Ajouter un signe «**@**« juste avant le nom de variable. Exemple :  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [@set Instruction](../../javascript/reference/at-set-statement-javascript.md)   
 [Compilation conditionnelle](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilation conditionnelle](../../javascript/advanced/conditional-compilation-variables-javascript.md)