---
title: Ajouter des références dans le Gestionnaire de références
ms.date: 04/11/2018
ms.topic: conceptual
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- C# projects, references
- references [Visual Studio], adding
- assemblies [Visual Studio], references
- Visual Basic projects, references
- project references, adding
- referencing components, adding references
- project references, removing
- referencing assemblies
- referencing components, removing references
- references [Visual Studio], removing
- referencing components, assemblies not listed
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 885dee2ca04060042e804ff964636d16e6a725ee
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745813"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Procédure : Ajouter ou supprimer des références à l’aide du gestionnaire de références

Vous pouvez utiliser la boîte de dialogue **Gestionnaire de références** pour ajouter et gérer des références aux composants développés par vous, par Microsoft ou par une autre société. Si vous développez une application Windows universelle, votre projet référence automatiquement toutes les DLL correctes du kit SDK Windows. Si vous développez une application .NET, votre projet référence automatiquement *mscorlib.dll*. Certaines API .NET sont exposées dans des composants que vous devez ajouter manuellement. Les références à des composants COM ou à des composants personnalisés doivent être ajoutées manuellement.

## <a name="reference-manager-dialog-box"></a>Boîte de dialogue Gestionnaire de références

La boîte de dialogue **Gestionnaire de références** affiche différentes catégories sur le côté gauche, en fonction du type de projet :

- **Assemblys**, avec les sous-groupes **Framework** et **Extensions**.

- **COM** répertorie tous les composants COM pouvant être référencés.

- **Solution**, avec le sous-groupe **Projets**.

- **Windows**, avec les sous-groupes **Principal** et **Extensions**. Vous pouvez explorer les références dans le SDK Windows ou les SDK de l’extension à l’aide de l’**Explorateur d’objets**.

- **Parcourir**, avec le sous-groupe **Récent**.

## <a name="add-a-reference"></a>Ajouter une référence

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références** ou **Dépendances**, puis choisissez **Ajouter une référence**. Vous pouvez également cliquer avec le bouton droit sur le nœud de projet, et sélectionner **Ajouter** > **Référence**.

   Le **Gestionnaire de références** s’ouvre et affiche la liste des références disponibles par groupe.

2. Spécifiez les références à ajouter, puis sélectionnez **OK**.

## <a name="assemblies-tab"></a>Onglet Assemblys

L’onglet **Assemblys** liste tous les assemblys .NET qui sont disponibles pour le référencement. L’onglet **Assemblys** ne répertorie pas les assemblys du Global Assembly Cache (GAC), car ceux-ci appartiennent à l’environnement d’exécution. Si vous déployez ou copiez une application qui contient une référence à un assembly inscrit dans le GAC, cet assembly n’est ni déployé ni copié avec l’application, quelle que soit la valeur du paramètre **Copie locale**. Pour plus d’informations, consultez [Gérer les références dans un projet](../ide/managing-references-in-a-project.md).

Quand vous ajoutez manuellement une référence à l’un des espaces de noms EnvDTE (<xref:EnvDTE>, <xref:EnvDTE80>, <xref:EnvDTE90>, <xref:EnvDTE90a> ou <xref:EnvDTE100>), affectez la valeur **False** à la propriété **Incorporer les types interop**, dans la fenêtre **Propriétés**. Si cette propriété a la valeur **True**, des problèmes de génération peuvent survenir car certaines propriétés EnvDTE ne peuvent pas être incorporées.

Tous les projets d’application de bureau contiennent une référence implicite à **mscorlib**. Les projets Visual Basic contiennent une référence implicite à <xref:Microsoft.VisualBasic>. Tous les projets contiennent une référence implicite à **System.Core**, même s’il est supprimé de la liste des références.

Si un type de projet ne prend pas en charge les assemblys, l’onglet ne s’affiche pas dans la boîte de dialogue **Gestionnaire de références**.

L’onglet **Assemblys** comprend deux sous-onglets :

