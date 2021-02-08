---
title: Page Application des propriétés de projet VB
description: Découvrez comment utiliser la page application du concepteur de projet Visual Basic pour spécifier les paramètres d’application et les propriétés du projet.
ms.custom: SEO-VS-2020
ms.date: 10/30/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 986179e66335403cda85ba48d1652ac95b9f8171
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836525"
---
# <a name="application-page-project-designer-visual-basic"></a>Page Application, Concepteur de projet (Visual Basic)

Utilisez la page **Application** du Concepteur de projet pour spécifier les paramètres d’application et les propriétés du projet.

Pour accéder à la page **Application**, choisissez un nœud de projet (pas le nœud **Solution**) dans l’**Explorateur de solutions**. Choisissez ensuite   >  **Propriétés** du projet dans la barre de menus. Quand le **Concepteur de projet** apparaît, sélectionnez l’onglet **Application**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Paramètres généraux d’une application

Les options suivantes permettent de configurer les paramètres généraux d’une application.

### <a name="assembly-name"></a>Nom de l'assembly

Spécifie le nom du fichier de sortie qui contient le manifeste de l’assembly. La modification de cette propriété modifie également la propriété **Nom de sortie**.

Vous pouvez aussi spécifier le nom du fichier de sortie dans une invite de commandes, à l’aide du commutateur de compilateur [/out (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/out).

Pour plus d’informations sur la façon d’accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

### <a name="root-namespace"></a>Espace de noms racine

Spécifie l’espace de noms de base pour tous les fichiers du projet. Par exemple, si vous définissez l’**espace de noms racine** sur `Project1` et que vous avez un `Class1` en dehors des espaces de noms dans votre code, son espace de noms est `Project1.Class1`. Si vous avez un `Class2` dans un espace de noms `Order` dans le code, son espace de noms est `Project1.Order.Class2`.

Si vous effacez l’**espace de noms racine**, vous pouvez spécifier la structure de l’espace de noms de votre projet dans le code.

> [!NOTE]
> Si vous utilisez le mot clé `Global` dans une [instruction Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement), vous pouvez définir un espace de noms en dehors de l’espace de noms racine de votre projet. Si vous effacez l' **espace de noms racine**, `Global` devient l’espace de noms de niveau supérieur, ce qui supprime le recours au `Global` mot clé dans une `Namespace` instruction. Pour plus d’informations, consultez « Mot clé Global dans les instructions Namespace » dans [Espaces de noms dans Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces).

Pour plus d’informations sur la création d’espaces de noms dans votre code, consultez [Instruction Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement).

Pour plus d’informations sur la propriété d’espace de noms racine, consultez [/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace).

Pour plus d’informations sur la façon d’accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

### <a name="target-framework-all-configurations"></a>Version cible de .NET Framework (toutes les configurations)

Spécifie la version de .NET ciblée par l’application. Cette option peut avoir des valeurs différentes selon les versions de .NET installées sur votre ordinateur.

Pour les projets .NET Framework, la valeur par défaut correspond au framework cible que vous avez spécifié quand vous avez créé le projet.

> [!NOTE]
> Les packages de prérequis répertoriés dans la [boîte de dialogue Composants requis](../../ide/reference/prerequisites-dialog-box.md) sont définis automatiquement la première fois que vous ouvrez la boîte de dialogue. Si vous modifiez par la suite le framework cible du projet, vous devez spécifier manuellement les prérequis pour qu’ils correspondent au nouveau framework cible.

Pour plus d’informations, consultez [Vue d’ensemble du ciblage des frameworks](../../ide/visual-studio-multi-targeting-overview.md).

### <a name="application-type"></a>Type d'application

Spécifie le type d’application à générer. Les valeurs sont différentes selon le type de projet. Par exemple, pour un projet **Application Windows Forms**, vous pouvez spécifier **Application Windows Forms**, **Bibliothèque de classes**, **Application console**, **Service Windows** ou **Bibliothèque de contrôles web**.

Pour un projet d’application web, vous devez spécifier **Bibliothèque de classes**.

Pour plus d’informations sur la propriété **Type d’application**, consultez [/target (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/target). Pour plus d’informations sur la façon d’accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.OutputType%2A>.

### <a name="auto-generate-binding-redirects"></a>Générer automatiquement des redirections de liaison

Des redirections de liaison sont ajoutées à votre projet si votre application ou ses composants référencent plusieurs versions du même assembly. Si vous voulez définir manuellement des redirections de liaison dans le fichier projet, décochez **Générer automatiquement des redirections de liaison**.

Pour plus d’informations sur la redirection, consultez [Redirection des versions d’assemblys](/dotnet/framework/configure-apps/redirect-assembly-versions).

### <a name="startup-form--startup-object--startup-uri"></a>Formulaire de démarrage / Objet de démarrage / URI de démarrage

Spécifie le formulaire de démarrage ou le point d’entrée de l’application.

Si **Activer l’infrastructure de l’application** est sélectionné (par défaut), cette liste est intitulée **Formulaire de démarrage** et affiche uniquement des formulaires, car le framework d’application ne prend en charge que les formulaires de démarrage, et non les objets.

Si le projet est une application de navigateur WPF, cette liste est intitulée **URI de démarrage** et la valeur par défaut est **Page1.xaml**. La liste **URI de démarrage** permet de spécifier la ressource d’interface utilisateur (un élément XAML) que l’application affiche au démarrage. Pour plus d’informations, consultez <xref:System.Windows.Application.StartupUri%2A>.

Si **Activer l’infrastructure de l’application** n’est pas sélectionné, cette liste devient **Objet de démarrage**, et affiche des formulaires et des classes ou des modules avec un `Sub Main`.

L’**objet de démarrage** définit le point d’entrée à appeler quand l’application se charge. Cet objet est généralement défini sur le formulaire principal de votre application ou sur la procédure `Sub Main` qui s’exécute quand l’application démarre. Comme les bibliothèques de classes n’ont pas de point d’entrée, la seule option disponible pour cette propriété est **(Aucun)**. Pour plus d’informations, consultez [/main](/dotnet/visual-basic/reference/command-line-compiler/main). Pour accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

### <a name="icon"></a>Icône

Définit le fichier .ico à utiliser comme icône de votre programme. Sélectionnez cette option **\<Browse...>** pour rechercher un graphique existant. Pour plus d’informations, consultez [/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) (ou [/win32icon (Options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). Pour accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

### <a name="assembly-information"></a>Informations de l’assembly

Cliquez sur ce bouton pour afficher la [boîte de dialogue Informations de l’assembly](../../ide/reference/assembly-information-dialog-box.md).

### <a name="enable-application-framework"></a>Activer l’infrastructure d’application

Spécifie si un projet utilise le framework d’application. La valeur de cette option affecte les options disponibles dans l’objet de démarrage du formulaire de **démarrage** / .

Si cette case est cochée, votre application utilise le `Sub Main` standard. En cochant cette case, vous activez les fonctionnalités de la section **Propriétés de l’infrastructure d’application Windows** et vous êtes invité à sélectionner un formulaire de démarrage.

Si cette case est décochée, votre application utilise le `Sub Main` personnalisé que vous avez spécifié dans le **Formulaire de démarrage**. Dans ce cas, vous pouvez spécifier un objet de démarrage (un `Sub Main` personnalisé dans une méthode ou une classe) ou un formulaire. Par ailleurs, les options de la section **Propriétés de l’infrastructure d’application Windows** deviennent indisponibles.

### <a name="view-windows-settings"></a>Afficher les paramètres Windows

Cliquez sur ce bouton pour générer et ouvrir le fichier *app. manifest* . Visual Studio utilise ce fichier pour générer des données de manifeste pour l’application. Définissez ensuite le niveau d’exécution demandé du contrôle de compte d’utilisateur en modifiant la `<requestedExecutionLevel>` balise dans *app. manifest* comme suit :

`<requestedExecutionLevel level="asInvoker" />`

ClickOnce fonctionne avec le niveau `asInvoker` ou en mode virtualisé (aucune génération de manifeste). Pour spécifier le mode virtualisé, supprimez l’intégralité de la balise dans app.manifest.

Pour plus d’informations sur la génération du manifeste, consultez [Déploiement ClickOnce sur Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Propriétés de l’infrastructure d’application Windows

Les paramètres suivants sont disponibles dans la section **Propriétés de l’infrastructure d’application Windows**. Ces options sont disponibles uniquement si la case **Activer l’infrastructure de l’application** est cochée.

> [!TIP]
> La section suivante décrit les paramètres des **Propriétés de l’infrastructure d’application Windows** spécifiques aux applications Windows Presentation Foundation (WPF).

### <a name="enable-xp-visual-styles"></a>Activer les styles visuels XP

Active ou désactive les styles visuels Windows XP, également appelés *Thèmes Windows XP*. Les styles visuels Windows XP activent, par exemple, les contrôles avec des angles arrondis et des couleurs dynamiques. Il est activé par défaut.

### <a name="make-single-instance-application"></a>Créer une application à instance unique

Cochez cette case pour empêcher les utilisateurs d’exécuter plusieurs instances de l’application. Le paramètre par défaut de cette case à cocher est *désactivé*, ce qui permet à plusieurs instances de l’application de s’exécuter. Pour plus d'informations, consultez l'événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>.

### <a name="save-mysettings-on-shutdown"></a>Enregistrer My.Settings à l’arrêt

Cochez cette case pour spécifier que les paramètres `My.Settings` de l’application sont enregistrés quand les utilisateurs éteignent leur ordinateur. La case est cochée par défaut. Si cette option est désactivée, vous pouvez enregistrer manuellement les paramètres de l’application en appelant `My.Settings.Save`.

### <a name="authentication-mode"></a>Mode d'authentification

Sélectionnez **Windows** (la valeur par défaut) pour spécifier l’utilisation de l’authentification Windows afin d’identifier l’utilisateur actuellement connecté. Vous pouvez récupérer ces informations au moment de l’exécution à l’aide de l’objet `My.User`. Sélectionnez **Défini par l’application** si vous fournissez votre propre code pour authentifier les utilisateurs au lieu d’utiliser les méthodes d’authentification Windows par défaut.

### <a name="shutdown-mode"></a>Mode d’arrêt

Sélectionnez **À la fermeture du formulaire de démarrage** (valeur par défaut) pour spécifier que l’application doit se fermer à la fermeture du formulaire de démarrage défini, même si d’autres formulaires sont ouverts. Sélectionnez **À la fermeture du dernier formulaire** pour spécifier que l’application doit se fermer à la fermeture du dernier formulaire, ou quand `My.Application.Exit` ou l’instruction `End` est explicitement appelée.

Sélectionnez **Lors de l’arrêt explicite** pour spécifier que l’application doit se fermer quand vous appelez explicitement `Shutdown`.

Sélectionnez **Lors de la fermeture de la dernière fenêtre** pour spécifier que l’application doit se fermer à la fermeture de la dernière fenêtre ou quand vous appelez explicitement `Shutdown`. Il s'agit du paramètre par défaut.

Sélectionnez **Lors de la fermeture de la fenêtre principale** pour spécifier que l’application doit se fermer à la fermeture de la fenêtre principale ou quand vous appelez explicitement `Shutdown`.

### <a name="splash-screen"></a>Écran de démarrage

Sélectionnez le formulaire à utiliser comme écran de démarrage. Vous devez déjà avoir créé un écran de démarrage à l’aide d’un formulaire ou d’un modèle. La valeur par défaut est **(aucune)**.

### <a name="view-application-events"></a>Afficher les événements de l’application

Cliquez sur ce bouton pour afficher un fichier de code d’événements dans lequel vous pouvez écrire des événements du framework d’application `Startup`, `Shutdown`, `UnhandledException`, `StartupNextInstance` et `NetworkAvailabilityChanged`. Vous pouvez également remplacer certaines méthodes du framework d’application. Par exemple, vous pouvez modifier le comportement d’affichage de l’écran de démarrage en remplaçant `OnInitialize`.

## <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-apps"></a>Propriétés du framework d’application Windows pour les applications WPF (Windows Presentation Foundation)

Les paramètres suivants sont disponibles dans la section **Propriétés de l’infrastructure d’application Windows** quand le projet est une application WPF (Windows Presentation Foundation). Ces options sont disponibles uniquement si la case **Activer l’infrastructure de l’application** est cochée. Les options listées dans ce tableau sont disponibles seulement pour les applications WPF ou les applications de navigateur WPF. Elles ne sont pas disponibles pour les bibliothèques de contrôles personnalisés ou de contrôles utilisateur WPF.

### <a name="shutdown-mode"></a>Mode d’arrêt

Cette propriété s’applique uniquement aux applications WPF (Windows Presentation Foundation).

Sélectionnez **Lors de l’arrêt explicite** pour spécifier que l’application doit se fermer quand vous appelez explicitement <xref:System.Windows.Application.Shutdown%2A>.

Sélectionnez **Lors de la fermeture de la dernière fenêtre** pour spécifier que l’application doit se fermer à la fermeture de la dernière fenêtre ou quand vous appelez explicitement <xref:System.Windows.Application.Shutdown%2A>. Il s'agit du paramètre par défaut.

Sélectionnez **Lors de la fermeture de la fenêtre principale** pour spécifier que l’application doit se fermer à la fermeture de la fenêtre principale ou quand vous appelez explicitement <xref:System.Windows.Application.Shutdown%2A>.

Pour plus d’informations sur l’utilisation de ce paramètre, consultez <xref:System.Windows.Application.Shutdown%2A>

### <a name="edit-xaml"></a>Modifier XAML

Ce bouton permet d’ouvrir le fichier de définition d’application (Application.xaml) dans l’éditeur XAML. Lorsque vous cliquez sur ce bouton, *application. Xaml* s’ouvre au niveau du nœud de définition d’application. Vous devez peut-être modifier ce fichier pour effectuer certaines tâches, comme la définition des ressources. Si le fichier de définition d’application n’existe pas, le Concepteur de projet en crée un.

### <a name="view-application-events"></a>Afficher les événements de l’application

Ce bouton permet d’ouvrir le fichier de classe `Application` (*Application.xaml.vb*) dans un éditeur de code. Si le fichier n’existe pas, le Concepteur de projet en crée un avec le nom de classe et l’espace de noms appropriés.

L’objet <xref:System.Windows.Application> déclenche des événements quand certaines modifications de l’état de l’application se produisent (par exemple, au démarrage ou à l’arrêt de l’application). Pour obtenir la liste complète des événements exposés par cette classe, consultez <xref:System.Windows.Application>. Ces événements sont traités dans la section de code utilisateur de la classe partielle `Application`.
