---
title: 'Erreur : Impossible d’initier les communications DCOM | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.unmarshal_server_failed
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
ms.openlocfilehash: 5581a1d98b24b53aae0da674719c594de51a7bb7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Erreur : Impossible d'initier les communications DCOM
Une erreur DCOM s'est produite lorsque l'ordinateur local a tenté de communiquer avec l'ordinateur distant. Cette erreur est provoquée par un pare-feu sur le serveur distant ou une authentification Windows interrompue sur l'ordinateur distant.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si l’ordinateur distant a activé le pare-feu Windows, consultez [débogage distant](../debugger/remote-debugging.md) pour obtenir des instructions sur la façon de configurer le pare-feu pour le débogage local.  
  
-   Pour restaurer l'authentification Windows, tentez de redémarrer les deux ordinateurs. Vérifiez si les journaux des événements de l'ordinateur local ou distant contiennent des erreurs Kerberos et contactez les administrateurs de domaines pour les problèmes connus.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage à distance](../debugger/remote-debugging.md)