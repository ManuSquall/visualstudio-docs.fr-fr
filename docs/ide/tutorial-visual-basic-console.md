---
title: Bien démarrer avec Visual Basic dans Visual Studio
ms.custom: ''
ms.date: 12/08/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 228ebc2fd2137b78b44347fa2e03d7ba949a23c7
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764931"
---
# <a name="get-started-with-visual-basic-in-visual-studio"></a>Bien démarrer avec Visual Basic dans Visual Studio

Dans ce tutoriel pour Visual Basic (VB), vous allez utiliser Visual Studio pour créer et exécuter différentes applications console tout en explorant certaines fonctionnalités de [l’environnement de développement intégré (IDE) de Visual Studio](visual-studio-ide.md).

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

## <a name="before-you-begin"></a>Avant de commencer

Voici un petit forum aux questions qui présente quelques concepts clés.

### <a name="what-is-visual-basic"></a>Qu’est-ce que Visual Basic ?

Visual Basic est un langage de programmation de type sécurisé conçu pour être facile à apprendre. Il est dérivé du langage BASIC, qui signifie « Beginner’s All-purpose Symbolic Instruction Code ».

### <a name="what-is-visual-studio"></a>Qu’est-ce que Visual Studio ?

Visual Studio est une suite de développement intégrée d’outils de productivité pour les développeurs. Il s’agit d’un programme qui sert à créer des applications et des programmes.

### <a name="what-is-a-console-app"></a>Qu’est-ce qu’une application console ?

Une application console prend une entrée et affiche la sortie dans une fenêtre de ligne de commande, également appelée console.

### <a name="what-is-net-core"></a>Qu'est-ce que le .NET Core ?

.NET Core est la suite logique du .NET Framework. Là où le .NET Framework vous permettait de partager du code entre les langages de programmation, .NET Core ajoute la capacité à partager du code entre des plateformes. De plus, il est open source. (Le .NET Framework et .NET Core incluent des bibliothèques de fonctionnalités prégénérées ainsi qu’un CLR (Common Language Runtime) qui agit comme une machine virtuelle dans laquelle exécuter votre code.)

## <a name="start-developing"></a>Commencer à développer

Prêt à commencer à développer ? C’est parti.

### <a name="create-a-project"></a>Créer un projet

Tout d’abord, nous allons créer un projet d’application Visual Basic. Le type de projet inclut tous les fichiers de modèle dont vous aurez besoin au départ.

1. Ouvrez Visual Studio 2017.

2. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

3. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **Visual Basic**, puis choisissez **.NET Core**. Dans le volet central, choisissez **Application console (.NET Core)**. Ensuite, nommez le fichier *HelloWorld*.  

   ![Modèle de projet d’application console (.NET Core) dans la boîte de dialogue Nouveau projet dans l’IDE de Visual Studio](../ide/media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

#### <a name="add-a-workgroup-optional"></a>Ajouter un groupe de travail (facultatif)

Si vous ne voyez pas le modèle de projet **Application console (.NET Core)**, vous pouvez l’obtenir en ajoutant la charge de travail **Développement multiplateforme .NET Core**. Vous pouvez ajouter cette charge de travail de l’une des deux manières suivantes, en fonction des mises à jour de Visual Studio 2017 qui sont installées sur votre ordinateur.

##### <a name="option-1-use-the-new-project-dialog-box"></a>Option 1 : Utiliser la boîte de dialogue Nouveau projet

1. Cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**.

  ![Cliquer sur le lien Ouvrir Visual Studio Installer dans la boîte de dialogue Nouveau projet](../ide/media/vs-open-visual-studio-installer-generic.png)

2. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement multiplateforme .NET Core**, puis choisissez **Modifier**.

   ![Charge de travail Développement multiplateforme .Net Core dans Visual Studio Installer](../ide/media/dot-net-core-xplat-dev-workload.png)

##### <a name="option-2-use-the-tools-menu-bar"></a>Option 2 : Utiliser la barre de menus Outils

1. Quittez la boîte de dialogue **Nouveau projet** puis, dans la barre de menus supérieure, choisissez **Outils** > **Obtenir les outils et fonctionnalités**.

2. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement multiplateforme .NET Core**, puis choisissez **Modifier**.

## <a name="create-a-what-is-your-name-application"></a>Créer une application « Quel est votre nom »

Nous allons créer une application qui vous demande votre nom et l’affiche, ainsi que la date et l’heure. Voici comment :

1. S’il n’est pas déjà ouvert, ouvrez votre projet *WhatIsYourName*.

2. Entrez le code Visual Basic suivant juste après le crochet ouvrant qui suit la ligne `Sub Main(args As String())` et avant la ligne `End Sub` :

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Ce code remplace les instructions <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> et <xref:System.Console.ReadKey%2A> existantes.

 ![Fenêtre de code affichant le code « Quel est votre nom »](../ide/media/vb-codewindow-what-name.png)

3. Quand la fenêtre de console s’ouvre, entrez votre nom. La fenêtre de console doit ressembler à la capture d’écran suivante :

   ![Fenêtre de console qui affiche What Is Your Name, la date et l’heure, et le message Press any key to continue](../ide/media/vb-console-what-name.png)

5. Appuyez sur une touche pour fermer la fenêtre de console.

## <a name="create-a-calculate-this-application"></a>Créer une application « Calculer ceci »

1. Ouvrez Visual Studio 2017 puis, dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

2. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **Visual Basic**, puis choisissez **.NET Core**. Dans le volet central, choisissez **Application console (.NET Core)**. Ensuite, nommez le fichier *CalculateThis*.  

3. Entrez le code suivant entre les lignes `Module Program` et `End Module` :

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

  La fenêtre de code doit ressembler à la capture d’écran suivante :

   ![Fenêtre de code montrant le code Calculer ceci](../ide/media/vb-codewindow-calculate-this.png)

4. Cliquez sur **CalculateThis** pour exécuter votre programme. La fenêtre de console doit ressembler à la capture d’écran suivante :       

    ![Fenêtre de console montrant l’application CalculateThis, qui comprend des invites sur les actions à effectuer.](../ide/media/vb-console-calculate-this.png)

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé ce didacticiel. Pour en savoir plus sur Visual Basic et l’IDE Visual Studio, consultez les pages suivantes.

* [Guide Visual Basic](/dotnet/visual-basic/index)
* [Nouveautés de Visual Basic](/dotnet/visual-basic/getting-started/whats-new)
* [IntelliSense pour les fichiers de code Visual Basic](visual-basic-specific-intellisense.md)
* [Références du langage Visual Basic](/dotnet/visual-basic/language-reference/index)
* Cours vidéo [Concepts de base de Visual Basic pour les débutants](https://mva.microsoft.com/en-us/training-courses/visual-basic-fundamentals-for-absolute-beginners-16507)
