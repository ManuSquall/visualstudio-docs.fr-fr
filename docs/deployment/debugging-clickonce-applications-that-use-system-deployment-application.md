---
title: Déboguer des applications ClickOnce qui utilisent System. Deployment. application
description: Découvrez comment utiliser et personnaliser les fonctionnalités avancées de déploiement ClickOnce en accédant au modèle objet de déploiement fourni par System. Deployment. application.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6a014afff6c26b8cfe8f4f7fae508f78ef5905f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912243"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>Déboguer des applications ClickOnce qui utilisent System.Deployment.Application
Dans [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le déploiement vous permet de configurer la façon dont une application est mise à jour. Toutefois, si vous devez utiliser et personnaliser des [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fonctionnalités de déploiement avancées, vous devrez accéder au modèle objet de déploiement fourni par <xref:System.Deployment.Application> . Vous pouvez utiliser les <xref:System.Deployment.Application> API pour des tâches avancées telles que :

- Création d’une option « mettre à jour maintenant » dans votre application

- Téléchargements conditionnels à la demande de différents composants d’application

- Mises à jour intégrées directement dans l’application

- Garantir que l’application cliente est toujours à jour

  Étant donné que les <xref:System.Deployment.Application> API fonctionnent uniquement quand une application est déployée avec la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] technologie, le seul moyen de les déboguer consiste à déployer l’application à l’aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , à s’y attacher, puis à la déboguer. Il peut être difficile de joindre le débogueur suffisamment tôt, car ce code s’exécute souvent lorsque l’application démarre et s’exécute avant que vous ne puissiez attacher le débogueur. Une solution consiste à placer des arrêts (ou des arrêts pour les projets Visual Basic) avant votre code de vérification de la mise à jour ou votre code à la demande.

  La technique de débogage recommandée est la suivante :

1. Avant de commencer, assurez-vous que les fichiers de symboles (. pdb) et les fichiers sources sont archivés.

2. Déployez la version 1 de l’application.

3. Créez une nouvelle solution vide. Dans le menu **Fichier**, cliquez sur **Nouveau**, puis sur **Projet**. Dans la boîte de dialogue **nouveau projet** , ouvrez le nœud **autres types de projets** , puis sélectionnez le dossier **solutions Visual Studio** . Dans le volet **modèles** , sélectionnez **solution vide**.

4. Ajoutez l’emplacement source archivé aux propriétés de cette nouvelle solution. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de la solution, puis cliquez sur **Propriétés**. Dans la boîte de dialogue **pages de propriétés** , sélectionnez fichiers sources pour le **débogage**, puis ajoutez le répertoire du code source archivé. Dans le cas contraire, le débogueur trouvera les fichiers sources obsolètes, car les chemins d’accès aux fichiers sources sont enregistrés dans le fichier. pdb. Si le débogueur utilise des fichiers sources obsolètes, un message s’affiche pour vous indiquer que la source ne correspond pas.

5. Assurez-vous que le débogueur peut trouver les fichiers *. pdb* . Si vous les avez déployées avec votre application, le débogueur les trouve automatiquement. Elle apparaît toujours en regard de l’assembly en question en premier. Dans le cas contraire, vous devrez ajouter le chemin d’archivage aux **emplacements du fichier de symboles (. pdb)** (pour accéder à cette option, dans le menu **Outils** , cliquez sur **options**, puis ouvrez le nœud **débogage** et cliquez sur **symboles**).

6. Déboguez ce qui se passe entre les `CheckForUpdate` `Download` / `Update` appels de méthode et.

    Par exemple, le code de mise à jour peut être le suivant :

   ```vb
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
           If My.Application.Deployment.IsNetworkDeployed Then

               If (My.Application.Deployment.CheckForUpdate()) Then

                   My.Application.Deployment.Update()
                   Application.Restart()

               End If

           End If
       End Sub
   ```

7. Déployez la version 2.

8. Essayez d’attacher le débogueur à l’application version 1 lors du téléchargement d’une mise à jour pour la version 2. Vous pouvez également utiliser la `System.Diagnostics.Debugger.Break` méthode ou simplement `Stop` dans Visual Basic. Bien entendu, vous ne devez pas conserver ces appels de méthode dans le code de production.

    Par exemple, supposons que vous développiez une application Windows Forms, et que vous ayez un gestionnaire d’événements pour cette méthode avec la logique de mise à jour qu’elle contient. Pour déboguer cela, il vous suffit d’attacher avant d’appuyer sur le bouton, de définir un point d’arrêt (veillez à ouvrir le fichier archivé approprié et à y définir le point d’arrêt).

   Utilisez la <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> propriété pour appeler les <xref:System.Deployment.Application> API uniquement lorsque l’application est déployée ; les API ne doivent pas être appelées pendant le débogage dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Voir aussi
- <xref:System.Deployment.Application>