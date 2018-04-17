---
title: 'Comment : gérer les mises à jour pour une Application ClickOnce | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 2346ab8bfcaaaaf2934461e251803fd5920f804b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Comment : gérer des mises à jour pour une application ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] les mises à jour les applications peuvent vérifier automatiquement ou par programme. En tant que développeur, vous avez une grande souplesse pour spécifier quand et comment les vérifications de la mise à jour sont effectuées, si les mises à jour sont obligatoires et où l’application doit vérifier les mises à jour.  
  
 Vous pouvez configurer l’application pour rechercher les mises à jour automatiquement avant le démarrage de l’application ou à des intervalles définis après le démarrage de l’application. En outre, vous pouvez spécifier une version minimale requise ; Autrement dit, une mise à jour est installé si la version de l’utilisateur est inférieure à la version requise.  
  
 Vous pouvez configurer l’application pour rechercher les mises à jour par programmation basées sur un événement tel qu’une demande de l’utilisateur. La procédure « pour vérifier les mises à jour par programmation » dans cette rubrique montre comment écrire le code qui utilise le <xref:System.Deployment.Application.ApplicationDeployment> classe pour rechercher les mises à jour basée sur un événement.  
  
 Vous pouvez également déployer votre application à partir d’un emplacement et mettez-le à jour à partir d’un autre. Consultez la procédure « pour spécifier un emplacement autre mise à jour ».  
  
 Pour plus d’informations, consultez [choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Comportement de mise à jour est géré dans le **mises à jour de l’Application** boîte de dialogue, disponible à partir de la **publier** page de la **Concepteur de projets.**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>Pour rechercher les mises à jour avant le démarrage de l’application  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Cliquez sur le **mises à jour** bouton pour ouvrir la **mises à jour de l’Application** boîte de dialogue.  
  
4.  Dans le **mises à jour de l’Application** boîte de dialogue zone, assurez-vous que le **l’application doit vérifier les mises à jour** case à cocher est activée.  
  
5.  Dans le **choisissez à quel moment l’application doit vérifier les mises à jour** section, sélectionnez **avant le démarrage de l’application**. Cela garantit que les utilisateurs connectés au réseau toujours exécutent l’application avec les dernières mises à jour.  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Pour rechercher les mises à jour en arrière-plan après le démarrage de l’application  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Cliquez sur le **mises à jour** bouton pour ouvrir la **mises à jour de l’Application** boîte de dialogue.  
  
4.  Dans le **mises à jour de l’Application** boîte de dialogue zone, assurez-vous que la case à cocher **l’application doit vérifier les mises à jour** est sélectionnée.  
  
5.  Dans le **choisissez à quel moment l’application doit vérifier pour la section mises à jour**, sélectionnez **après le démarrage de l’application**. L’application démarrera plus rapidement de cette manière, puis elle rechercher les mises à jour en arrière-plan et uniquement avertir l’utilisateur lorsqu’une mise à jour est disponible. Une fois installé, les mises à jour ne prendront effet qu’après le redémarrage de l’application.  
  
6.  Dans le **spécifier la fréquence à laquelle l’application doit vérifier les mises à jour** , sélectionnez **vérifier à chaque exécution de l’application** (la valeur par défaut) ou **vérifier chaque** et entrez un intervalle de temps et du numéro.  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Pour spécifier une version minimale requise pour l’application  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Cliquez sur le **mises à jour** bouton pour ouvrir la **mises à jour de l’Application** boîte de dialogue.  
  
4.  Dans le **mises à jour de l’Application** boîte de dialogue zone, assurez-vous que le **l’application doit vérifier les mises à jour** case à cocher est activée.  
  
5.  Sélectionnez le **spécifier une version minimale requise pour cette application** case à cocher, puis entrez **majeure**, **secondaire**, **générer**et  **Révision** nombres pour l’application.  
  
### <a name="to-specify-a-different-update-location"></a>Pour spécifier un emplacement autre mise à jour  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Cliquez sur le **mises à jour** bouton pour ouvrir la **mises à jour de l’Application** boîte de dialogue.  
  
4.  Dans le **mises à jour de l’Application** boîte de dialogue zone, assurez-vous que le **l’application doit vérifier les mises à jour** case à cocher est activée.  
  
5.  Dans le **mettre à jour emplacement** , entrez l’emplacement de mise à jour avec une URL qualifiée complète, en utilisant le format http://Hostname/ApplicationName, ou un chemin d’accès UNC au format \\\Server\ApplicationName, ou cliquez sur le **Parcourir** bouton pour rechercher l’emplacement de mise à jour.  
  
### <a name="to-check-for-updates-programmatically"></a>Pour vérifier les mises à jour par programme  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Cliquez sur le **mises à jour** bouton pour ouvrir la **mises à jour de l’Application** boîte de dialogue.  
  
4.  Dans le **mises à jour de l’Application** boîte de dialogue zone, assurez-vous que le **l’application doit vérifier les mises à jour** case à cocher est désactivée. (Si vous le souhaitez, vous pouvez sélectionner cette case à cocher pour vérifier des mises à jour par programme et laisser également le runtime ClickOnce vérifie automatiquement les mises à jour).  
  
5.  Dans le **mettre à jour emplacement** , entrez l’emplacement de mise à jour avec une URL qualifiée complète, en utilisant le format http://Hostname/ApplicationName, ou un chemin d’accès UNC au format \\\Server\ApplicationName, ou cliquez sur le **Parcourir** bouton pour rechercher l’emplacement de mise à jour. L’emplacement de mise à jour est dans laquelle l’application recherche une version mise à jour de lui-même.  
  
6.  Créer un bouton, élément de menu ou autre élément d’interface utilisateur sur un Windows Form qui sélectionnent les utilisateurs pour rechercher les mises à jour. À partir du Gestionnaire d’événements de cet élément, appelez une méthode pour rechercher et installer des mises à jour. Vous trouverez un exemple de code Visual Basic et Visual c# pour une telle méthode dans [Comment : vérifier pour l’Application des mises à jour par programmation à l’aide de l’API de déploiement ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).  
  
7.  Générez votre application.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [Boîte de dialogue application des mises à jour](http://msdn.microsoft.com/en-us/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)   
 [Choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Guide pratique pour vérifier la disponibilité de mises à jour des applications par programmation à l’aide de l’API de déploiement ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)