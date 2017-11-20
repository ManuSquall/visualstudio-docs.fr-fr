---
title: "Erreur : Impossible d’initier les communications DCOM | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.unmarshal_server_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c80f2455b53cba46f0f2f753c55ff1b7e9dad8d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Erreur : Impossible d'initier les communications DCOM
Une erreur DCOM s'est produite lorsque l'ordinateur local a tenté de communiquer avec l'ordinateur distant. Cette erreur est provoquée par un pare-feu sur le serveur distant ou une authentification Windows interrompue sur l'ordinateur distant.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si l’ordinateur distant a activé le pare-feu Windows, consultez [débogage distant](../debugger/remote-debugging.md) pour obtenir des instructions sur la façon de configurer le pare-feu pour le débogage local.  
  
-   Pour restaurer l'authentification Windows, tentez de redémarrer les deux ordinateurs. Vérifiez si les journaux des événements de l'ordinateur local ou distant contiennent des erreurs Kerberos et contactez les administrateurs de domaines pour les problèmes connus.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage à distance](../debugger/remote-debugging.md)