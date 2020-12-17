---
title: Présentation des projets et solutions
description: Découvrez la différence entre les projets et les solutions et comment les utiliser dans Visual Studio.
ms.date: 11/17/2020
ms.technology: vs-ide-general
ms.custom:
- get-started
- SEO-VS-2020
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48fb0f1c22b2f7055005640baff2239a0ad4a32a
ms.sourcegitcommit: fed8782b2fb2ca18a90746b6e7e0b33f3fde10f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97646409"
---
# <a name="learn-about-projects-and-solutions"></a>Découvrir les projets et les solutions

Dans cet article d’introduction, nous allons explorer le processus de création d’une *solution* et d’un *projet* dans Visual Studio. Une solution est un conteneur servant à organiser un ou plusieurs projets de code associés, par exemple un projet de bibliothèque de classes et un projet de test correspondant. Nous allons examiner les propriétés d’un projet et certains des fichiers associés. Nous allons également créer une référence d’un projet vers un autre.

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

Nous allons créer une solution et un projet de toutes pièces pour vous aider à bien comprendre le concept de projet. En règle générale, quand vous créez un projet dans Visual Studio, il vous suffit le plus souvent d’utiliser certains des différents *modèles* de projet proposés par Visual Studio.

> [!NOTE]
> Le développement d’applications dans Visual Studio peut se faire sans solutions ni projets. Vous pouvez aussi simplement ouvrir un dossier qui contient du code et commencer à écrire du code, générer des builds et déboguer le code. Par exemple, si vous clonez un dépôt [GitHub](https://github.com/), il est possible qu’il ne contienne pas de solutions et projets Visual Studio. Pour plus d’informations, consultez [Développer du code dans Visual Studio sans projets ni solutions](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Solutions et projets

Malgré son nom, une solution n’est pas une « réponse ». Il s’agit simplement d’un conteneur dans lequel Visual Studio organise un ou plusieurs projets associés. Quand vous ouvrez une solution dans Visual Studio, tous les projets que contient la solution sont chargés automatiquement.

### <a name="create-a-solution"></a>Créer une solution

Nous allons commencer notre exploration en créant une solution vide. Une fois que vous connaîtrez mieux Visual Studio, vous n’aurez sans doute pas souvent besoin de créer des solutions vides. Quand vous créez un projet, Visual Studio crée automatiquement une solution pour héberger le projet (s’il n’y a pas d’autre solution déjà ouverte).

::: moniker range="vs-2017"

1. Ouvrez Visual Studio.

1. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

   La boîte de dialogue **Nouveau projet** s’affiche.

1. Dans le volet gauche, développez **Autres types de projets**, puis choisissez **Solutions Visual Studio**. Dans le volet central, choisissez le modèle **Solution vide**. Nommez votre solution **QuickSolution**, puis choisissez le bouton **OK**.

   ![Modèle de solution vide dans Visual Studio 2017](media/tutorial-projects-new-solution.png "Modèle de solution vide dans Visual Studio 2017.")

   La **page de démarrage** se ferme et une solution s’affiche dans l’**Explorateur de solutions** sur le côté droit de la fenêtre Visual Studio. **L’Explorateur de solutions** vous sera sans doute souvent utile pour parcourir le contenu de vos projets.

::: moniker-end

::: moniker range=">=vs-2019"

1. Ouvrez Visual Studio.

2. Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

3. Sur la page **Créer un projet**, entrez **nouvelle solution** dans la zone de recherche, sélectionnez le modèle **Nouvelle solution**, puis choisissez **Suivant**.

   ![Modèle de solution vide dans Visual Studio 2019](media/vs-2019/tutorial-projects-blank-solution-template.png "Modèle de solution vide dans Visual Studio 2019.")

    > [!TIP]
    > Si vous avez plusieurs charges de travail installées, le modèle de **solution vide** peut ne pas apparaître en haut de la liste des résultats de la recherche. Essayez de faire défiler vers les **autres résultats en fonction de votre** section de recherche de la liste. Il doit y figurer.

4. Nommez la solution **QuickSolution**, puis choisissez **Créer**.

   Une solution s’affiche dans l’**Explorateur de solutions** sur le côté droit de la fenêtre Visual Studio. **L’Explorateur de solutions** vous sera sans doute souvent utile pour parcourir le contenu de vos projets.

::: moniker-end

### <a name="add-a-project"></a>Ajouter un projet

Nous allons maintenant ajouter notre premier projet à la solution. Nous allons démarrer avec un projet vide et y ajouter les éléments nécessaires.

::: moniker range="vs-2017"

1. Dans le menu contextuel (clic droit) de **Solution 'QuickSolution'** dans l’**Explorateur de solutions**, choisissez **Ajouter** > **Nouveau projet**.

   La boîte de dialogue **Ajouter un nouveau projet** s'ouvre.

1. Dans le volet gauche, développez **Visual C#**, puis choisissez **Bureau Windows**. Ensuite, dans le volet central, choisissez le modèle **Projet vide (.NET Framework)**. Nommez le projet **QuickDate**, puis choisissez **OK**.

   Un projet nommé QuickDate s’affiche en dessous de la solution dans l’**Explorateur de solutions**. Il contient un seul fichier appelé *App.config*.

   > [!NOTE]
   > Si vous ne voyez pas **Visual C#** dans le volet gauche de la boîte de dialogue, vous devez installer la charge de travail Visual Studio pour le **développement .net Desktop** . Visual Studio utilise une installation basée sur la charge de travail pour installer uniquement les composants dont vous avez besoin pour le type de développement que vous effectuez. Pour installer une nouvelle charge de travail, un moyen simple consiste à choisir le lien **Ouvrir Visual Studio Installer** en bas à gauche de la boîte de dialogue **Ajouter un nouveau projet**. Une fois Visual Studio Installer lancé, choisissez la charge de travail **Développement .NET Desktop**, puis cliquez sur le bouton **Modifier**.
   >
   > ![Lien Ouvrir Visual Studio Installer](media/tutorial-projects-open-installer.png "Le lien ouvrir le Visual Studio Installer dans la boîte de dialogue Ajouter un nouveau projet dans Visual Studio 2017.")

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans le menu contextuel (clic droit) de **Solution 'QuickSolution'** dans l’**Explorateur de solutions**, choisissez **Ajouter** > **Nouveau projet**.

   Une boîte de dialogue s’ouvre en indiquant **Ajouter un nouveau projet**.

1. Dans la zone de recherche située tout en haut, entrez le texte **vide**, puis sélectionnez **C#** sous **Langage**.

1. Sélectionnez le modèle **Projet vide (.NET Framework)**, puis choisissez **Suivant**.

1. Nommez le projet **QuickDate**, puis choisissez **Créer**.

   Un projet nommé QuickDate s’affiche en dessous de la solution dans l’**Explorateur de solutions**. Il contient un seul fichier appelé *App.config*.

   > [!NOTE]
   > Si vous ne voyez pas le modèle **projet vide (.NET Framework)** , vous devez installer la charge de travail Visual Studio pour le **développement .net Desktop** . Visual Studio utilise une installation basée sur la charge de travail pour installer uniquement les composants dont vous avez besoin pour le type de développement que vous effectuez.
   >
   >Pour installer une nouvelle charge de travail quand vous créez un projet, il vous suffit simplement de choisir le lien **Installer plus d’outils et de fonctionnalités** sous le texte indiquant **Vous n’arrivez pas à trouver ce que vous cherchez ?**. Une fois Visual Studio Installer lancé, choisissez la charge de travail **Développement .NET Desktop**, puis cliquez sur le bouton **Modifier**.
   >
   > ![Lien Ouvrir Visual Studio Installer](media/vs-2019/tutorial-projects-open-installer.png "Le lien ouvrir le Visual Studio Installer dans la boîte de dialogue créer un nouveau projet dans Visual Studio.")

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Ajouter un élément au projet

Nous avons un projet vide. Ajoutons un fichier de code.

1. Dans le menu contextuel (clic droit) du projet **QuickDate** dans l’**Explorateur de solutions**, choisissez **Ajouter** > **Nouvel élément**.

   La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

1. Développez **Éléments Visual C#**, puis choisissez **Code**. Dans le volet central, choisissez le modèle d’élément de **classe** . Nommez la classe **Calendar**, puis choisissez le bouton **Ajouter**.

   Un fichier nommé *Calendar.cs* est ajouté au projet. *.cs* est l’extension de fichier attribuée aux fichiers de code C#. Le fichier s’affiche dans la hiérarchie de projets Visual dans **l’Explorateur de solutions**, et son contenu est ouvert dans l’éditeur.

1. Remplacez le contenu du fichier *Calendar.cs* par le code ci-dessous :

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

   Vous n’avez pas besoin de comprendre ce que fait le code, mais si vous le souhaitez, vous pouvez exécuter le programme en appuyant sur **CTRL** + **F5** et voir qu’il affiche la date du jour dans la fenêtre de la console (ou sortie standard).

## <a name="add-a-second-project"></a>Ajouter un deuxième projet

Les solutions contiennent souvent plusieurs projets, qui se référencent mutuellement. Les différents projets d’une solution peuvent être des bibliothèques de classes, des applications exécutables, des projets de test unitaire ou des sites web.

Nous allons ajouter un projet de test unitaire à notre solution. Cette fois, nous allons démarrer avec un modèle de projet. Nous n’avons donc pas à ajouter un fichier de code supplémentaire au projet.

1. Dans le menu contextuel (clic droit) de **Solution 'QuickSolution'** dans l’**Explorateur de solutions**, choisissez **Ajouter** > **Nouveau projet**.

::: moniker range="vs-2017"

2. Dans le volet gauche, développez **Visual C#** et choisissez la catégorie **Test**. Dans le volet central, choisissez le modèle de projet **Projet de test MSTest (.NET Core)**. Nommez le projet **QuickTest**, puis choisissez **OK**.

   Un deuxième projet est ajouté à **l’Explorateur de solutions** et un fichier nommé *UnitTest1.cs* s’ouvre dans l’éditeur.

   ![Explorateur de solutions de Visual Studio avec deux projets](media/tutorial-projects-solution-explorer.png "Explorateur de solutions avec deux projets dans Visual Studio 2017.")

::: moniker-end

::: moniker range=">=vs-2019"

2. Dans la boîte de dialogue **Ajouter un nouveau projet**, dans la zone de recherche située tout en haut, entrez le texte **test unitaire**, puis sélectionnez **C#** sous **Langage**.

3. Choisissez le modèle de projet **Projet de test MSTest (.NET Core)**, puis **Suivant**.

4. Nommez le projet **QuickTest**, puis choisissez **Créer**.

   Un deuxième projet est ajouté à **l’Explorateur de solutions** et un fichier nommé *UnitTest1.cs* s’ouvre dans l’éditeur.

   ![Explorateur de solutions de Visual Studio avec deux projets](media/vs-2019/tutorial-projects-solution-explorer.png "Explorateur de solutions avec deux projets dans Visual Studio.")

::: moniker-end

## <a name="add-a-project-reference"></a>Ajouter une référence au projet

Nous allons utiliser le nouveau projet de test unitaire pour tester notre méthode dans le projet **QuickDate**. Nous devons donc ajouter une référence à ce projet. Cette opération crée une *dépendance de build* entre les deux projets, ce qui signifie que quand vous générez la solution, **QuickDate** est généré avant **QuickTest**.

::: moniker range="vs-2017"

1. Choisissez le nœud **Dépendances** dans le projet **QuickTest**, puis dans le menu contextuel (clic droit), choisissez **Ajouter une référence**.

   La boîte de dialogue **Gestionnaire de références** s’ouvre.

1. Dans le volet gauche, développez **Projets** et choisissez **Solution**. Dans le volet central, activez la case à cocher en regard de **QuickDate**, puis choisissez **OK**.

   Une référence au projet **QuickDate** est ajoutée.

   ![Explorateur de solutions Visual Studio 2019 montrant la référence de projet](media/vs-2019/tutorial-projects-solution-explorer-reference.png "Explorateur de solutions présentant une référence de projet dans Visual Studio.")

::: moniker-end

::: moniker range="vs-2019"

1. Choisissez le nœud **dépendances** dans le projet **QuickTest** , puis, dans le menu contextuel, cliquez avec le bouton droit, puis choisissez Ajouter une **référence de projet...**.

   La boîte de dialogue **Gestionnaire de références** s’ouvre.

1. Dans le volet gauche, développez **Projets** et choisissez **Solution**. Dans le volet central, activez la case à cocher en regard de **QuickDate**, puis choisissez **OK**.

   Une référence au projet **QuickDate** est ajoutée.

   ![Explorateur de solutions Visual Studio 2019 montrant la référence de projet](media/vs-2019/tutorial-projects-solution-explorer-reference.png)
   
::: moniker-end

## <a name="add-test-code"></a>Ajouter le code de test

1. Nous allons maintenant ajouter le code de test dans le fichier de code de test C#. Remplacez le contenu du fichier *UnitTest1.cs* par le code suivant :

   ```csharp
   using System;
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace QuickTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestGetCurrentDate()
           {
               Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate());
           }
       }
   }
   ```

   Vous voyez une ligne ondulée rouge s’afficher sous une partie du code. Pour résoudre cette erreur, nous devons référencer le projet de test comme [assembly friend](/dotnet/standard/assembly/friend-assemblies) dans le projet **QuickDate**.

1. De retour dans le projet **QuickDate**, ouvrez le fichier *Calendar.cs*, s’il ne l’est pas déjà. Ajoutez l’[instruction using](/dotnet/csharp/language-reference/keywords/using-statement) et l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> suivants en haut du fichier pour résoudre l’erreur dans le projet de test.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Le fichier de code doit ressembler à ceci :

   ![Code CSharp](media/tutorial-projects-cs-code.png "Extrait de code de la section ajouter le code de test de cet article.")

## <a name="project-properties"></a>Propriétés d’un projet

Dans le fichier *Calendar.cs*, la ligne qui contient l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> référence le nom de l’assembly (nom de fichier) du projet **QuickTest**. Le nom de l’assembly n’est pas toujours identique au nom du projet. Pour connaître le nom de l’assembly d’un projet, ouvrez les propriétés du projet.

1. Dans **l’Explorateur de solutions**, sélectionnez le projet **QuickTest**. Dans le menu contextuel (clic droit), sélectionnez **Propriétés**, ou appuyez simplement sur **Alt**+**Entrée**.

   Les *pages de propriétés* du projet sont ouvertes sous l’onglet **application** . Les pages de propriétés contiennent différents paramètres pour le projet. Notez que le nom de l’assembly du projet **QuickTest** est bien « QuickTest ». Vous pouvez le changer à cet endroit si vous le souhaitez. Quand vous générez le projet de test, le nom du fichier binaire obtenu a le nouveau nom choisi à la place de *QuickTest.dll*.

   ![Propriétés d’un projet](media/tutorial-projects-netcore-properties.png "Boîte de dialogue Propriétés du projet dans Visual Studio.")

1. Explorez d’autres onglets des pages de propriétés du projet, par exemple **Générer** et **Déboguer**. Ces onglets sont différents pour différents types de projets.

## <a name="next-steps"></a>Étapes suivantes

Si vous souhaitez vérifier que votre test unitaire fonctionne, choisissez **tester**  >  **exécuter**  >  **tous les tests** dans la barre de menus. Une fenêtre intitulée **Explorateur de tests** s’ouvre. Vérifiez que le résultat du test **TestGetCurrentDate** est correct.

![Explorateur de tests dans Visual Studio affichant le test réussi](media/tutorial-projects-test-explorer.png "Explorateur de tests dans Visual Studio présentant un test réussi.")

::: moniker range="vs-2017"

> [!TIP]
> Si **l’Explorateur de tests** ne s’ouvre pas automatiquement, ouvrez-le en choisissant **Tester** > **Windows** > **Explorateur de tests** dans la barre de menus.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Si l' **Explorateur de tests** ne s’ouvre pas automatiquement, ouvrez-le en sélectionnant **tester**  >  l’Explorateur de **tests** dans la barre de menus.

::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Créer des projets et des solutions](../ide/creating-solutions-and-projects.md)
- [Gérer les propriétés des projets et des solutions](../ide/managing-project-and-solution-properties.md)
- [Gérer les références dans un projet](../ide/managing-references-in-a-project.md)
- [Développer du code dans Visual Studio sans projets ni solutions](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Vue d’ensemble de l’IDE de Visual Studio](../get-started/visual-studio-ide.md)
