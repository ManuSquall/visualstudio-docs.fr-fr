---
title: 'Procédure pas à pas : Téléchargement d’assemblys à la demande avec l’API à l’aide du concepteur du déploiement ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 009a2a264ac1605983378197b427cfe7490e5cae
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434952"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Procédure pas à pas : Téléchargement d’assemblys à la demande avec l’API à l’aide du concepteur du déploiement ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Par défaut, tous les assemblys inclus dans une application [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] sont téléchargés lors de la première exécution de l’application. Toutefois, il peut y avoir certaines parties de votre application qui sont utilisées par un petit ensemble d’utilisateurs. Dans ce cas, vous souhaiterez sans doute télécharger un assembly uniquement quand vous créez l’un de ses types. La procédure suivante montre comment marquer certains assemblys de votre application comme « facultatifs » et comment les télécharger à l’aide de classes dans l’espace de noms <xref:System.Deployment.Application> quand le Common Language Runtime en a besoin.  
  
> [!NOTE]
> Votre application doit s’exécuter avec une confiance totale pour utiliser cette procédure.  
  
> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier ces paramètres, cliquez sur **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-projects"></a>Création des projets  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Pour créer un projet qui utilise un assembly à la demande avec Visual Studio  
  
1. Créez un projet Windows Forms dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Dans le menu **Fichier** , pointez sur **Ajouter**, puis cliquez sur **Nouveau projet**. Choisissez un projet de **Bibliothèque de classes** dans la boîte de dialogue et nommez-le `ClickOnceLibrary`.  
  
    > [!NOTE]
    > Dans Visual Basic, nous vous recommandons de modifier les propriétés du projet pour affecter `Microsoft.Samples.ClickOnceOnDemand` ou un espace de noms de votre choix comme espace de noms racine pour ce projet. Pour des raisons de simplicité, les deux projets de cette procédure pas à pas sont dans le même espace de noms.  
  
2. Définissez une classe nommée `DynamicClass` avec une propriété unique nommée `Message`.  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
3. Sélectionnez le projet Windows Forms dans l’ **Explorateur de solutions**. Ajoutez une référence à l’assembly <xref:System.Deployment.Application> et une référence de projet au projet `ClickOnceLibrary` .  
  
    > [!NOTE]
    > Dans Visual Basic, nous vous recommandons de modifier les propriétés du projet pour affecter `Microsoft.Samples.ClickOnceOnDemand` ou un espace de noms de votre choix comme espace de noms racine pour ce projet. Pour des raisons de simplicité, les deux projets de cette procédure pas à pas figurent dans le même espace de noms.  
  
4. Cliquez avec le bouton droit sur le formulaire, cliquez sur **Afficher le code** dans le menu, puis ajoutez les références suivantes au formulaire.  
  
     [!code-csharp[ClickOnceOnDemand#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemand#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#1)]  
  
5. Ajoutez le code suivant pour télécharger cet assembly à la demande. Ce code montre comment mapper un jeu d’assemblys à un nom de groupe à l’aide d’une classe <xref:System.Collections.DictionaryBase.Dictionary%2A> générique. Comme nous ne téléchargeons qu’un seul assembly dans cette procédure pas à pas, il n’y a qu’un seul assembly dans notre groupe. Dans une application réelle, il faudrait probablement télécharger simultanément tous les assemblys liés à une même fonctionnalité dans votre application. La table de mappage vous permet de le faire facilement en associant toutes les DLL qui appartiennent à une fonctionnalité à un nom de groupe de téléchargement.  
  
     [!code-csharp[ClickOnceOnDemand#2](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#2)]
     [!code-vb[ClickOnceOnDemand#2](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#2)]  
  
6. Dans le menu **Affichage** , cliquez sur **Boîte à outils**. Faites glisser un <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers le formulaire. Double-cliquez sur le bouton et ajoutez le code suivant au gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> .  
  
     [!code-csharp[ClickOnceOnDemand#3](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#3)]
     [!code-vb[ClickOnceOnDemand#3](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#3)]  
  
## <a name="marking-assemblies-as-optional"></a>Marquage d’assemblys comme facultatifs  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Pour marquer des assemblys comme facultatifs dans votre application ClickOnce à l’aide de Visual Studio  
  
1. Cliquez avec le bouton droit sur le projet Windows Forms dans l’ **Explorateur de solutions** , puis cliquez sur **Propriétés**. Sélectionnez l’onglet **Publier** .  
  
2. Cliquez sur le bouton **Fichiers d’application** .  
  
3. Recherchez ClickOnceLibrary.dll dans la liste. Affectez la valeur **Inclure** à la zone de liste déroulante **État de la publication**.  
  
4. Développez la zone de liste déroulante **Groupe** et sélectionnez **Nouveau**. Entrez `ClickOnceLibrary` comme nom du nouveau groupe.  
  
5. Poursuivez la publication de votre application comme décrit dans [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>Pour marquer des assemblys comme facultatifs dans votre application ClickOnce à l’aide de l’Outil Manifest Generation and Editing — Client graphique (MageUI.exe)  
  
1. Créer votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] se manifeste comme décrit dans [procédure pas à pas : déploiement manuel d’une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2. Avant de fermer MageUI.exe, sélectionnez l’onglet qui contient le manifeste d’application de votre déploiement et, sous cet onglet, sélectionnez l’onglet **Fichiers** .  
  
3. Recherchez ClickOnceLibrary.dll dans la liste des fichiers d’application et affectez la valeur **Aucun** à sa colonne **Type de fichier**. Pour la colonne **Groupe** , tapez `ClickOnceLibrary.dll`.  
  
## <a name="testing-the-new-assembly"></a>Test du nouvel assembly  
  
#### <a name="to-test-your-on-demand-assembly"></a>Pour tester votre assembly à la demande  
  
1. Démarrez votre application déployée avec [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
2. Quand votre formulaire principal apparaît, appuyez sur <xref:System.Windows.Forms.Button>. Une chaîne « Hello, World ! » doit apparaître dans une fenêtre de message.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Deployment.Application.ApplicationDeployment>
