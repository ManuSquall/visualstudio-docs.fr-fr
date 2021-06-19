---
title: Tutoriel – Projets et solutions Visual Basic
description: Découvrez comment créer une solution et un projet dans Visual Studio en tant que développeur Visual Basic.
ms.date: 12/12/2018
ms.technology: vs-ide-general
ms.custom:
- vs-acquisition
- get-started
- SEO-VS-2020
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 813a6ce10b0c5bcc385ac72ba6fdf99495c457ee
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384731"
---
# <a name="learn-about-projects-and-solutions-using-visual-basic"></a>Découvrir les projets et les solutions avec Visual Basic

Dans cet article d’introduction, nous allons explorer le processus de création d’une *solution* et d’un *projet* dans Visual Studio. Une solution est un conteneur servant à organiser un ou plusieurs projets de code associés, par exemple un projet de bibliothèque de classes et un projet de test correspondant. Nous allons examiner les propriétés d’un projet et certains des fichiers associés. Nous allons également créer une référence d’un projet vers un autre.

::: moniker range="vs-2017"

> [!TIP]
> Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2022"

> [!TIP]
> Si vous n’avez pas encore installé Visual Studio Preview, accédez à la page [téléchargements Visual studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) pour l’installer gratuitement.

::: moniker-end

Nous allons créer une solution et un projet de toutes pièces pour vous aider à bien comprendre le concept de projet. En règle générale, quand vous créez un projet dans Visual Studio, il vous suffit le plus souvent d’utiliser certains des différents *modèles* de projet proposés par Visual Studio.

