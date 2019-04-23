---
title: 'Erreur : Impossible d’initier les communications DCOM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.unmarshal_server_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f9ae4de4f8dc044d578bb4f593dc9c6c77a7b0b6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60083892"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Erreur : Impossible de lancer les communications DCOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une erreur DCOM s'est produite lorsque l'ordinateur local a tenté de communiquer avec l'ordinateur distant. Cette erreur est provoquée par un pare-feu sur le serveur distant ou une authentification Windows interrompue sur l'ordinateur distant.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Si l’ordinateur distant a de pare-feu Windows est activé, consultez [définir Up the Remote Tools sur l’appareil](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) pour obtenir des instructions sur la façon de configurer le pare-feu pour le débogage local.  
  
- Pour restaurer l'authentification Windows, tentez de redémarrer les deux ordinateurs. Vérifiez si les journaux des événements de l'ordinateur local ou distant contiennent des erreurs Kerberos et contactez les administrateurs de domaines pour les problèmes connus.  
  
## <a name="see-also"></a>Voir aussi  
 [Remote Debugging](../debugger/remote-debugging.md)
