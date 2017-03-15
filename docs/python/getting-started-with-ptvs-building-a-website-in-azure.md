---
title: "Bien démarrer avec PTVS : création d’un site web dans Azure | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bdbda36-14d2-4fde-ba42-d91042777ff6
caps.latest.revision: 4
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 2d84d0c8949772feab8f5bd046651449e58271d8
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-ptvs-building-a-website-in-azure"></a>Bien démarrer avec PTVS : création d’un site web dans Azure
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
