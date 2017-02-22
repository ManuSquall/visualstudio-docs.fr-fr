---
title: "Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "assemblies, downloading [ClickOnce]"
  - "ClickOnce deployment, on-demand download"
  - "on-demand assemblies, ClickOnce"
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Par défaut, tous les assemblys inclus dans une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sont téléchargés lors de la première exécution de l'application.  Toutefois, certaines parties de votre application peuvent n'être utilisées que par un petit nombre d'utilisateurs.  Dans ce cas, vous souhaitez télécharger un assembly uniquement lorsque vous créez l'un de ses types.  La procédure pas à pas suivante montre comment marquer certains assemblys de votre application comme « facultatifs » et les télécharger à l'aide de classes de l'espace de noms <xref:System.Deployment.Application> lorsque le Common Language Runtime \(CLR\) en a besoin.  
  
> [!NOTE]
>  Votre application devra s'exécuter avec une confiance totale pour utiliser cette procédure.  
  
## Composants requis  
 Vous aurez besoin d'un des composants suivants pour exécuter cette procédure pas à pas :  
  
-   Kit de développement logiciel Windows.  Le Kit de développement logiciel \(SDK\) Windows peut être téléchargé à partir du Centre de téléchargement Microsoft.  
  
-   Visual Studio.  
  
## Création du projet  
  
#### Pour créer un projet qui utilise un assembly à la demande  
  
1.  Créez un répertoire nommé ClickOnceOnDemand.  
  
2.  Ouvrez l'invite de commandes du Kit de développement Windows SDK ou l'invite de commandes [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Accédez au répertoire ClickOnceOnDemand.  
  
4.  Générez une paire de clés publique\/privée à l'aide de la commande suivante :  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  À l'aide du Bloc\-notes ou d'un autre éditeur de texte, définissez une classe nommée `DynamicClass` avec une seule propriété appelée `Message`.  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-cs[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  Enregistrez le texte en tant que fichier nommé `ClickOnceLibrary.cs` ou `ClickOnceLibrary.vb`, selon le langage vous utilisez, dans le répertoire ClickOnceOnDemand.  
  
7.  Compilez le fichier dans un assembly.  
  
    ```c#  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb#  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  Pour obtenir le jeton de clé publique de l'assembly, utilisez la commande suivante :  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Créez un fichier à l'aide de votre éditeur de texte et entrez le code suivant.  Ce code crée une application Windows Forms qui télécharge l'assembly ClickOnceLibrary lorsqu'il est requis.  
  
     [!code-cs[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. Dans le code, localisez l'appel à <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Affectez à `PublicKeyToken` la valeur que vous avez récupérée précédemment.  
  
12. Enregistrez le fichier en tant que `Form1.cs` ou `Form1.vb`.  
  
13. Compilez\-le dans un fichier exécutable à l'aide de la commande suivante.  
  
    ```c#  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb#  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## Marquage d'assemblys comme étant facultatifs  
  
#### Pour marquer des assemblys comme étant facultatifs dans votre application ClickOnce à l'aide de MageUI.exe  
  
1.  À l'aide de MageUI.exe, créez un manifeste d'application comme décrit dans [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Utilisez les paramètres suivants pour le manifeste d'application :  
  
    -   Nommez le manifeste d'application `ClickOnceOnDemand`.  
  
    -   Dans la page **Fichiers**, sur la ligne ClickOnceLibrary.dll, affectez à la colonne **Type de fichier** la valeur **Aucun**.  
  
    -   Dans la page **Fichiers**, sur la ligne ClickOnceLibrary.dll, tapez `ClickOnceLibrary.dll` dans la colonne **Groupe**.  
  
2.  À l'aide de MageUI.exe, créez un manifeste de déploiement comme décrit dans [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Utilisez les paramètres suivants pour le manifeste de déploiement :  
  
    -   Nommez le manifeste de déploiement `ClickOnceOnDemand`.  
  
## Test du nouvel assembly  
  
#### Pour tester votre assembly à la demande  
  
1.  Téléchargez votre déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sur un serveur Web.  
  
2.  Lancez votre application déployée avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à partir d'un navigateur Web en entrant l'URL du manifeste de déploiement.  Si vous appelez votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `ClickOnceOnDemand` et si vous la téléchargez dans le répertoire racine de adatum.com, votre URL se présente comme suit :  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Lorsque votre formulaire principal apparaît, appuyez sur <xref:System.Windows.Forms.Button>.  Vous devez voir la chaîne "Hello World\!" dans une fenêtre de message.  
  
## Voir aussi  
 <xref:System.Deployment.Application.ApplicationDeployment>