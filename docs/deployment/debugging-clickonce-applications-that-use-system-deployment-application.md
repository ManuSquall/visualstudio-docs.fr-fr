---
title: Débogage des Applications ClickOnce qui utilisent System.Deployment.Application | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c877c3373f7d028291b521558a04fafd56e022c6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836357"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>Déboguer des applications ClickOnce qui utilisent System.Deployment.Application
Dans [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement vous permet de configurer la façon dont une application est mise à jour. Toutefois, si vous souhaitez utiliser et personnaliser avancés [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] des fonctionnalités de déploiement, vous devrez accéder au modèle objet de déploiement fourni par <xref:System.Deployment.Application>. Vous pouvez utiliser le <xref:System.Deployment.Application> API pour des tâches avancées telles que :  
  
- Création d’une option « Mise à jour maintenant » dans votre application  
  
- Conditionnel, les téléchargements à la demande de différents composants d’application  
  
- Mises à jour directement intégré à l’application  
  
- Ce qui garantit que l’application cliente est toujours à jour  
  
  Étant donné que le <xref:System.Deployment.Application> API fonctionnent uniquement quand une application est déployée avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] technologie, la seule façon de les déboguer est de déployer l’application à l’aide [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], attacher à celui-ci, puis à la déboguer. Il peut être difficile d’attacher le débogueur suffisamment tôt, étant donné que ce code s’exécute souvent lorsque l’application démarre et s’exécute avant que vous pouvez attacher le débogueur. Une solution consiste à placer des sauts (ou s’arrête, pour les projets Visual Basic) avant votre code de vérification de mise à jour ou le code de la demande.  
  
  La technique de débogage recommandée est la suivante :  
  
1. Avant de commencer, assurez-vous que les symboles (.pdb) et les fichiers sources sont archivés.  
  
2. Déployez la version 1 de l’application.  
  
3. Créer une nouvelle solution vide. À partir de la **fichier** menu, cliquez sur **New**, puis **projet**. Dans le **nouveau projet** boîte de dialogue, ouvrez le **autres Types de projets** nœud, puis sélectionnez le **Solutions Visual Studio** dossier. Dans le **modèles** volet, sélectionnez **nouvelle Solution**.  
  
4. Ajoutez l’emplacement source archivé aux propriétés pour cette nouvelle solution. Dans **l’Explorateur de solutions**, cliquez sur le nœud de solution, puis cliquez sur **propriétés**. Dans le **Pages de propriétés** boîte de dialogue, sélectionnez **déboguer les fichiers sources**, puis ajoutez le répertoire du code source archivé. Sinon, le débogueur recherchera les fichiers sources obsolètes, étant donné que les chemins d’accès du fichier source sont enregistrées dans le fichier .pdb. Si le débogueur utilise des fichiers sources obsolètes, vous voyez un message indiquant que la source ne correspond pas à vous.  
  
5. Assurez-vous que le débogueur peut trouver la *.pdb* fichiers. Si vous avez déployés avec votre application, le débogueur les trouve automatiquement. Il toujours commence par rechercher en regard de l’assembly en question. Dans le cas contraire, vous devez ajouter le chemin d’accès de l’archive à le **emplacements du fichier (.pdb) de symboles** (pour accéder à cette option, à partir de la **outils** menu, cliquez sur **Options**, puis ouvrez le  **Débogage** nœud, puis cliquez sur **symboles**).  
  
6. Déboguer ce qui se passe entre le `CheckForUpdate` et `Download` / `Update` les appels de méthode.  
  
    Par exemple, le code de mise à jour peut être comme suit :  
  
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
  
8. Essayer d’attacher le débogueur à l’application de la version 1 pendant le téléchargement d’une mise à jour pour la version 2. Vous pouvez également utiliser le `System.Diagnostics.Debugger.Break` méthode ou simplement `Stop` en Visual Basic. Bien sûr, vous ne devez pas laisser ces appels de méthode dans le code de production.  
  
    Par exemple, supposons que vous développiez une application Windows Forms, et que vous avez un gestionnaire d’événements pour cette méthode avec la logique de mise à jour qu’il contient. Pour déboguer ce, simplement un attachement avant le bouton est enfoncé, puis définissez un point d’arrêt (Assurez-vous que vous ouvrez le fichier archivé approprié et définissez le point d’arrêt).  
  
   Utilisez le <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> propriété à appeler le <xref:System.Deployment.Application> API uniquement lorsque l’application est déployée ; les API ne doivent pas être appelés pendant le débogage dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Deployment.Application>