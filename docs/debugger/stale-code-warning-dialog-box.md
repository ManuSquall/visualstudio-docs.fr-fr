---
title: Périmées de boîte de dialogue d’avertissement Code | Documents Microsoft
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
ms.openlocfilehash: ec80baa04529bcc6a9705d1c8df03e120e6bc64e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481474"
---
# <a name="stale-code-warning-dialog-box"></a>Avertissement : code périmé (boîte de dialogue)
Cette boîte de dialogue s’affiche lorsque vous avez apporté des modifications au code natif qui **Modifier & Continuer** pas pu appliquer immédiatement. Par conséquent, une partie du code natif du frame de pile actif n'est plus à jour ; il est périmé. Pour plus d’informations, consultez [Comment : utiliser du Code périmé](http://msdn.microsoft.com/en-us/c7536e95-66a6-44a0-995d-3fe5035250b4).  
  
 **Ne plus afficher cette boîte de dialogue**  
 Si vous activez cette case à cocher, Modifier & Continuer appliquera à l'avenir les modifications de code sans vous en demander l'autorisation. Vous pouvez réactiver cet avertissement en accédant à la **Options** boîte de dialogue le **débogage** dossier, en cliquant sur le **Modifier & Continuer** page et en sélectionnant **Signaler le code périmé**.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de Code prises en charge (C++)](../debugger/supported-code-changes-cpp.md)   
 [Modifier & Continuer, débogage, boîte de dialogue Options](http://msdn.microsoft.com/Library/009d225f-ef65-463f-a146-e4c518f86103)