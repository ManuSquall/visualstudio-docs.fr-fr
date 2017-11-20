---
title: "Périmées de boîte de dialogue d’avertissement Code | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.ENC.stalecode
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Stale Code Warning dialog box
- code, stale code warning
- warnings, Stale Code Warning dialog box
- Edit and Continue, stale code
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54ff550719f1b0bbea12f3b64b49fc9792f63ee6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="stale-code-warning-dialog-box"></a>Avertissement : code périmé (boîte de dialogue)
Cette boîte de dialogue s’affiche lorsque vous avez apporté des modifications au code natif qui **Modifier & Continuer** pas pu appliquer immédiatement. Par conséquent, une partie du code natif du frame de pile actif n'est plus à jour ; il est périmé. Pour plus d’informations, consultez [Comment : utiliser du Code périmé](http://msdn.microsoft.com/en-us/c7536e95-66a6-44a0-995d-3fe5035250b4).  
  
 **Ne plus afficher cette boîte de dialogue**  
 Si vous activez cette case à cocher, Modifier & Continuer appliquera à l'avenir les modifications de code sans vous en demander l'autorisation. Vous pouvez réactiver cet avertissement en accédant à la **Options** boîte de dialogue le **débogage** dossier, en cliquant sur le **Modifier & Continuer** page et en sélectionnant **Signaler le code périmé**.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de Code prises en charge (C++)](../debugger/supported-code-changes-cpp.md)   
 [Modifier & Continuer, débogage, boîte de dialogue Options](http://msdn.microsoft.com/Library/009d225f-ef65-463f-a146-e4c518f86103)