1. **Framework** liste tous les assemblys qui constituent le framework ciblé.

   Pour les projets qui ne ciblent pas .NET Core ou la plateforme Windows universelle, l’onglet **Framework** énumère les assemblys du framework ciblé. L’utilisateur doit ajouter les références nécessaires à l’application.

   Les projets Windows universel contiennent des références à tous les assemblys dans le framework ciblé par défaut. Dans les projets managés, un nœud en lecture seule dans le dossier **Références** de l’**Explorateur de solutions** indique la référence à l’intégralité du framework. Ainsi, l’onglet **Framework** n’énumère aucun des assemblys du framework. Il affiche à la place le message suivant : « Tous les assemblys du framework sont déjà référencés. Utilisez l’Explorateur d’objets pour explorer les références dans le Framework. ».

2. **Extensions** liste tous les assemblys que les fournisseurs externes de composants et de contrôles ont développés pour étendre le framework ciblé. Selon l'objectif de l'application utilisateur, ces assemblys peuvent être nécessaires.

   Les **extensions** sont remplies à partir de l’énumération des assemblys inscrits dans les emplacements suivants :

   Machine 32 bits :
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   Machine 64 bits :
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   Et les anciennes versions de [identificateur du framework cible]

   Par exemple, si un projet cible le .NET Framework 4 sur une machine 32 bits, les **extensions** énumèrent les assemblys inscrits sous *\Microsoft\.NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.5\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.0\AssemblyFoldersEx* et *\Microsoft\.NETFramework\v2.0\AssemblyFoldersEx*.

Selon la version du framework de votre projet, certains composants de la liste peuvent ne pas être affichés. Cela peut se produire dans les conditions suivantes :

