---
title: "Procédure pas à pas : Téléchargement d’assemblys à la demande avec l’API du déploiement ClickOnce | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 640c0852a3745d11aae119e3c00e024b594d9132
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Procédure pas à pas : téléchargement d'assemblys à la demande avec l'API du déploiement ClickOnce
Par défaut, tous les assemblys inclus dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application sont téléchargées lors de la première exécution de l’application. Toutefois, vous pouvez avoir des parties de votre application qui sont utilisés par un petit ensemble de vos utilisateurs. Dans ce cas, vous souhaiterez sans doute télécharger un assembly uniquement quand vous créez l’un de ses types. La procédure suivante montre comment marquer certains assemblys de votre application comme « facultatifs » et les télécharger à l’aide de classes dans le <xref:System.Deployment.Application> espace de noms lorsque le common language runtime (CLR) en a besoin.  
  
> [!NOTE]
>  Votre application doit s’exécuter avec une confiance totale pour utiliser cette procédure.  
  
## <a name="prerequisites"></a>Prérequis  
 Vous avez besoin d’un des composants suivants pour effectuer cette procédure pas à pas :  
  
-   Le SDK Windows. Le Kit de développement logiciel Windows peuvent être téléchargé à partir du Microsoft Download Center.  
  
-   Visual Studio.  
  
## <a name="creating-the-projects"></a>Création des projets  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Pour créer un projet qui utilise un assembly à la demande  
  
1.  Créez un répertoire nommé ClickOnceOnDemand.  
  
2.  Ouvrez l’invite de commandes du Kit de développement logiciel Windows ou le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] invite de commandes.  
  
3.  Accédez au répertoire ClickOnceOnDemand.  
  
4.  Générer une paire de clés publique/privée à l’aide de la commande suivante :  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  Utilisez le bloc-notes ou un autre éditeur de texte, définissez une classe nommée `DynamicClass` avec une propriété unique nommée `Message`.  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  Enregistrer le texte dans un fichier nommé `ClickOnceLibrary.cs` ou `ClickOnceLibrary.vb`, selon la langue que vous utilisez, dans le répertoire ClickOnceOnDemand.  
  
7.  Compilez le fichier dans un assembly.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  Pour obtenir la clé publique jeton pour l’assembly, utilisez la commande suivante :  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Créer un nouveau fichier à l’aide du texte de votre éditeur et entrez le code suivant. Ce code crée une application Windows Forms qui télécharge l’assembly BibliothèqueClickOnce lorsqu’il est requis.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. Dans le code, localisez l’appel à <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Définissez`PublicKeyToken` à la valeur que vous avez récupéré le plus haut.  
  
12. Enregistrez le fichier sous la forme `Form1.cs` ou `Form1.vb`.  
  
13. Le compiler dans un fichier exécutable à l’aide de la commande suivante.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Marquage d’assemblys comme facultatifs  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Pour marquer des assemblys comme étant facultatifs dans votre application ClickOnce à l’aide de MageUI.exe  
  
1.  À l’aide de MageUI.exe, créez un manifeste d’application comme décrit dans [procédure pas à pas : déploiement manuel d’une Application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Utilisez les paramètres suivants pour le manifeste d’application :  
  
    -   Nommez le manifeste d’application `ClickOnceOnDemand`.  
  
    -   Sur le **fichiers** page, dans la ligne ClickOnceLibrary.dll, définissez la **Type de fichier** colonne **aucun**.  
  
    -   Sur le **fichiers** page, dans le type de la ligne ClickOnceLibrary.dll `ClickOnceLibrary.dll` dans les **groupe** colonne.  
  
2.  À l’aide de MageUI.exe, créez un manifeste de déploiement comme décrit dans [procédure pas à pas : déploiement manuel d’une Application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Utilisez les paramètres suivants pour le manifeste de déploiement :  
  
    -   Nommez le manifeste de déploiement `ClickOnceOnDemand`.  
  
## <a name="testing-the-new-assembly"></a>Test du nouvel assembly  
  
#### <a name="to-test-your-on-demand-assembly"></a>Pour tester votre assembly à la demande  
  
1.  Télécharger votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement sur un serveur Web.  
  
2.  Démarrez votre application déployée avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à partir d’un navigateur Web en entrant l’URL du manifeste de déploiement. Si vous appelez votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application `ClickOnceOnDemand`et chargez-le dans le répertoire racine de adatum.com, votre URL ressemble à ceci :  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Quand votre formulaire principal apparaît, appuyez sur <xref:System.Windows.Forms.Button>. Vous devez voir une chaîne dans une fenêtre de message qui indique « Hello, World ! ».  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Deployment.Application.ApplicationDeployment>