> [!NOTE]
> Le développement d’applications dans Visual Studio peut se faire sans solutions ni projets. Vous pouvez aussi simplement ouvrir un dossier qui contient du code et commencer à écrire du code, générer des builds et déboguer le code. Par exemple, si vous clonez un dépôt [GitHub](https://github.com/), il est possible qu’il ne contienne pas de solutions et projets Visual Studio. Pour plus d’informations, consultez [Développer du code dans Visual Studio sans projets ni solutions](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Solutions et projets

Malgré son nom, une solution n’est pas une « réponse ». Il s’agit simplement d’un conteneur dans lequel Visual Studio organise un ou plusieurs projets associés. Quand vous ouvrez une solution dans Visual Studio, tous les projets que contient la solution sont chargés automatiquement.

### <a name="create-a-solution"></a>Créer une solution

Nous allons commencer notre exploration en créant une solution vide. Une fois que vous connaîtrez mieux Visual Studio, vous n’aurez sans doute pas souvent besoin de créer des solutions vides. Quand vous créez un projet, Visual Studio crée automatiquement une solution pour héberger le projet (s’il n’y a pas d’autre solution déjà ouverte).

::: moniker range="vs-2017"

1. Ouvrez Visual Studio.

1. Dans la barre de menus, choisissez **fichier** > **nouveau** > **projet**.

   La boîte de dialogue **Nouveau projet** s’affiche.

1. Dans le volet gauche, développez **Autres types de projets**, puis choisissez **Solutions Visual Studio**. Dans le volet central, choisissez le modèle **Solution vide**. Nommez votre solution **QuickSolution**, puis choisissez **OK**.

   ![Modèle Solution vide dans Visual Studio](../media/tutorial-projects-new-solution.png)

   La **page de démarrage** se ferme et une solution s’affiche dans l’**Explorateur de solutions** sur le côté droit de la fenêtre Visual Studio. **L’Explorateur de solutions** vous sera sans doute souvent utile pour parcourir le contenu de vos projets.

::: moniker-end

::: moniker range=">=vs-2019"

1. Ouvrez Visual Studio.

2. Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

3. Sur la page **Créer un projet**, entrez **nouvelle solution** dans la zone de recherche, sélectionnez le modèle **Nouvelle solution**, puis choisissez **Suivant**.

   ![Modèle de solution vide dans Visual Studio 2019](../media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Nommez la solution **QuickSolution**, puis choisissez **Créer**.

   Une solution s’affiche dans l’**Explorateur de solutions** sur le côté droit de la fenêtre Visual Studio. **L’Explorateur de solutions** vous sera sans doute souvent utile pour parcourir le contenu de vos projets.

::: moniker-end

### <a name="add-a-project"></a>Ajouter un projet

Nous allons maintenant ajouter notre premier projet à la solution. Nous allons démarrer avec un projet vide et y ajouter les éléments nécessaires.

::: moniker range="vs-2017"

1. Dans le menu contextuel, cliquez avec le bouton droit de la **solution’QuickSolution'** dans **Explorateur de solutions**, choisissez **Ajouter** > **nouveau projet**.

   La boîte de dialogue **Ajouter un nouveau projet** s'ouvre.

1. Dans le volet gauche, développez **Visual Basic**, puis choisissez **Bureau Windows**. Ensuite, dans le volet central, choisissez le modèle **Projet vide (.NET Framework)**. Nommez le projet **QuickDate**, puis choisissez le bouton **OK**.

   Un projet nommé QuickDate s’affiche en dessous de la solution dans l’**Explorateur de solutions**. Il contient un seul fichier appelé *App.config*.

   > [!NOTE]
   > Si vous ne voyez pas **Visual Basic** dans le volet gauche de la boîte de dialogue, vous devez installer la *charge de travail* Visual Studio **Développement .NET Desktop**. Visual Studio utilise une installation basée sur la charge de travail pour installer uniquement les composants dont vous avez besoin pour le type de développement que vous effectuez. Pour installer une nouvelle charge de travail, un moyen simple consiste à choisir le lien **Ouvrir Visual Studio Installer** en bas à gauche de la boîte de dialogue **Ajouter un nouveau projet**. Une fois Visual Studio Installer lancé, choisissez la charge de travail **Développement .NET Desktop**, puis cliquez sur le bouton **Modifier**.
   >
   > ![Lien Ouvrir Visual Studio Installer](media/tutorial-projects-open-installer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans le menu contextuel, cliquez avec le bouton droit de la **solution’QuickSolution'** dans **Explorateur de solutions**, choisissez **Ajouter** > **nouveau projet**.

   Une boîte de dialogue s’ouvre en indiquant **Ajouter un nouveau projet**.

1. Dans la zone de recherche située tout en haut, entrez le texte **vide**, puis sélectionnez **Visual Basic** sous **Langage**.

1. Sélectionnez le modèle **Projet vide (.NET Framework)**, puis choisissez **Suivant**.

1. Nommez le projet **QuickDate**, puis choisissez **Créer**.

   Un projet nommé QuickDate s’affiche en dessous de la solution dans l’**Explorateur de solutions**. Il contient un seul fichier appelé *App.config*.

   > [!NOTE]
   > Si vous ne voyez pas le modèle **Projet vide (.NET Framework)**, installez la *charge de travail* Visual Studio de **développement d’applications de bureau .NET**. Visual Studio utilise une installation basée sur la charge de travail pour installer uniquement les composants dont vous avez besoin pour le type de développement que vous effectuez. Pour installer une nouvelle charge de travail quand vous créez un projet, il vous suffit simplement de choisir le lien **Installer plus d’outils et de fonctionnalités** sous le texte indiquant **Vous n’arrivez pas à trouver ce que vous cherchez ?**. Une fois Visual Studio Installer lancé, choisissez la charge de travail **Développement .NET Desktop**, puis cliquez sur le bouton **Modifier**.
   >
   > ![Lien du programme d’installation dans Visual Studio 2019](../media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Ajouter un élément au projet

Nous avons un projet vide. Ajoutons un fichier de code.

1. Dans le menu contextuel (clic droit) du projet **QuickDate** dans l’**Explorateur de solutions**, choisissez **Ajouter** > **Nouvel élément**.

   La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

1. Développez **Éléments communs**, puis choisissez **Code**. Dans le volet central, choisissez le modèle d’élément **Classe**. Nommez la classe **Calendar**, puis choisissez le bouton **Ajouter**.

   Un fichier nommé *Calendar.vb* est ajouté au projet. Le *.vb* à la fin correspond à l’extension de fichier attribuée aux fichiers de code Visual Basic. Le fichier s’affiche dans la hiérarchie de projets Visual de **l’Explorateur de solutions**, et son contenu s’ouvre dans l’éditeur.

1. Remplacez le contenu du fichier *Calendar.vb* par le code suivant :

   ```vb
   Class Calendar
       Public Shared Function GetCurrentDate() As Date
           Return DateTime.Now.Date
       End Function
   End Class
   ```

   La classe `Calendar` contient une seule fonction, `GetCurrentDate`, qui retourne la date actuelle.

1. Ouvrez les propriétés du projet en double-cliquant sur **Mon projet** dans **l’Explorateur de solutions**. Sur l’onglet **Application** , remplacez **Type d’application** par **Bibliothèque de classes**. Cette étape est nécessaire pour générer correctement le projet.

1. Générez le projet en cliquant avec le bouton droit sur **QuickDate** dans **l’Explorateur de solutions** et en choisissant **Build**. Un message de réussite de la build devrait apparaître dans la fenêtre **Sortie**.

## <a name="add-a-second-project"></a>Ajouter un deuxième projet

Les solutions contiennent souvent plusieurs projets, qui font référence les uns aux autres. Les différents projets d’une solution peuvent être des bibliothèques de classes, des applications exécutables, des projets de test unitaire ou des sites web.

Nous allons ajouter un projet de test unitaire à notre solution. Cette fois, nous allons démarrer avec un modèle de projet. Nous n’avons donc pas à ajouter un fichier de code supplémentaire au projet.

1. Dans le menu contextuel (clic droit) de **Solution 'QuickSolution'** dans l’**Explorateur de solutions**, choisissez **Ajouter** > **Nouveau projet**.

::: moniker range="Vs-2017"

2. Dans le volet gauche, développez **Visual Basic** et choisissez la catégorie **Test**. Dans le volet central, choisissez le modèle de projet **Projet de test unitaire (.NET Framework)**. Nommez le projet **QuickTest**, puis choisissez **OK**.

   Un deuxième projet est ajouté à **l’Explorateur de solutions** et un fichier nommé *UnitTest1.vb* s’ouvre dans l’éditeur.

   ![Explorateur de solutions de Visual Studio avec deux projets](media/tutorial-projects-solution-explorer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Dans la boîte de dialogue **Ajouter un nouveau projet**, dans la zone de recherche située tout en haut, entrez le texte **test unitaire**, puis sélectionnez **Visual Basic** sous **Langage**.

3. Choisissez le modèle de projet **Projet de test unitaire (.NET Framework)**, puis **Suivant**.

4. Nommez le projet **QuickTest**, puis choisissez **Créer**.

   Un deuxième projet est ajouté à **l’Explorateur de solutions** et un fichier nommé *UnitTest1.vb* s’ouvre dans l’éditeur.

::: moniker-end

## <a name="add-a-project-reference"></a>Ajouter une référence au projet

Nous allons utiliser le nouveau projet de test unitaire pour tester notre méthode dans le projet **QuickDate**. Nous devons donc ajouter une référence à ce projet. Cette opération crée une *dépendance de build* entre les deux projets, ce qui signifie que quand vous générez la solution, **QuickDate** est généré avant **QuickTest**.

1. Choisissez le nœud **Références** dans le projet **QuickTest** et, dans le menu contextuel (clic droit), choisissez **Ajouter une référence**.

   ![Menu Ajouter une référence](media/tutorial-projects-add-reference-vb.png)

   La boîte de dialogue **Gestionnaire de références** s’ouvre.

1. Dans le volet gauche, développez **Projets** et choisissez **Solution**. Dans le volet central, cochez la case à côté de **QuickDate**, puis choisissez le bouton **OK**.

   Une référence au projet **QuickDate** est ajoutée.

## <a name="add-test-code"></a>Ajouter le code de test

1. Nous allons maintenant ajouter le code de test dans le fichier de code Visual Basic. Remplacez le contenu du fichier *UnitTest1.vb* par le code suivant.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(Date.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Vous voyez une ligne ondulée rouge s’afficher sous une partie du code. Pour résoudre cette erreur, nous devons référencer le projet de test comme [assembly friend](/dotnet/visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies) dans le projet **QuickDate**.

1. Retournez dans le projet **QuickDate**, ouvrez le fichier *Calendar.vb* s’il n’est pas ouvert, puis ajoutez [l’instruction Imports](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) et l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> suivants pour résoudre l’erreur dans le projet de test.

   ```vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("QuickTest")>
   ```

   Le fichier de code doit ressembler à ceci :

   ![code Visual Basic](media/tutorial-projects-code-vb.png)

## <a name="project-properties"></a>Propriétés d’un projet

Dans le fichier *Calendar.vb*, la ligne qui contient l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> fait référence au nom de l’assembly (nom de fichier) du projet **QuickTest**. Le nom de l’assembly n’est pas toujours identique au nom du projet. Pour connaître le nom de l’assembly d’un projet, ouvrez les propriétés du projet.

1. Dans **l’Explorateur de solutions**, sélectionnez le projet **QuickTest**. Dans le menu contextuel (clic droit), sélectionnez **Propriétés**, ou appuyez simplement sur **Alt**+**Entrée**. (Vous pouvez également double-cliquer sur **Mon Projet** dans **l’Explorateur de solutions**.)

   Les *pages de propriétés* du projet sont ouvertes sous l’onglet **application** . Les pages de propriétés contiennent différents paramètres pour le projet. Notez que le nom de l’assembly du projet **QuickTest** est bien « QuickTest ». Vous pouvez le changer à cet endroit si vous le souhaitez. Quand vous générez le projet de test, le nom du fichier binaire obtenu a le nouveau nom choisi à la place de *QuickTest.dll*.

   ![Propriétés d’un projet](../media/tutorial-projects-properties.png)

1. Explorez les autres onglets des pages de propriétés du projet, tels que les onglets **Compiler** et **Paramètres**. Ces onglets sont différents pour différents types de projets.

## <a name="optional-run-the-test"></a>(Facultatif) Exécuter le test

Si vous souhaitez vérifier que votre test unitaire fonctionne, choisissez **tester**  >  **exécuter**  >  **tous les tests** dans la barre de menus. Une fenêtre intitulée **Explorateur de tests** s’ouvre. Vérifiez que le résultat du test **TestGetCurrentDate** est correct.

![Team Explorer dans Visual Studio affichant le test réussi](../media/tutorial-projects-test-explorer.png)

> [!TIP]
> Si **l’Explorateur de tests** ne s’ouvre pas automatiquement, ouvrez-le en choisissant **Tester** > **Windows** > **Explorateur de tests** dans la barre de menus.

## <a name="next-steps"></a>Étapes suivantes

Pour explorer davantage Visual Studio, vous pouvez créer une application en suivant l’un des [tutoriels Visual Basic](index.yml).

## <a name="see-also"></a>Voir aussi

- [Créer des projets et des solutions](../../ide/creating-solutions-and-projects.md)
- [Gérer les propriétés des projets et des solutions](../../ide/managing-project-and-solution-properties.md)
- [Gérer les références dans un projet](../../ide/managing-references-in-a-project.md)
- [Développer du code dans Visual Studio sans projets ni solutions](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Vue d’ensemble de l’IDE de Visual Studio](../../get-started/visual-studio-ide.md)
