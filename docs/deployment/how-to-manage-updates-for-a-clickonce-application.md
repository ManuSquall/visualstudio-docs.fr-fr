---
title: 'Comment : gérer les mises à jour pour une Application ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5bd9d8d7e88bc9ee8c8b041571ddaa258067c300
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283650"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Comment : gérer les mises à jour pour une application ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] les applications peuvent vérifier les mises à jour automatiquement ou par programmation. En tant que développeur, vous avez une grande souplesse lors de la spécification de quand et comment les vérifications de mise à jour sont effectuées, si les mises à jour sont obligatoires, et où l’application doit vérifier les mises à jour.  
  
 Vous pouvez configurer l’application pour rechercher les mises à jour automatiquement avant le démarrage de l’application ou à des intervalles définis après le démarrage de l’application. En outre, vous pouvez spécifier une version minimale requise ; Autrement dit, une mise à jour est installé si la version de l’utilisateur est inférieure à la version requise.  
  
 Vous pouvez configurer l’application pour rechercher les mises à jour par programmation basées sur un événement tel qu’une demande utilisateur. La procédure « pour vérifier les mises à jour par programme » dans cette rubrique montre comment écrire le code qui utilise le <xref:System.Deployment.Application.ApplicationDeployment> class à vérifier les mises à jour basée sur un événement.  
  
 Vous pouvez également déployer votre application à partir d’un emplacement et mettez-le à jour à partir d’un autre. Consultez la procédure « pour spécifier un emplacement de mise à jour différent ».  
  
 Pour plus d’informations, consultez [choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Comportement de mise à jour est géré dans le **mises à jour de l’Application** boîte de dialogue, disponible à partir de la **publier** page de la **Concepteur de projets.**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>Pour vérifier les mises à jour avant le démarrage de l’application  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Cliquez sur le **mises à jour** bouton pour ouvrir la **mises à jour de l’Application** boîte de dialogue.  
  
4.  Dans le **mises à jour de l’Application** boîte de dialogue zone, assurez-vous que le **l’application doit vérifier les mises à jour** case à cocher est activée.  
  
5.  Dans le **choisissez à quel moment l’application doit vérifier les mises à jour** section, sélectionnez **avant le démarrage de l’application**. Cela garantit que les utilisateurs connectés au réseau toujours exécutent l’application avec les dernières mises à jour.  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Pour vérifier les mises à jour en arrière-plan après le démarrage de l’application  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Cliquez sur le **mises à jour** bouton pour ouvrir la **mises à jour de l’Application** boîte de dialogue.  
  
4.  Dans le **mises à jour de l’Application** boîte de dialogue zone, assurez-vous que la case à cocher **l’application doit vérifier les mises à jour** est sélectionné.  
  
5.  Dans le **choisissez à quel moment l’application doit vérifier pour la section mises à jour**, sélectionnez **après le démarrage de l’application**. L’application démarrera plus rapidement de cette façon, puis il vérifie les mises à jour en arrière-plan et uniquement avertir l’utilisateur lorsqu’une mise à jour est disponible. Une fois installé, les mises à jour ne prendront effet qu’après le redémarrage de l’application.  
  
6.  Dans le **spécifier la fréquence à laquelle l’application doit vérifier les mises à jour** , sélectionnez **vérifier à chaque exécution de l’application** (la valeur par défaut) ou **vérifier chaque** et entrez un intervalle de temps et du numéro.  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Pour spécifier une version minimale requise pour l’application  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Cliquez sur le **mises à jour** bouton pour ouvrir la **mises à jour de l’Application** boîte de dialogue.  
  
4.  Dans le **mises à jour de l’Application** boîte de dialogue zone, assurez-vous que le **l’application doit vérifier les mises à jour** case à cocher est activée.  
  
5.  Sélectionnez le **spécifier une version minimale requise pour cette application** case à cocher, puis entrez **majeure**, **mineure**, **Build**et  **Révision** nombres pour l’application.  
  
### <a name="to-specify-a-different-update-location"></a>Pour spécifier un emplacement différent de mise à jour  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Cliquez sur le **mises à jour** bouton pour ouvrir la **mises à jour de l’Application** boîte de dialogue.  
  
4.  Dans le **mises à jour de l’Application** boîte de dialogue zone, assurez-vous que le **l’application doit vérifier les mises à jour** case à cocher est activée.  
  
5.  Dans le **mettre à jour emplacement** , entrez l’emplacement de mise à jour avec une URL qualifiée complète, en utilisant le format *http://Hostname/ApplicationName*, ou un chemin d’accès UNC au format  *\\\Server\ ApplicationName*, ou cliquez sur le **Parcourir** bouton pour rechercher l’emplacement de mise à jour.  
  
### <a name="to-check-for-updates-programmatically"></a>Pour vérifier les mises à jour par programmation  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Cliquez sur le **mises à jour** bouton pour ouvrir la **mises à jour de l’Application** boîte de dialogue.  
  
4.  Dans le **mises à jour de l’Application** boîte de dialogue zone, assurez-vous que le **l’application doit vérifier les mises à jour** case à cocher est désactivée. (Si vous le souhaitez, vous pouvez sélectionner cette case à cocher pour vérifier des mises à jour par programmation et laisser également le runtime ClickOnce vérifier automatiquement les mises à jour).  
  
5.  Dans le **mettre à jour emplacement** , entrez l’emplacement de mise à jour avec une URL qualifiée complète, en utilisant le format *http://Hostname/ApplicationName*, ou un chemin d’accès UNC au format  *\\\Server\ ApplicationName*, ou cliquez sur le **Parcourir** bouton pour rechercher l’emplacement de mise à jour. Mise à jour se trouve dans laquelle l’application recherche une version mise à jour de lui-même.  
  
6.  Créer un bouton, un élément de menu ou autre élément d’interface utilisateur sur un formulaire Windows qui sélectionnent les utilisateurs pour rechercher les mises à jour. À partir du Gestionnaire d’événements de cet élément, appelez une méthode pour vérifier et installer les mises à jour. Vous trouverez un exemple de code Visual Basic et Visual c# pour une telle méthode dans [Comment : rechercher les mises à jour de l’application par programmation à l’aide de l’API du déploiement ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).  
  
7.  Générez votre application.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [Boîte de dialogue application mises à jour](/previous-versions/visualstudio/visual-studio-2010/axw1fa38(v=vs.100))   
 [Choisir une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publier la liaison de ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Comment : rechercher les mises à jour de l’application par programmation à l’aide de l’API du déploiement ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)