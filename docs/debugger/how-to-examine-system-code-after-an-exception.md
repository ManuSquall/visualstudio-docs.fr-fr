---
title: 'Comment : examiner du Code système après une Exception | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2914aab911d3c700b38c58eac009b2e21e94420e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Comment : examiner du code système après une exception
Lorsqu'une exception est levée, il peut s'avérer nécessaire d'examiner le code dans un appel système afin de déterminer la cause de l'exception. Pour ce faire, suivez la procédure ci-dessous si aucun symbole n'est chargé pour le code système ou si l'option Uniquement mon code est activée.  
  
### <a name="to-examine-system-code-following-an-exception"></a>Pour examiner du code système après une exception  
  
1.  Dans le **pile des appels** fenêtre, avec le bouton droit, puis cliquez sur **afficher le Code externe**.  
  
     Si l'option Uniquement mon code n'est pas activée, cette option n'est pas disponible dans le menu contextuel et le code système s'affiche par défaut.  
  
2.  Cliquez sur les frames de code externe qui s’affichent maintenant dans le **pile des appels** fenêtre.  
  
3.  Pointez sur **charger les symboles depuis** puis cliquez sur **serveurs de symboles Microsoft**.  
  
    1.  Si l'option Uniquement mon code était activée, une boîte de dialogue s'affiche pour indiquer que cette option est à présent désactivée, ce qui est nécessaire pour effectuer un pas à pas détaillé dans les appels système.  
  
    2.  Le **le téléchargement des symboles publics** boîte de dialogue s’affiche. puis se ferme une fois le téléchargement terminé.  
  
4.  Vous pouvez maintenant examiner le code système dans le **pile des appels** fenêtre et les autres fenêtres. Par exemple, vous pouvez double-cliquer sur un frame de pile des appels pour afficher le code dans une source ou **code machine** fenêtre.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md)