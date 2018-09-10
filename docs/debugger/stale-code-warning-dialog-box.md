---
title: Périmées de boîte de dialogue Avertissement de Code | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.stalecode
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1e212602b317127cfd14adcd246a23cdd92ed86
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281791"
---
# <a name="stale-code-warning-dialog-box"></a>Avertissement : code périmé (boîte de dialogue)
Cette boîte de dialogue s’affiche lorsque vous avez apporté des modifications au code natif qui **Modifier & Continuer** pas pu appliquer immédiatement. Par conséquent, une partie du code natif du frame de pile actif n'est plus à jour ; il est périmé. Pour plus d’informations, consultez [Comment : utiliser du Code périmé](/visualstudio/debugger/edit-and-continue-visual-cpp#bkmk_how_to_work_with_stale_code).  
  
 **Ne plus afficher cette boîte de dialogue**  
 Si vous activez cette case à cocher, Modifier & Continuer appliquera à l'avenir les modifications de code sans vous en demander l'autorisation. Vous pouvez réactiver cet avertissement en accédant à la **Options** boîte de dialogue le **débogage** dossier, en cliquant sur le **Modifier & Continuer** page, puis en sélectionnant **Signaler le code périmé**.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de Code prises en charge (C++)](../debugger/supported-code-changes-cpp.md)   
 [Modifier & Continuer, Débogage, Boîte de dialogue Options](/visualstudio/debugger/edit-and-continue)