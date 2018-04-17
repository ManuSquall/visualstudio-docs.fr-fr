---
title: 'Erreur : Ordinateur distant n’a pas initier les communications DCOM | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e104e63bf9dde11efbefe4b657a85b3bfc94549
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Erreur : L'ordinateur distant n'a pas pu initier les communications DCOM
Une erreur DCOM s'est produite lorsque l'ordinateur distant a tenté de communiquer avec l'ordinateur local. L'ordinateur local est l'ordinateur qui  
  
 exécute Visual Studio. Cette erreur peut se produire pour plusieurs raisons :  
  
-   L'ordinateur local a un pare-feu activé.  
  
-   L'authentification Windows de l'ordinateur distant vers l'ordinateur local ne fonctionne pas.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Si l’ordinateur local dispose de pare-feu Windows est activé, consultez [débogage distant](../debugger/remote-debugging.md) pour obtenir des instructions sur la façon de configurer le pare-feu pour le débogage local.  
  
2.  Testez l'authentification Windows en essayant d'ouvrir un partage de fichiers sur l'ordinateur local du serveur distant.  
  
3.  Pour restaurer l'authentification Windows, tentez de redémarrer les deux ordinateurs. Vérifiez si les journaux des événements de l'ordinateur local ou distant contiennent des erreurs Kerberos et contactez les administrateurs de domaines pour les problèmes connus.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage à distance](../debugger/remote-debugging.md)