---
title: Page Application des propriétés de projet C#
ms.date: 10/30/2018
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 897c3a82f5add84ad343c100b93fd8a4d2663610
ms.sourcegitcommit: d4920babfc3d24a3fe1d4bf446ed3fe73b344467
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67160053"
---
# <a name="application-page-project-designer-c"></a>Page Application, Concepteur de projet (C#)

Utilisez la page **Application** du **Concepteur de projet** pour spécifier les paramètres d’application et les propriétés du projet.

Pour accéder à la page **Application**, choisissez un nœud de projet (pas le nœud **Solution**) dans l’**Explorateur de solutions**. Ensuite, choisissez **Projet** > **Propriétés** dans la barre de menus. Quand le **Concepteur de projet** s’affiche, cliquez sur l’onglet **Application**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Paramètres d’application généraux

Les options suivantes permettent de configurer les paramètres généraux de l’application.

**Nom de l’assembly**

Spécifie le nom du fichier de sortie qui contient le manifeste de l’assembly. La modification de cette propriété modifie également la propriété **Nom de sortie**.

Vous pouvez également effectuer cette modification à partir de la ligne de commande à l’aide de [/out (Options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).

Pour accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Espace de noms par défaut**

Spécifie l’espace de noms de base pour les fichiers ajoutés au projet.

Consultez la rubrique [espace de noms](/dotnet/csharp/language-reference/keywords/namespace) pour plus d’informations sur la création d’espaces de noms dans votre code.

Pour accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Framework cible**

Spécifie la version de .NET ciblée par l’application. Cette option peut avoir des valeurs différentes selon les versions de .NET installées sur votre ordinateur.

Pour les projets .NET Framework, la valeur par défaut correspond au framework cible que vous avez spécifié quand vous avez créé le projet.

Pour un projet qui cible .NET Core, les versions disponibles peuvent apparaître comme suit :

![Versions du framework cible pour un projet .NET Core](../media/application-target-framework.png)

> [!NOTE]
> Les packages de prérequis répertoriés dans la [boîte de dialogue Composants requis](../../ide/reference/prerequisites-dialog-box.md) sont définis automatiquement la première fois que vous ouvrez la boîte de dialogue. Si vous modifiez par la suite le framework cible du projet, vous devez sélectionner manuellement les prérequis pour qu’ils correspondent au nouveau framework cible.

Pour plus d’informations, consultez [Vue d’ensemble du ciblage des frameworks](../../ide/visual-studio-multi-targeting-overview.md).

**Type de sortie**

Spécifie le type d’application à générer. Les valeurs sont différentes selon le type de projet. Par exemple, pour un projet **Application console**, vous pouvez spécifier **Application Windows**, **Application console** ou **Bibliothèque de classes** comme type de sortie.

Pour un projet d’application web, vous devez spécifier **Bibliothèque de classes**.

Pour plus d’informations sur la propriété **Type de sortie**, consultez [/target (Options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).

Pour plus d’informations sur la façon d’accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.OutputType%2A>.

**Générer automatiquement des redirections de liaison**

Des redirections de liaison sont ajoutées à votre projet si votre application ou ses composants référencent plusieurs versions du même assembly. Si vous voulez définir manuellement des redirections de liaison dans le fichier projet, décochez **Générer automatiquement des redirections de liaison**.

Pour plus d’informations sur la redirection, consultez [Redirection des versions d’assemblys](/dotnet/framework/configure-apps/redirect-assembly-versions).

**Objet de démarrage**

Définit le point d’entrée à appeler quand l’application se charge. Cet objet est généralement défini sur le formulaire principal de votre application ou sur la procédure `Main` qui s’exécute quand l’application démarre. Comme les bibliothèques de classes n’ont pas de point d’entrée, la seule option disponible pour cette propriété est **(Non défini)** .

Par défaut, dans un projet d’application WPF, cette option est **(Non défini)** . L’autre option est \[nom_projet].App. Dans un projet WPF, vous devez définir l’URI de démarrage pour charger une ressource d’interface utilisateur quand l’application démarre. Pour cela, ouvrez le fichier *Application.xaml* de votre projet et définissez la propriété `StartupUri` sur un fichier *.xaml* de votre projet, par exemple, *Window1.xaml*. Pour obtenir la liste des éléments racines valides, consultez <xref:System.Windows.Application.StartupUri%2A>. Vous devez également définir une méthode `public static void Main()` dans une classe du projet. Cette classe s’affiche dans la liste **Objet de démarrage** comme *nom_projet.nom_classe*. Vous pouvez ensuite sélectionner la classe comme objet de démarrage.

Pour plus d’informations, consultez [/main (Options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). Pour accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

**Informations de l’assembly**

Ce bouton permet d’ouvrir la boîte de dialogue [Informations de l’assembly](../../ide/reference/assembly-information-dialog-box.md).

## <a name="resources"></a>Ressources

Les options de **Ressources** vous permettent de configurer les paramètres des ressources pour votre application.

**Icône et manifeste**

Par défaut, cette case d’option est sélectionnée et les options **Icône** et **Manifeste** sont activées. Cela vous permet de sélectionner votre propre icône ou différentes options de génération du manifeste. Laissez cette case d’option sélectionnée, sauf si vous fournissez un fichier de ressources pour le projet.

**Icône**

Définit le fichier *.ico* à utiliser comme icône de votre programme. Cliquez sur le bouton **Parcourir** pour accéder à un graphique existant ou tapez le nom du fichier souhaité. Pour plus d’informations, consultez [/win32icon (Options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option).

Pour accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

**Manifest**

Sélectionne une option de génération de manifeste quand l’application s’exécute sur Windows Vista sous contrôle de compte d’utilisateur (UAC). Cette option peut avoir les valeurs suivantes :

- **Incorporer les paramètres par défaut dans le fichier manifeste**. Prend en charge le fonctionnement standard de Visual Studio sur Windows Vista, qui incorpore les informations de sécurité dans le fichier exécutable de l’application, en indiquant que `requestedExecutionLevel` doit être `AsInvoker`. Il s'agit de l'option par défaut.

- **Créer une application sans fichier manifeste**. Cette méthode est appelée *virtualisation*. Utilisez cette option pour la compatibilité avec les applications antérieures.

- **Propriétés\app.manifest**. Cette option est obligatoire pour les applications déployées par ClickOnce ou COM sans inscription. Si vous publiez une application à l’aide du déploiement ClickOnce, l’option **Manifeste** est automatiquement définie sur cette option.

**Fichier de ressources**

Sélectionnez cette case d’option, sauf si vous fournissez un fichier de ressources pour le projet. Cette option désactive les options **Icône** et **Manifeste**.

Entrez un nom de chemin ou utilisez le bouton Parcourir ( **...** ) pour ajouter un fichier de ressources Win32 au projet.