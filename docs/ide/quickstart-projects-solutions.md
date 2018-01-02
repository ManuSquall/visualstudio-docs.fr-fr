---
title: "Présentation des projets et solutions dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 12/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f3b30b796ca389d5adfc4f8ece3c8f774626e994
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2017
---
# <a name="quickstart-projects-and-solutions"></a>Démarrage rapide : Projets et solutions

Dans ce guide de démarrage rapide de 10 minutes, nous allons explorer le processus de création d’une solution et d’un projet dans Visual Studio. Nous allons examiner les propriétés d’un projet et certains des fichiers associés. Nous allons aussi créer une référence à un deuxième projet.

> [!TIP]
> Dans ce guide de démarrage rapide, nous allons créer une solution et un projet de toutes pièces pour vous aider à bien comprendre le concept de projet. En règle générale, quand vous créez un projet dans Visual Studio, il vous suffit le plus souvent d’utiliser l’un des nombreux modèles de projet que Visual Studio propose.

> [!NOTE]
> Le développement d’applications dans Visual Studio peut se faire sans solutions ni projets. Vous pouvez aussi simplement ouvrir un dossier qui contient du code et commencer à écrire du code, générer des builds et déboguer le code. Par exemple, si vous clonez un dépôt GitHub, il est possible qu’il ne contienne pas de solutions et projets Visual Studio. Pour plus d’informations, consultez [Développer du code dans Visual Studio sans projets ni solutions](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions"></a>Solutions

Les solutions sont des conteneurs dans lesquels Visual Studio organise un ou plusieurs projets associés. Quand vous ouvrez une solution dans Visual Studio, tous les projets qu’elle contient sont automatiquement chargés.

### <a name="create-a-solution"></a>Créer une solution

Nous allons commencer notre exploration en créant une solution vide. Une fois que vous connaîtrez mieux Visual Studio, vous n’aurez sans doute pas souvent besoin de créer des solutions vides. Quand vous créez un projet dans Visual Studio, une solution est automatiquement créée pour héberger le projet (s’il n’y a pas d’autre solution déjà ouverte).

1. Démarrez Visual Studio.

   Visual Studio s’ouvre, avec probablement la **page de démarrage** qui occupe la plus grande partie de l’espace de la fenêtre.

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet...**.

   La boîte de dialogue **Nouveau projet** s'affiche.

1. Dans le volet gauche, développez **Autres types de projets**, puis choisissez **Solutions Visual Studio**. Dans le volet central, choisissez **Solution vide**. Nommez votre solution « QuickSolution », puis choisissez **OK**.

   ![Modèle de solution vide](media/quickstart-projects-new-solution.png)

   La **page de démarrage** se ferme et une solution s’affiche dans **l’Explorateur de solutions** sur le côté droit de la fenêtre Visual Studio. **L’Explorateur de solutions** vous sera sans doute souvent utile pour parcourir le contenu de vos projets.

### <a name="add-a-project"></a>Ajouter un projet

Nous allons maintenant ajouter notre premier projet à la solution. Nous allons démarrer avec un projet vide et y ajouter les éléments nécessaires.

1. Dans le menu contextuel (clic droit) de **Solution 'QuickSolution'** dans **l’Explorateur de solutions**, choisissez **Ajouter** > **Nouveau projet...**.

   La boîte de dialogue **Ajouter un nouveau projet** s'ouvre.

1. Dans le volet gauche, développez **Visual C#** et choisissez **Bureau Windows Classic**. Ensuite, dans le volet central, choisissez **Projet vide (.NET Framework)**. Nommez le projet « QuickDate », puis choisissez le bouton **OK**.

   Un projet nommé « QuickDate » s’affiche en dessous de la solution dans **l’Explorateur de solutions**. Il contient un seul fichier appelé **App.config**.

   > [!NOTE]
   > Si vous ne voyez pas **Visual C#** dans le volet gauche de la boîte de dialogue, vous devez installer la charge de travail **Développement .NET Desktop**. Pour l’installer rapidement, cliquez sur le lien **Ouvrir Visual Studio Installer** situé en bas de ce volet gauche. Dans la fenêtre **Visual Studio Installer** qui s’ouvre, choisissez la charge de travail appropriée, puis choisissez le bouton **Modifier**.

   ![Lien Ouvrir Visual Studio Installer](media/quickstart-projects-open-installer.png)

## <a name="add-an-item-to-the-project"></a>Ajouter un élément au projet

Nous avons un projet vide &mdash; nous allons y ajouter un fichier de code.

1. Dans le menu contextuel (clic droit) de **QuickDate** dans **l’Explorateur de solutions**, choisissez **Ajouter** > **Nouvel élément...**.

   La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

1. Développez **Éléments Visual C#**, puis choisissez **Code**. Dans le volet central, choisissez **Classe**. Nommez la classe « Calendar », puis choisissez le bouton **Ajouter**.

   Un fichier nommé « Calendar.cs » est ajouté au projet. **.cs** est l’extension de fichier attribuée aux fichiers de code C#. Le fichier s’affiche dans la hiérarchie de projets Visual dans **l’Explorateur de solutions**, et son contenu est ouvert dans l’éditeur.

1. Remplacez le contenu du fichier **Calendar.cs** par le code ci-dessous.

   ```csharp
   using System;

   namespace QuickDate
   {
       internal class Calendar
       {
           static void Main(string[] args)
           {
               DateTime now = GetCurrentDate();
               Console.WriteLine($"Today's date is {now}");
               Console.ReadLine();
           }

           internal static DateTime GetCurrentDate()
           {
               return DateTime.Now.Date;
           }
       }
   }
   ```

   Vous n’avez pas besoin de comprendre ce que fait le code, mais si vous le souhaitez, vous pouvez exécuter le programme pour observer qu’il affiche la date du jour dans la fenêtre de console.

## <a name="add-a-second-project"></a>Ajouter un deuxième projet

Les solutions contiennent souvent plusieurs projets, qui se référencent mutuellement. Les différents projets d’une solution peuvent être des bibliothèques de classes, des applications exécutables, des projets de test unitaire ou des sites web.

Nous allons ajouter un projet de test unitaire à notre solution. Cette fois, nous allons démarrer avec un modèle de projet. Nous n’avons donc pas à ajouter un fichier de code supplémentaire au projet.

1. Dans le menu contextuel (clic droit) de **Solution 'QuickSolution'** dans **l’Explorateur de solutions**, choisissez **Ajouter** > **Nouveau projet...**.

   La boîte de dialogue **Ajouter un nouveau projet** s'ouvre.

1. Dans le volet gauche, développez **Visual Basic** et choisissez la catégorie **Test**. Dans le volet central, choisissez **Projet de test unitaire (.NET Framework)**. Nommez le projet « QuickTest », puis choisissez le bouton **OK**.

   Un deuxième projet est ajouté à **l’Explorateur de solutions** et un fichier nommé **UnitTest1.vb** s’ouvre dans l’éditeur. **.vb** est l’extension de fichier attribuée aux fichiers de code Visual Basic.

   ![Explorateur de solutions avec deux projets](media/quickstart-projects-solution-explorer.png)

## <a name="add-a-project-reference"></a>Ajouter une référence au projet

Nous allons utiliser le nouveau projet de test unitaire pour tester notre méthode dans le projet **QuickDate**. Nous devons donc ajouter une référence à ce projet. Cette opération crée une dépendance de build entre les deux projets, ce qui signifie que **QuickDate** sera généré avant **QuickTest** au moment de la génération de la solution.

1. Choisissez le nœud **Références** dans le projet **QuickTest** et, dans le menu contextuel (clic droit), choisissez **Ajouter une référence...**.

   ![Menu Ajouter une référence](media/quickstart-projects-add-reference.png)

   La boîte de dialogue **Gestionnaire de références** s’ouvre.

1. Dans le volet gauche, développez **Projets** et choisissez **Solution**. Dans le volet central, cochez la case à côté de **QuickDate**, puis choisissez le bouton **OK**.

   Une référence au projet **QuickDate** est ajoutée.

## <a name="add-test-code"></a>Ajouter le code de test

1. Nous allons maintenant ajouter le code de test dans le fichier de code Visual Basic. Remplacez le contenu du fichier **UnitTest1.vb** par le code suivant.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Vous voyez qu’une ligne ondulée rouge s’affiche sous une partie du code. Pour résoudre cette erreur, nous devons référencer le projet de test comme [assembly friend](/dotnet/csharp/programming-guide/concepts/assemblies-gac/friend-assemblies) dans le projet **QuickDate**.

1. Retournez dans le projet **QuickDate**, ouvrez le fichier **Calendar.cs** s’il n’est pas déjà ouvert, puis ajoutez l’instruction using et l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> suivants pour résoudre l’erreur dans le projet de test.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Le fichier de code doit ressembler à ceci.

   ![Code CSharp](media/quickstart-projects-cs-code.png)

## <a name="project-properties"></a>Propriétés de projet

Dans le fichier de code C#, la ligne qui contient l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> fait référence au nom de l’assembly dans le projet **QuickTest**. Le nom de l’assembly n’est pas toujours identique au nom du projet. Pour connaître le nom de l’assembly d’un projet, ouvrez les propriétés du projet.

1. Dans **l’Explorateur de solutions**, sélectionnez le projet **QuickTest**. Dans le menu contextuel (clic droit), sélectionnez **Propriétés**, ou appuyez simplement sur **Alt**+**Entrée**.

   Les pages de propriétés du projet s’ouvrent sous l’onglet **Application**. Notez que le nom de l’assembly du projet **QuickTest** est bien « QuickTest ». Vous pouvez le modifier à cet endroit si vous le souhaitez. Quand vous générerez le projet de test, le nom du fichier exécutable obtenu aura le nouveau nom choisi à la place de **QuickTest.exe**.

   ![Propriétés de projet](media/quickstart-projects-properties.png)

1. Explorez les autres onglets des pages de propriétés du projet, tels que les onglets **Compiler** et **Paramètres**. Ces onglets diffèrent selon le type de projet.

## <a name="next-steps"></a>Étapes suivantes

Si vous souhaitez vérifier que votre test unitaire fonctionne correctement, choisissez **Test** > **Exécuter** > **Tous les tests** dans la barre de menus. Une fenêtre intitulée **Explorateur de tests** s’ouvre. Vérifiez que le résultat du test **TestGetCurrentDate** est correct.

Félicitations ! Vous avez terminé ce guide de démarrage rapide. Vous pouvez suivre d’autres guides de démarrage rapide pour Visual Studio ou en découvrir davantage sur la [création de projets et solutions](../ide/creating-solutions-and-projects.md).

## <a name="see-also"></a>Voir aussi

[Démarrage rapide : premier aperçu de l’IDE Visual Studio](../ide/quickstart-ide-orientation.md)  
[Démarrage rapide : Personnaliser l’éditeur et l’IDE de Visual Studio](../ide/quickstart-personalize-the-ide.md)  
[Démarrage rapide : Codage dans l’éditeur](../ide/quickstart-editor.md)  
[Gestion des propriétés des projets et des solutions](../ide/managing-project-and-solution-properties.md)  
[Gestion des références dans un projet](../ide/managing-references-in-a-project.md)  
[Développer du code dans Visual Studio sans projets ni solutions](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)  
[Vue d’ensemble de l’IDE de Visual Studio](../ide/visual-studio-ide.md)
