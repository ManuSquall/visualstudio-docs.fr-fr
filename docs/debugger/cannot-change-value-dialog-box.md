---
title: Impossible de changer la valeur, boîte de dialogue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97f057edefefd590c37b49d709ecf8a6e029b905
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745738"
---
# <a name="cannot-change-value-dialog-box"></a>Impossible de changer la valeur (boîte de dialogue)
## <a name="error"></a>Erreur
 `The value of this variable cannot be changed` &#124; `The name` *nom* `does not exist in the current context` &#124; d' *autres messages*

 Cette boîte de message s'affiche lorsque vous essayez de remplacer le contenu d'une variable par une valeur non conforme dans une fenêtre du débogueur (Automatique, Espion ou Variables locales) ou dans la boîte de dialogue Espion express. Par exemple, cette boîte de message s'affiche si vous essayez d'attribuer à la valeur d'une variable entière une chaîne de caractères.

## <a name="solution"></a>Solution
 Assurez-vous que l'entrée que vous tapez dans la fenêtre du débogueur ou dans la boîte de dialogue Espion express représente une valeur conforme pour la variable que vous essayez de définir.

## <a name="see-also"></a>Voir aussi

- [Expressions dans le débogueur](../debugger/expressions-in-the-debugger.md)