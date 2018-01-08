---
title: "Impossible de modifier le boîte de dialogue valeur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7a6b5cc2c1a5317009225d8e86fd497dc4367787
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2018
---
# <a name="cannot-change-value-dialog-box"></a>Impossible de changer la valeur (boîte de dialogue)
## <a name="error"></a>Error  
 `The value of this variable cannot be changed`&#124; `The name` *nom* `does not exist in the current context` &#124; *divers autres messages.*  
  
 Cette boîte de message s'affiche lorsque vous essayez de remplacer le contenu d'une variable par une valeur non conforme dans une fenêtre du débogueur (Automatique, Espion ou Variables locales) ou dans la boîte de dialogue Espion express. Par exemple, cette boîte de message s'affiche si vous essayez d'attribuer à la valeur d'une variable entière une chaîne de caractères.  
  
## <a name="solution"></a>Solution  
 Assurez-vous que l'entrée que vous tapez dans la fenêtre du débogueur ou dans la boîte de dialogue Espion express représente une valeur conforme pour la variable que vous essayez de définir.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions dans le débogueur](../debugger/expressions-in-the-debugger.md)