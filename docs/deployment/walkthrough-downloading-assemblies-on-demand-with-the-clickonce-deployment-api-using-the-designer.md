---
title: Télécharger les assemblys à la demande à l’aide du concepteur (API ClickOnce)
description: Découvrez comment marquer certains assemblys dans votre application ClickOnce comme facultatifs à l’aide du concepteur et les télécharger quand le common language runtime en a besoin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- Windows applications, ClickOnce deployments
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: 59a0dd5f-1cab-4f2f-b780-0ab7399905d5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 597f633c1f92b09add06909b8cb626262de1156f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350346"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Procédure pas à pas : Téléchargement d’assemblys à la demande avec l’API de déploiement ClickOnce à l’aide du concepteur
Par défaut, tous les assemblys inclus dans une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sont téléchargés lors de la première exécution de l’application. Toutefois, il peut y avoir certaines parties de votre application qui sont utilisées par un petit ensemble d’utilisateurs. Dans ce cas, vous souhaiterez sans doute télécharger un assembly uniquement quand vous créez l’un de ses types. La procédure suivante montre comment marquer certains assemblys de votre application comme « facultatifs » et comment les télécharger à l’aide de classes dans l’espace de noms <xref:System.Deployment.Application> quand le Common Language Runtime en a besoin.

> [!NOTE]
> Votre application doit s’exécuter avec une confiance totale pour utiliser cette procédure.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier ces paramètres, cliquez sur **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

## <a name="create-the-projects"></a>Créer les projets

### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Pour créer un projet qui utilise un assembly à la demande avec Visual Studio

1. Créez un projet Windows Forms dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dans le menu **Fichier** , pointez sur **Ajouter** , puis cliquez sur **Nouveau projet**. Choisissez un projet de **Bibliothèque de classes** dans la boîte de dialogue et nommez-le `ClickOnceLibrary`.

   > [!NOTE]
   > Dans Visual Basic, nous vous recommandons de modifier les propriétés du projet pour affecter `Microsoft.Samples.ClickOnceOnDemand` ou un espace de noms de votre choix comme espace de noms racine pour ce projet. Pour des raisons de simplicité, les deux projets de cette procédure pas à pas sont dans le même espace de noms.

2. Définissez une classe nommée `DynamicClass` avec une propriété unique nommée `Message`.

    [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.vb)]
    [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]

3. Sélectionnez le projet Windows Forms dans l’ **Explorateur de solutions**. Ajoutez une référence à l’assembly <xref:System.Deployment.Application> et une référence de projet au projet `ClickOnceLibrary` .

   > [!NOTE]
   > Dans Visual Basic, nous vous recommandons de modifier les propriétés du projet pour affecter `Microsoft.Samples.ClickOnceOnDemand` ou un espace de noms de votre choix comme espace de noms racine pour ce projet. Pour des raisons de simplicité, les deux projets de cette procédure pas à pas figurent dans le même espace de noms.

4. Cliquez avec le bouton droit sur le formulaire, cliquez sur **Afficher le code** dans le menu, puis ajoutez les références suivantes au formulaire.

    [!code-csharp[ClickOnceOnDemand#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.cs)]
    [!code-vb[ClickOnceOnDemand#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]

5. Ajoutez le code suivant pour télécharger cet assembly à la demande. Ce code montre comment mapper un jeu d’assemblys à un nom de groupe à l’aide d’une classe <xref:System.Collections.DictionaryBase.Dictionary%2A> générique. Comme nous ne téléchargeons qu’un seul assembly dans cette procédure pas à pas, il n’y a qu’un seul assembly dans notre groupe. Dans une application réelle, il faudrait probablement télécharger simultanément tous les assemblys liés à une même fonctionnalité dans votre application. La table de mappage vous permet de le faire facilement en associant toutes les DLL qui appartiennent à une fonctionnalité à un nom de groupe de téléchargement.

    [!code-csharp[ClickOnceOnDemand#2](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.cs)]
    [!code-vb[ClickOnceOnDemand#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]

6. Dans le menu **Affichage** , cliquez sur **Boîte à outils**. Faites glisser un <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers le formulaire. Double-cliquez sur le bouton et ajoutez le code suivant au gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> .

    [!code-csharp[ClickOnceOnDemand#3](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_4.cs)]
    [!code-vb[ClickOnceOnDemand#3](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_4.vb)]

## <a name="mark-assemblies-as-optional"></a>Marquer les assemblys comme facultatifs

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Pour marquer des assemblys comme facultatifs dans votre application ClickOnce à l’aide de Visual Studio

1. Cliquez avec le bouton droit sur le projet Windows Forms dans l’ **Explorateur de solutions** , puis cliquez sur **Propriétés**. Sélectionnez l’onglet **Publier** .

2. Cliquez sur le bouton **Fichiers d’application** .

3. Recherchez la liste de *ClickOnceLibrary.dll*. Affectez la valeur **Inclure** à la zone de liste déroulante **État de la publication**.

4. Développez la zone de liste déroulante **Groupe** et sélectionnez **Nouveau**. Entrez `ClickOnceLibrary` comme nom du nouveau groupe.

5. Continuez la publication de votre application comme décrit dans [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>Pour marquer des assemblys comme facultatifs dans votre application ClickOnce à l’aide de l’Outil Manifest Generation and Editing — Client graphique (MageUI.exe)

1. Créez vos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestes comme décrit dans [procédure pas à pas : déployer manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

2. Avant de fermer MageUI.exe, sélectionnez l’onglet qui contient le manifeste d’application de votre déploiement et, sous cet onglet, sélectionnez l’onglet **Fichiers** .

3. Recherchez ClickOnceLibrary.dll dans la liste des fichiers d’application et affectez la valeur **Aucun** à sa colonne **Type de fichier**. Pour la colonne **Groupe** , tapez `ClickOnceLibrary.dll`.

## <a name="test-the-new-assembly"></a>Tester le nouvel assembly

Pour tester votre assembly à la demande :

1. Démarrez votre application déployée avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

2. Quand votre formulaire principal apparaît, appuyez sur <xref:System.Windows.Forms.Button>. Une chaîne « Hello, World ! » doit apparaître dans une fenêtre de message.

## <a name="see-also"></a>Voir aussi

- <xref:System.Deployment.Application.ApplicationDeployment>
