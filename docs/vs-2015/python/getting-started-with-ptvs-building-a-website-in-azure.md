---
title: 'Bien démarrer avec PTVS : création d’un site web dans Azure | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bdbda36-14d2-4fde-ba42-d91042777ff6
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 75b47239f37586751d1a3c41696a9798a3cfffb1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494660"
---
# <a name="getting-started-with-ptvs-building-a-website-in-azure"></a>Bien démarrer avec PTVS : création d’un site web dans Azure
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez commencer rapidement à créer un site web Python dans Azure.  
  
 Vous pouvez obtenir des instructions en regardant cette très courte [vidéo youtube](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6).  
  
 Commencez avec la boîte de dialogue Nouveau projet ... et, dans les projets Python, choisissez le projet web Bottle.  Ce modèle [Bottle](http://bottlepy.org/docs/dev/index.html) est un site de démarrage basé sur le [framework Bootstrap](http://getbootstrap.com/).  Quand vous créez le projet, Visual Studio vous invite à installer les dépendances (Bottle dans ce cas) dans un environnement virtuel.  Étant donné que vous effectuez le déploiement sur un site web Azure, vous devez ajouter les dépendances dans un environnement virtuel pour déployer les bits nécessaires au fonctionnement de votre site.  Vous devez également baser votre environnement sur Python 2.7 ou 3.4 32 bits.  Une fois votre projet créé, appuyez sur F5 pour commencer à exécuter votre site.  
  
 L'essai du site dans Azure s'effectue facilement.  Si vous n’avez pas d’abonnement Azure, vous pouvez utiliser [try.azurewebsites.net](https://trywebsites.azurewebsites.net/).  Ce site offre un moyen simple pour tester Azure Websites pendant une heure à l’aide d’une simple connexion sociale.  Vous n'avez pas besoin de carte de crédit.  Choisissez le modèle Site vide dans la liste déroulante Modifier le langage et sélectionnez Créer.  Sous « Utiliser votre application web », choisissez Télécharger le profil de publication et enregistrez le fichier pour l'utiliser avec Visual Studio.  Vous pouvez également effectuer le déploiement à l'aide de git sur n'importe quel système d'exploitation.  
  
 Revenez à Visual Studio et au projet que vous avez créé.  Sélectionnez le nœud de votre projet dans l'Explorateur de solutions, cliquez avec le bouton droit du pointeur et choisissez Publier.  Si vous avez un abonnement Azure, vous pouvez cliquer sur Microsoft Azure Websites dans la boîte de dialogue pour gérer vos sites à cet endroit.  Dans le cadre de cette procédure pas à pas, cliquez sur Importer pour importer le profil de publication que vous venez de télécharger.  Étant donné que le profil de publication contient toutes les informations nécessaires, vous pouvez sélectionner Publier.  Au bout de quelques secondes, une nouvelle fenêtre de navigateur s'ouvre et votre site est en ligne hébergé sur le cloud Azure.  
  
 Les sites web simples sont faciles à gérer, mais pour plus d’informations sur les applications web plus complexes dans Azure, consultez la vidéo de [présentation approfondie](https://www.youtube.com/watch?v=WG3pGmoo8nE&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=10) ainsi que d’autres vidéos de ce canal (lien en haut à droite de la page de la vidéo de prise en main ou de présentation approfondie, et ci-dessous).  
  
 Vous pouvez obtenir des instructions en regardant cette très courte [vidéo youtube](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6).  
  
## <a name="see-also"></a>Voir aussi  
 [Documentation du wiki](https://github.com/Microsoft/PTVS/wiki/Web-Project)   
 [Vidéos sur le démarrage et l’exploration de PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