- Un composant qui utilise une version récente du framework est incompatible avec un projet qui cible une version antérieure.

   Pour plus d’informations sur la façon de changer la version du framework cible pour un projet, consultez [Guide pratique pour cibler une version du framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

- Un composant qui utilise le .NET Framework 4 est incompatible avec un projet qui cible le .NET Framework 4.5.

Évitez si possible d'ajouter des références de fichier aux sorties d'un autre projet de la même solution, car cela risquerait de provoquer des erreurs de compilation. Utilisez l’onglet **Projets** de la boîte de dialogue **Ajouter une référence** afin de créer des références entre projets. Cela facilite le développement en équipe, en permettant une meilleure gestion des bibliothèques de classes créées dans vos projets. Pour plus d’informations, consultez [Dépanner des références rompues](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> Dans Visual Studio 2015 ou ultérieur, une référence de fichier est créée au lieu d’une référence de projet si la version du framework cible d’un projet est .NET Framework 4.5 ou ultérieure, et que la version cible de l’autre projet est .NET Framework 2, 3, 3.5 ou 4.0.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Pour afficher un assembly dans la boîte de dialogue Ajouter une référence

- Déplacez ou copiez l'assembly vers l'un des emplacements suivants :

   - Le répertoire de projet actuel (vous pouvez rechercher ces assemblys via l’onglet **Parcourir** ).

   - Autres répertoires de projet de la même solution (vous pouvez rechercher ces assemblys à l’aide de l’onglet **Projets**)

    \- ou -

- Définissez une clé de Registre qui spécifie l'emplacement des assemblys à afficher :

   Sur un système d'exploitation 32 bits, ajoutez l'une des clés de Registre suivantes :

   - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   Sur un système d'exploitation 64 bits, ajoutez l'une des clés de Registre suivantes dans une ruche du Registre 32 bits  :

   - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   *\<VersionMinimum\>* représente la version la plus ancienne du framework pouvant s’appliquer. Si *\<VersionMinimum\>* a la valeur v3.0, les dossiers spécifiés dans *AssemblyFoldersEx* s’appliquent aux projets qui ciblent .NET Framework 3.0 et les versions ultérieures.

   *\<AssemblyLocation\>* correspond au répertoire des assemblys que vous souhaitez voir figurer dans la boîte de dialogue **Ajouter une référence** (par exemple *C:\MyAssemblies*).

   La création de la clé de Registre sous le nœud `HKEY_LOCAL_MACHINE` permet à tous les utilisateurs de voir les assemblys à l’emplacement spécifié dans la boîte de dialogue **Ajouter une référence**. La création de la clé de Registre sous le nœud `HKEY_CURRENT_USER` affecte uniquement le paramètre de l’utilisateur actuel.

   Rouvrez la boîte de dialogue **Ajouter une référence**. Les assemblys doivent apparaître sous l’onglet **.NET**. Si ce n’est pas le cas, vérifiez que les assemblys se trouvent dans le répertoire *AssemblyLocation* spécifié, redémarrez Visual Studio, puis réessayez.

## <a name="projects-tab"></a>Onglet Projets

L’onglet **Projets** liste tous les projets compatibles de la solution actuelle, sous le sous-onglet **Solution**.

Un projet peut référencer un autre projet qui cible une version différente du framework. Par exemple, vous pouvez créer un projet qui cible .NET Framework 4, mais qui référence un assembly qui a créé pour .NET Framework 2. Cependant, le projet .NET Framework 2 ne peut pas référencer un projet .NET Framework 4. Pour plus d’informations, consultez [Vue d’ensemble du ciblage des frameworks](../ide/visual-studio-multi-targeting-overview.md).

> [!NOTE]
> Un projet qui cible le .NET Framework 4 est incompatible avec un projet qui cible le profil de client du .NET Framework 4.

## <a name="universal-windows-tab"></a>Onglet Windows universel

L’onglet **Windows universel** liste tous les SDK spécifiques aux plateformes sur lesquelles des systèmes d’exploitation Windows s’exécutent.
Cet onglet comprend deux sous-groupes : **Principal** et **Extensions**.

### <a name="core-subgroup"></a>Sous-groupe Principal

Les projets d’application Windows universelles ont une référence au SDK Windows universel par défaut. Ainsi, le sous-groupe **Principal** du **Gestionnaire de références** n’énumère pas les assemblys du SDK Windows universel.

### <a name="extensions-subgroup"></a>Sous-groupe Extensions

Les **extensions** listent les kits SDK utilisateur qui étendent la plateforme Windows ciblée.

Un kit SDK est une collection de fichiers que Visual Studio traite comme un seul composant. Sous l’onglet **Extensions**, les kits SDK qui s’appliquent au projet à partir duquel la boîte de dialogue **Gestionnaire de références** a été appelée sont listés sous forme d’entrées uniques. Une fois ajouté à un projet, tout le contenu du kit SDK est utilisé par Visual Studio afin que l’utilisateur n’ait rien d’autre à faire pour l’exploiter dans IntelliSense, la boîte à outils, les concepteurs, l’Explorateur d’objets, la création, le déploiement, le débogage et l’empaquetage.

Pour plus d’informations sur l’affichage de votre kit SDK sous l’onglet **Extensions**, consultez [Création d’un kit SDK](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> Si un projet référence un SDK qui dépend d’un autre SDK, Visual Studio n’utilise pas le second SDK, sauf si vous ajoutez manuellement une référence à celui-ci. Quand un utilisateur choisit un SDK sous l’onglet **Extensions**, la boîte de dialogue **Gestionnaire de références** l’aide à identifier les dépendances du SDK en les listant dans le volet d’informations.

Si un type de projet ne prend pas en charge les extensions, cet onglet n’apparaît pas dans la boîte de dialogue **Gestionnaire de références**.

## <a name="com-tab"></a>Onglet COM

L’onglet **COM** liste tous les composants COM pouvant être référencés. Si vous souhaitez ajouter une référence à une DLL COM inscrite qui contient un manifeste interne, annulez d'abord l'inscription de la DLL. Sinon, Visual Studio ajoute la référence d’assembly en tant que contrôle ActiveX, et non en tant que DLL native.

Si un type de projet ne prend pas en charge COM, l’onglet ne s’affiche pas dans la boîte de dialogue **Gestionnaire de références**.

## <a name="browse-button"></a>Bouton Parcourir

Vous pouvez utiliser le bouton **Parcourir** pour rechercher un composant dans le système de fichiers.

Un projet peut référencer un composant qui cible une version différente du framework. Par exemple, vous pouvez créer une application qui cible .NET Framework 4.7, mais qui référence un composant ciblant .NET Framework 4. Pour plus d’informations, consultez [Vue d’ensemble du ciblage des frameworks](../ide/visual-studio-multi-targeting-overview.md).

Évitez d’ajouter des références de fichier aux sorties d’un autre projet de la même solution, car cela risquerait de provoquer des erreurs de compilation. Utilisez plutôt l’onglet **Solution** de la boîte de dialogue **Gestionnaire de références** afin de créer des références entre projets. Cela facilite le développement en équipe, en permettant une meilleure gestion des bibliothèques de classes créées dans vos projets. Pour plus d’informations, consultez [Dépanner des références rompues](../ide/troubleshooting-broken-references.md).

Vous ne pouvez pas accéder à un kit SDK et l’ajouter à votre projet. Vous pouvez uniquement rechercher un fichier (par exemple un assembly ou un fichier *.winmd*) et l’ajouter à votre projet.

Quand vous faites une référence de fichier à un fichier WinMD, la disposition attendue est la suivante : les fichiers *\<nom_fichier>.winmd*, *\<nom_fichier>.dll* et *\<nom_fichier>.pri* sont placés les uns aux côtés des autres. Si vous référencez un fichier WinMD dans les scénarios suivants, un ensemble incomplet de fichiers est copié dans le répertoire de sortie du projet et, par conséquent, des erreurs de rendu et d'exécution se produisent.

- **Composant natif** : un projet natif crée un fichier WinMD pour chaque ensemble d’espaces de noms disjoint et une DLL qui contient l’implémentation. Les WinMD auront des noms disparates. En référençant ce fichier de composant natif, MSBuild ne détecte pas que les WinMD nommés différemment constituent un même composant. Ainsi, seuls les fichiers *\<nom_fichier>.dll* et *\<nom_fichier>.winmd* portant le même nom sont copiés, et des erreurs d’exécution se produisent. Pour contourner ce problème, créez un kit SDK d’extension. Pour plus d’informations, consultez [Créer un kit SDK](../extensibility/creating-a-software-development-kit.md).

- **Utilisation de contrôles** : au minimum, un contrôle XAML comprend un fichier *\<nom_fichier>.winmd*, *\<nom_fichier>.dll*, *\<nom_fichier>.pri*, *\<nom_xaml>.xaml* et *\<nom_image>.jpg*. Quand le projet est généré, les fichiers de ressources associés à la référence de fichier ne sont pas copiés dans le répertoire de sortie du projet. Seuls les fichiers *\<nom_fichier>.winmd*, *\<nom_fichier>.dll* et *\<nom_fichier>.pri sont copiés*. Une erreur de build est journalisée pour indiquer à l’utilisateur que les ressources *\<nom_xaml>.xaml* et *\<nom_image>.jpg* sont manquantes. Pour que l'opération réussisse, l'utilisateur doit copier manuellement les fichiers de ressources dans le répertoire de sortie du projet pour la génération et le débogage/l'exécution. Pour contourner ce problème, créez un kit SDK d’extension en suivant les étapes décrites dans [Créer un kit SDK](../extensibility/creating-a-software-development-kit.md), ou modifiez le fichier projet pour ajouter la propriété suivante :

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Si vous ajoutez la propriété, la build peut s'exécuter plus lentement.

## <a name="recent"></a>Récent

Les éléments **Assemblys**, **COM**, **Windows** et **Parcourir** prennent tous en charge un onglet **Récent**, qui énumère la liste des composants ajoutés récemment aux projets.

## <a name="search"></a>Rechercher

La barre de recherche de la boîte de dialogue **Gestionnaire de références** fonctionne sur l’onglet actif. Par exemple, si un utilisateur tape « System » dans la barre de recherche alors que l’onglet **Solution** est actif, la recherche ne renvoie aucun résultat à moins que la solution soit composée d’un nom de projet contenant « System ».

## <a name="see-also"></a>Voir aussi

- [Gérer les références dans un projet](../ide/managing-references-in-a-project.md)