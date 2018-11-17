---
title: 'Erreur : Ordinateur distant Impossible d’initialiser les communications DCOM | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c86e5a193348a8f90e4888e0df3472d102beb08
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800872"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Erreur : L'ordinateur distant n'a pas pu initier les communications DCOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une erreur DCOM s'est produite lorsque l'ordinateur distant a tenté de communiquer avec l'ordinateur local. L'ordinateur local est l'ordinateur qui  
  
 exécute Visual Studio. Cette erreur peut se produire pour plusieurs raisons :  
  
-   L'ordinateur local a un pare-feu activé.  
  
-   L'authentification Windows de l'ordinateur distant vers l'ordinateur local ne fonctionne pas.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Si l’ordinateur local a un pare-feu Windows est activé, consultez [définir Up the Remote Tools sur l’appareil](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) pour obtenir des instructions sur la façon de configurer le pare-feu pour le débogage local.  
  
2.  Testez l'authentification Windows en essayant d'ouvrir un partage de fichiers sur l'ordinateur local du serveur distant.  
  
3.  Pour restaurer l'authentification Windows, tentez de redémarrer les deux ordinateurs. Vérifiez si les journaux des événements de l'ordinateur local ou distant contiennent des erreurs Kerberos et contactez les administrateurs de domaines pour les problèmes connus.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les outils de contrôle à distance sur le périphérique](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)



