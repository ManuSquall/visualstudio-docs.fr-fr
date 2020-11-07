---
title: Gérer les mises à jour pour une application ClickOnce | Microsoft Docs
description: Découvrez les options permettant de rechercher des mises à jour automatiquement ou par programme pour vos applications ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc2fd7b9e58cac0b013c511e17a6a9744e87ca39
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351178"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Guide pratique pour gérer les mises à jour pour une application ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] les applications peuvent rechercher des mises à jour automatiquement ou par programme. En tant que développeur, vous disposez d’une grande flexibilité pour spécifier quand et comment les vérifications de mise à jour sont effectuées, si les mises à jour sont obligatoires et si l’application doit rechercher les mises à jour.

 Vous pouvez configurer l’application pour qu’elle recherche automatiquement les mises à jour avant le démarrage de l’application, ou à des intervalles définis après le démarrage de l’application. En outre, vous pouvez spécifier une version minimale requise ; autrement dit, une mise à jour est installée si la version de l’utilisateur est antérieure à la version requise.

 Vous pouvez configurer l’application pour rechercher des mises à jour par programmation en fonction d’un événement tel qu’une demande de l’utilisateur. La procédure « pour rechercher des mises à jour par programmation » dans cette rubrique montre comment écrire du code qui utilise la <xref:System.Deployment.Application.ApplicationDeployment> classe pour rechercher des mises à jour en fonction d’un événement.

 Vous pouvez également déployer votre application à partir d’un emplacement et la mettre à jour à partir d’une autre. Consultez la procédure « pour spécifier un autre emplacement de mise à jour ».

 Pour plus d’informations, consultez [choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

 Le comportement de la mise à jour est géré dans la boîte de dialogue **mises à jour des applications** , disponible à partir de la page **publier** du **Concepteur de projet.**

### <a name="to-check-for-updates-before-the-application-starts"></a>Pour rechercher les mises à jour avant le démarrage de l’application

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions** , dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Cliquez sur le bouton **mises à jour** pour ouvrir la boîte de dialogue **mises à jour des applications** .

4. Dans la boîte de dialogue **mises à jour des applications** , assurez-vous que la case à cocher **l’application doit vérifier les mises à jour** est activée.

5. Dans la section **Choisissez à quel moment l’application doit vérifier les mises à jour** , sélectionnez **avant le démarrage de l’application**. Cela garantit que les utilisateurs connectés au réseau exécutent toujours l’application avec les dernières mises à jour.

### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Vérifier les mises à jour en arrière-plan, après le démarrage de l’application

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions** , dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Cliquez sur le bouton **mises à jour** pour ouvrir la boîte de dialogue **mises à jour des applications** .

4. Dans la boîte de dialogue **mises à jour des applications** , assurez-vous que la case à cocher **l’application doit rechercher les mises à jour** est sélectionnée.

5. Dans la **section Choisissez à quel moment l’application doit vérifier les mises à jour** , sélectionnez **après le démarrage de l’application**. L’application démarre plus rapidement de cette manière, puis vérifie si des mises à jour sont disponibles en arrière-plan et n’avertit l’utilisateur qu’une fois qu’une mise à jour est disponible. Une fois installé, les mises à jour ne prennent effet qu’après le redémarrage de l’application.

6. Dans la section **spécifier à quelle fréquence l’application doit vérifier les mises à jour** , sélectionnez **vérifier chaque fois que l’application s’exécute** (valeur par défaut) ou **Vérifier toutes** les, puis entrez un nombre et un intervalle de temps.

### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Pour spécifier une version minimale requise pour l’application

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions** , dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Cliquez sur le bouton **mises à jour** pour ouvrir la boîte de dialogue **mises à jour des applications** .

4. Dans la boîte de dialogue **mises à jour des applications** , assurez-vous que la case à cocher **l’application doit vérifier les mises à jour** est activée.

5. Activez la case à cocher **spécifier une version minimale requise pour cette application** , puis entrez les numéros **principal** , **secondaire** , de **Build** et de **révision** de l’application.

### <a name="to-specify-a-different-update-location"></a>Pour spécifier un autre emplacement de mise à jour

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions** , dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Cliquez sur le bouton **mises à jour** pour ouvrir la boîte de dialogue **mises à jour des applications** .

4. Dans la boîte de dialogue **mises à jour des applications** , assurez-vous que la case à cocher **l’application doit vérifier les mises à jour** est activée.

5. Dans le champ emplacement de la **mise à** jour, entrez l’emplacement de la mise à jour avec une URL complète, en utilisant le format *http://Hostname/ApplicationName* ou un chemin UNC au format *\\ \Server\ApplicationName* , ou cliquez sur le bouton **Parcourir** pour Rechercher l’emplacement de mise à jour.

### <a name="to-check-for-updates-programmatically"></a>Pour rechercher des mises à jour par programmation

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions** , dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Cliquez sur le bouton **mises à jour** pour ouvrir la boîte de dialogue **mises à jour des applications** .

4. Dans la boîte de dialogue **mises à jour des applications** , assurez-vous que la case à cocher **l’application doit vérifier les mises à jour** est désactivée. (Si vous le souhaitez, vous pouvez activer cette case à cocher pour rechercher des mises à jour par programme et également permettre au runtime ClickOnce de vérifier automatiquement les mises à jour.)

5. Dans le champ emplacement de la **mise à** jour, entrez l’emplacement de la mise à jour avec une URL complète, en utilisant le format *http://Hostname/ApplicationName* ou un chemin UNC au format *\\ \Server\ApplicationName* , ou cliquez sur le bouton **Parcourir** pour Rechercher l’emplacement de mise à jour. L’emplacement de la mise à jour est l’emplacement où l’application recherchera une version mise à jour de elle-même.

6. Créez un bouton, un élément de menu ou un autre élément d’interface utilisateur dans un Windows Form que les utilisateurs sélectionneront pour rechercher les mises à jour. À partir du gestionnaire d’événements de cet élément, appelez une méthode pour vérifier et installer les mises à jour. Vous trouverez un exemple de code Visual Basic et Visual C# pour une telle méthode dans [Comment : Rechercher des mises à jour d’application par programme à l’aide de l’API de déploiement ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).

7. Générez votre application.

## <a name="see-also"></a>Voir aussi
- <xref:System.Deployment.Application.ApplicationDeployment>
- [Boîte de dialogue Mises à jour des applications](/previous-versions/visualstudio/visual-studio-2010/axw1fa38(v=vs.100))
- [Choisir une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Guide pratique pour vérifier la disponibilité de mises à jour des applications par programmation à l’aide de l’API du déploiement ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)
