---
title: Impossible de modifier le boîte de dialogue valeur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f8f9dafe8ada8914591426dea9abc867de2236f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564149"
---
# <a name="cannot-change-value-dialog-box"></a>Impossible de changer la valeur (boîte de dialogue)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Error  
 `The value of this variable cannot be changed` &#124;`The name` *nom* `does not exist in the current context` &#124; *divers autres messages*  
  
 Cette boîte de message s'affiche lorsque vous essayez de remplacer le contenu d'une variable par une valeur non conforme dans une fenêtre du débogueur (Automatique, Espion ou Variables locales) ou dans la boîte de dialogue Espion express. Par exemple, cette boîte de message s'affiche si vous essayez d'attribuer à la valeur d'une variable entière une chaîne de caractères.  
  
## <a name="solution"></a>Solution  
 Assurez-vous que l'entrée que vous tapez dans la fenêtre du débogueur ou dans la boîte de dialogue Espion express représente une valeur conforme pour la variable que vous essayez de définir.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions dans le débogueur](../debugger/expressions-in-the-debugger.md)
