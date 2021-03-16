---
description: Vous avez tenté de créer une variable à utiliser avec des instructions de compilation conditionnelle à l’aide de l' @set instruction, mais n’avez pas placé au signe @ avant le nom de la variable.
title: "' @ 'Attendu | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: e7aa02ed1e436c92014d44e57f2c71ff7db5f99b
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570620"
---
# <a name="expected-"></a>'\@' attendu
Vous avez tenté de créer une variable à utiliser avec des instructions de compilation conditionnelle à l’aide de l' `@set` instruction, mais vous n’avez pas placé d’arobase « **@** » avant le nom de la variable.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Ajoutez un arobase « **@** » immédiatement avant le nom de la variable. Par exemple :  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [@set Gestion](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-set)   
 [Compilation conditionnelle](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/121hztk3(v=vs.84))   
 [Variables de compilation conditionnelle](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/s59bkzce(v=vs.84))
