---
title: 'Procédure pas à pas : Téléchargement d’assemblys à la demande avec l’API du déploiement ClickOnce | Microsoft Docs'
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
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 767c1b93972a5e8fc78b7de46a69d8f464fe85cc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953140"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Procédure pas à pas : Téléchargement d’assemblys à la demande avec l’API du déploiement ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Par défaut, tous les assemblys inclus dans un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application sont téléchargés lors de la première exécution de l’application. Toutefois, vous pouvez avoir des parties de votre application qui sont utilisés par un petit ensemble de vos utilisateurs. Dans ce cas, vous souhaiterez sans doute télécharger un assembly uniquement quand vous créez l’un de ses types. La procédure suivante montre comment marquer certains assemblys de votre application comme « facultatifs » et comment les télécharger à l’aide de classes dans l’espace de noms <xref:System.Deployment.Application> quand le Common Language Runtime en a besoin.  
  
> [!NOTE]
>  Votre application doit s’exécuter avec une confiance totale pour utiliser cette procédure.  
  
## <a name="prerequisites"></a>Prérequis  
 Vous pouvez utiliser un des composants suivants pour terminer cette procédure pas à pas :  
  
-   Le Kit de développement logiciel Windows. Le Kit de développement logiciel Windows peut être téléchargé à partir du Microsoft Download Center.  
  
-   Visual Studio.  
  
## <a name="creating-the-projects"></a>Création des projets  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Pour créer un projet qui utilise un assembly à la demande  
  
1.  Créez un répertoire nommé ClickOnceOnDemand.  
  
2.  Ouvrez l’invite de commandes du Kit de développement logiciel Windows ou le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] invite de commandes.  
  
3.  Accédez au répertoire ClickOnceOnDemand.  
  
4.  Générer une paire de clés publique/privée à l’aide de la commande suivante :  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  Le bloc-notes ou un autre éditeur de texte, définissez une classe nommée `DynamicClass` avec une propriété unique nommée `Message`.  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
6.  Enregistrez le texte dans un fichier nommé `ClickOnceLibrary.cs` ou `ClickOnceLibrary.vb`, selon le langage que vous utilisez, dans le répertoire ClickOnceOnDemand.  
  
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
  
9. Créer un nouveau fichier à l’aide du texte de votre éditeur et entrez le code suivant. Ce code crée une application Windows Forms qui télécharge l’assembly BibliothèqueClickOnce lorsque cela est nécessaire.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/VB/Form1.vb#1)]  
  
10. Dans le code, recherchez l’appel à <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Définissez`PublicKeyToken` à la valeur que vous avez récupéré précédemment.  
  
12. Enregistrez le fichier en tant que `Form1.cs` ou `Form1.vb`.  
  
13. Compilez-le dans un fichier exécutable à l’aide de la commande suivante.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Marquage d’assemblys comme facultatifs  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Pour marquer des assemblys comme facultatifs dans votre application ClickOnce à l’aide de MageUI.exe  
  
1.  À l’aide de MageUI.exe, créez un manifeste d’application comme décrit dans [procédure pas à pas : déploiement manuel d’une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Utilisez les paramètres suivants pour le manifeste d’application :  
  
    -   Nommez le manifeste d’application `ClickOnceOnDemand`.  
  
    -   Sur le **fichiers** page, dans la ligne ClickOnceLibrary.dll, définissez le **Type de fichier** colonne à **aucun**.  
  
    -   Sur le **fichiers** page, dans le type de la ligne ClickOnceLibrary.dll `ClickOnceLibrary.dll` dans le **groupe** colonne.  
  
2.  À l’aide de MageUI.exe, créez un manifeste de déploiement comme décrit dans [procédure pas à pas : déploiement manuel d’une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Utilisez les paramètres suivants pour le manifeste de déploiement :  
  
    -   Nommez le manifeste de déploiement `ClickOnceOnDemand`.  
  
## <a name="testing-the-new-assembly"></a>Test du nouvel assembly  
  
#### <a name="to-test-your-on-demand-assembly"></a>Pour tester votre assembly à la demande  
  
1.  Télécharger votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déploiement sur un serveur Web.  
  
2.  Démarrez votre application déployée avec [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] depuis un navigateur Web en entrant l’URL dans le manifeste de déploiement. Si vous appelez votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application `ClickOnceOnDemand`et chargez-le dans le répertoire racine de adatum.com, votre URL ressemblerait à ceci :  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Quand votre formulaire principal apparaît, appuyez sur <xref:System.Windows.Forms.Button>. Une chaîne « Hello, World ! » doit apparaître dans une fenêtre de message.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Deployment.Application.ApplicationDeployment>
