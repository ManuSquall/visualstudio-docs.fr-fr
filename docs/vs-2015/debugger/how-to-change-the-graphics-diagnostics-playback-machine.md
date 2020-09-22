---
title: 'Comment : modifier l’ordinateur de lecture Graphics Diagnostics | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb14fb4017ea1df6659b9a1a0ac093cd7cf7e0b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839806"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Procédure : modifier l’ordinateur de lecture Graphics Diagnostics
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez lire les informations graphiques à l’aide de votre ordinateur local ou à l’aide d’un ordinateur ou d’un appareil distant.  
  
## <a name="choosing-a-playback-machine"></a>Choix d’un ordinateur de lecture  
 L’ordinateur de lecture est un ordinateur ou un appareil utilisé pour lire les événements graphiques à partir d’un journal de graphisme. En règle générale, l’ordinateur local est l’option la plus pratique, mais un problème de rendu peut ne pas se reproduire sur un ordinateur dont la version du matériel ou du pilote est différente de celle de l’ordinateur sur lequel il a été capturé. dans ce cas, vous pouvez choisir un ordinateur de lecture à distance qui reproduit mieux le problème tout en continuant à utiliser votre ordinateur de développement pour le diagnostic.  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Pour utiliser l’ordinateur local pour lire les informations graphiques  
  
1. Dans la fenêtre de document du journal de graphisme, choisissez le lien de lecture de l' **ordinateur** . La boîte de dialogue **connexions du débogueur distant** s’affiche.  
  
2. Sous **configuration manuelle**, dans la propriété **adresse** , entrez `localhost` .  
  
3. Définissez la propriété **mode d’authentification** sur **aucun**.  
  
4. Choisissez le bouton **Sélectionner**.  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Pour utiliser une machine distante pour lire des informations graphiques  
  
1. Dans la fenêtre de document du journal de graphisme, choisissez le lien de lecture de l' **ordinateur** . La boîte de dialogue **connexions du débogueur distant** s’affiche.  
  
2. Sous **configuration manuelle**, dans la propriété **adresse** , entrez le nom de domaine Windows ou l’adresse IP de l’ordinateur ou du périphérique que vous souhaitez utiliser pour lire les informations graphiques.  
  
3. Spécifiez le type d’autorisation que vous souhaitez utiliser pour sécuriser la connexion à l’ordinateur de lecture.  
  
    - Pour l’authentification Windows, définissez la propriété **mode d’authentification** sur **Windows**.  
  
    - Pour aucune authentification, définissez la propriété **mode d’authentification** sur **aucun**.  
  
4. Choisissez le bouton **Sélectionner**.  
  
> [!NOTE]
> La boîte de dialogue **connexions du débogueur distant** peut également afficher des cibles de débogage distant qui sont directement connectées à votre ordinateur de développement ou qui se trouvent sur le même sous-réseau. Vous pouvez utiliser l’une de ces cibles de débogage distant en tant qu’ordinateur de lecture Graphics Diagnostics sans le configurer manuellement. Dans la boîte de dialogue **connexions du débogueur distant** , sélectionnez la cible souhaitée, puis cliquez sur le bouton **Sélectionner** .  
  
## <a name="see-also"></a>Voir aussi  
 [Document de journal Graphics](../debugger/graphics-log-document.md)
