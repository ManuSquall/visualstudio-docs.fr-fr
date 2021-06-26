---
title: Ajouter des références dans le Gestionnaire de références
description: Découvrez comment utiliser la boîte de dialogue Gestionnaire de références pour ajouter et gérer des références aux composants développés.
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: how-to
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 552ec8364bb58b72199bacecca99283303eb174c
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924914"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Guide pratique pour ajouter ou supprimer des références à l’aide du Gestionnaire de références

Vous pouvez utiliser la boîte de dialogue Gestionnaire de références pour ajouter et gérer des références aux composants développés par vous, par Microsoft ou par une autre société. Si vous développez une application Windows universelle, votre projet référence automatiquement toutes les DLL correctes du kit SDK Windows. Si vous développez une application .NET, votre projet référence automatiquement *mscorlib.dll*. Certaines API .NET sont exposées dans des composants que vous devez ajouter manuellement. Les références à des composants COM ou à des composants personnalisés doivent être ajoutées manuellement.

## <a name="reference-manager-dialog-box"></a>Boîte de dialogue Gestionnaire de références

La boîte de dialogue Gestionnaire de références affiche différentes catégories sur le côté gauche, en fonction du type de projet :

- **Assemblys**, avec les sous-groupes **Framework** et **Extensions**

- **Com** répertorie tous les composants COM pouvant être référencés

- **Projets**

- **Projets partagés**

- **Windows**, avec les sous-groupes **Principal** et **Extensions** Vous pouvez explorer les références dans le SDK Windows ou les SDK de l’extension à l’aide de l’**Explorateur d’objets**.

- **Parcourir**, avec le sous-groupe **Récent**
 
    > [!NOTE]
    > Vous ne verrez peut-être pas **Parcourir** dans la boîte de dialogue Gestionnaire de références si vous développez des projets C++.

## <a name="add-a-reference"></a>Ajouter une référence

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références** ou **Dépendances**, puis choisissez **Ajouter une référence**. Vous pouvez également cliquer avec le bouton droit sur le nœud du projet et sélectionner **Ajouter** une  >  **référence**.

   Le **Gestionnaire de références** s’ouvre et affiche la liste des références disponibles par groupe.

2. Spécifiez les références à ajouter, puis sélectionnez **OK**.

## <a name="assemblies-tab"></a>Onglet Assemblys

L’onglet **Assemblys** liste tous les assemblys .NET qui sont disponibles pour le référencement. L’onglet **Assemblys** ne répertorie pas les assemblys du Global Assembly Cache (GAC), car ceux-ci appartiennent à l’environnement d’exécution. Si vous déployez ou copiez une application qui contient une référence à un assembly inscrit dans le GAC, l’assembly ne sera ni déployé ni copié avec l’application, quel que soit le paramètre de **copie locale** . Pour plus d’informations, consultez [Gérer les références dans un projet](../ide/managing-references-in-a-project.md).

Quand vous ajoutez manuellement une référence à l’un des espaces de noms EnvDTE (<xref:EnvDTE>, <xref:EnvDTE80>, <xref:EnvDTE90>, <xref:EnvDTE90a> ou <xref:EnvDTE100>), affectez la valeur **False** à la propriété **Incorporer les types interop**, dans la fenêtre **Propriétés**. L’affectation de la **valeur true** à cette propriété peut entraîner des problèmes de génération en raison de certaines propriétés EnvDTE qui ne peuvent pas être incorporées.

Tous les projets d’application de bureau contiennent une référence implicite à **mscorlib**. Les projets Visual Basic contiennent une référence implicite à <xref:Microsoft.VisualBasic>. Tous les projets contiennent une référence implicite à **System.Core**, même s’il est supprimé de la liste des références.

Si un type de projet ne prend pas en charge les assemblys, l’onglet ne s’affiche pas dans la boîte de dialogue Gestionnaire de références.

L’onglet **Assemblys** comprend deux sous-onglets :

1. **Framework** répertorie tous les assemblys qui constituent le Framework ciblé.

   Pour les projets qui ne ciblent pas .NET Core ou la plateforme Windows universelle, l’onglet **Framework** énumère les assemblys du framework ciblé. L’utilisateur doit ajouter les références nécessaires à l’application.

   Les projets Windows universel contiennent des références à tous les assemblys dans le framework ciblé par défaut. Dans les projets managés, un nœud en lecture seule dans le dossier **références** de **Explorateur de solutions** indique la référence à l’ensemble de l’infrastructure. En conséquence, l’onglet **Framework** n’énumère pas les assemblys du Framework et affiche à la place le message suivant : «tous les assemblys du Framework sont déjà référencés. Utilisez l’Explorateur d’objets pour explorer les références dans le Framework. ».

2. **Extensions** répertorie tous les assemblys que les fournisseurs externes de composants et les contrôles ont développés pour étendre le Framework ciblé. Selon l'objectif de l'application utilisateur, ces assemblys peuvent être nécessaires.

   Les **Extensions** sont remplies en énumérant les assemblys qui sont enregistrés dans les emplacements suivants :

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

   Pour plus d’informations sur la façon de changer la version du framework cible pour un projet, consultez [Vue d’ensemble du ciblage des frameworks](visual-studio-multi-targeting-overview.md).

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

  *\<VersionMinimum\>* est la version de Framework la plus basse qui s’applique. Si *\<VersionMinimum\>* a la valeur v 3.0, les dossiers spécifiés dans *AssemblyFoldersEx* s’appliquent aux projets qui ciblent .NET Framework 3,0 et versions ultérieures.

  *\<AssemblyLocation\>* est le répertoire des assemblys que vous souhaitez afficher dans la boîte de dialogue **Ajouter une référence** , par exemple *c:\MyAssemblies)*.

  La création de la clé de Registre sous le nœud `HKEY_LOCAL_MACHINE` permet à tous les utilisateurs de voir les assemblys à l’emplacement spécifié dans la boîte de dialogue **Ajouter une référence**. La création de la clé de Registre sous le nœud `HKEY_CURRENT_USER` affecte uniquement le paramètre de l’utilisateur actuel.

  Rouvrez la boîte de dialogue **Ajouter une référence**. Les assemblys doivent apparaître sous l’onglet **.net** . Si ce n’est pas le cas, assurez-vous que les assemblys se trouvent dans le répertoire *AssemblyLocation* spécifié, redémarrez Visual Studio, puis réessayez.

## <a name="projects-tab"></a>Onglet Projets

L’onglet **Projets** liste tous les projets compatibles de la solution actuelle, sous le sous-onglet **Solution**.

Un projet peut référencer un autre projet qui cible une version différente du framework. Par exemple, vous pouvez créer un projet qui cible .NET Framework 4, mais qui référence un assembly qui a créé pour .NET Framework 2. Cependant, le projet .NET Framework 2 ne peut pas référencer un projet .NET Framework 4. Pour plus d’informations, consultez [Vue d’ensemble du ciblage des frameworks](../ide/visual-studio-multi-targeting-overview.md).

> [!NOTE]
> Un projet qui cible le .NET Framework 4 est incompatible avec un projet qui cible le profil de client du .NET Framework 4.

## <a name="shared-projects-tab"></a>Onglet Projets partagés

Ajoutez une référence à un projet partagé sous l’onglet **Projets partagés** de la boîte de dialogue Gestionnaire de références. Les [projets partagés](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) vous permettent d’écrire du code commun référencé par plusieurs projets d’application.

## <a name="universal-windows-tab"></a>Onglet Windows universel

L’onglet **Windows universel** liste tous les SDK spécifiques aux plateformes sur lesquelles des systèmes d’exploitation Windows s’exécutent.
Cet onglet comporte deux sous-groupes : **Core** et **Extensions**.

### <a name="core-subgroup"></a>Sous-groupe Principal

Les projets d’application Windows universelles ont une référence au SDK Windows universel par défaut. Ainsi, le sous-groupe **Principal** du **Gestionnaire de références** n’énumère pas les assemblys du SDK Windows universel.

### <a name="extensions-subgroup"></a>Sous-groupe Extensions

**Extensions** répertorie les kits de développement logiciel (SDK) utilisateur qui étendent la plateforme Windows ciblée.

Un kit SDK est une collection de fichiers que Visual Studio traite comme un seul composant. Sous l’onglet **Extensions** , les kits de développement logiciel (SDK) qui s’appliquent au projet à partir duquel la boîte de dialogue Gestionnaire de références a été appelée sont répertoriés en tant qu’entrées uniques. Une fois ajouté à un projet, tout le contenu du kit SDK est utilisé par Visual Studio afin que l’utilisateur n’ait rien d’autre à faire pour l’exploiter dans IntelliSense, la boîte à outils, les concepteurs, l’Explorateur d’objets, la création, le déploiement, le débogage et l’empaquetage.

Pour plus d’informations sur l’affichage de votre SDK sous l’onglet **Extensions** , consultez [création d’un kit de développement logiciel](../extensibility/creating-a-software-development-kit.md)(SDK).

> [!NOTE]
> Si un projet référence un SDK qui dépend d’un autre SDK, Visual Studio n’utilise pas le second SDK, sauf si vous ajoutez manuellement une référence à celui-ci. Quand un utilisateur choisit un SDK sous l’onglet **Extensions**, la boîte de dialogue Gestionnaire de références l’aide à identifier les dépendances du SDK en les listant dans le volet d’informations.

Si un type de projet ne prend pas en charge les extensions, cet onglet n’apparaît pas dans la boîte de dialogue Gestionnaire de références.

## <a name="com-tab"></a>Onglet COM

L’onglet **com** répertorie tous les composants COM pouvant être référencés. Si vous souhaitez ajouter une référence à une DLL COM inscrite qui contient un manifeste interne, annulez d'abord l'inscription de la DLL. Sinon, Visual Studio ajoute la référence d’assembly en tant que contrôle ActiveX, et non en tant que DLL native.

Si un type de projet ne prend pas en charge COM, l’onglet ne s’affiche pas dans la boîte de dialogue Gestionnaire de références.

## <a name="browse"></a>Parcourir

Vous pouvez utiliser le bouton **Parcourir** pour rechercher un composant dans le système de fichiers.

Un projet peut référencer un composant qui cible une version différente du framework. Par exemple, vous pouvez créer une application qui cible .NET Framework 4.7, mais qui référence un composant ciblant .NET Framework 4. Pour plus d’informations, consultez [Vue d’ensemble du ciblage des frameworks](../ide/visual-studio-multi-targeting-overview.md).

Évitez d’ajouter des références de fichier aux sorties d’un autre projet de la même solution, car cela risquerait de provoquer des erreurs de compilation. Utilisez plutôt l’onglet **Solution** de la boîte de dialogue Gestionnaire de références afin de créer des références entre projets. Cela facilite le développement en équipe, en permettant une meilleure gestion des bibliothèques de classes créées dans vos projets. Pour plus d’informations, consultez [Dépanner des références rompues](../ide/troubleshooting-broken-references.md).

Vous ne pouvez pas accéder à un kit SDK et l’ajouter à votre projet. Vous pouvez uniquement rechercher un fichier (par exemple un assembly ou un fichier *.winmd*) et l’ajouter à votre projet.

Lors d’une référence de fichier à un WinMD, la disposition attendue est que les fichiers *\<FileName> . WinMD*, *\<FileName>.dll* et *\<FileName> . pri* sont placés les uns à côté des autres. Si vous référencez un fichier WinMD dans les scénarios suivants, un ensemble incomplet de fichiers est copié dans le répertoire de sortie du projet et, par conséquent, des erreurs de rendu et d'exécution se produisent.

- **Composant natif** : un projet natif crée un fichier WinMD pour chaque ensemble d’espaces de noms disjoint et une DLL qui contient l’implémentation. Les WinMD auront des noms disparates. En référençant ce fichier de composant natif, MSBuild ne détecte pas que les WinMD nommés différemment constituent un même composant. Par conséquent, seuls les *\<FileName>.dll* et *\<FileName> . winmd* portant le même nom seront copiés, et des erreurs d’exécution se produiront. Pour contourner ce problème, créez un kit SDK d’extension. Pour plus d’informations, consultez [Créer un kit SDK](../extensibility/creating-a-software-development-kit.md).

- **Consommation de contrôles** : au minimum, un contrôle XAML se compose d’un fichier *\<FileName>.winmd*, *\<FileName>.dll*, *\<FileName>.pri*, *\<XamlName>.xaml* et *\<ImageName>.jpg*. Lorsque le projet est généré, les fichiers de ressources associés à la référence de fichier ne sont pas copiés dans le répertoire de sortie du projet, et seuls les fichiers *\<FileName> . winmd*, *\<FileName>.dll* et *\<FileName> . pri* sont copiés. Une erreur de build est journalisée pour informer l’utilisateur que les ressources *\<XamlName> . xaml* et *\<ImageName>.jpg* sont manquantes. Pour que l'opération réussisse, l'utilisateur doit copier manuellement les fichiers de ressources dans le répertoire de sortie du projet pour la génération et le débogage/l'exécution. Pour contourner ce problème, créez un kit SDK d’extension en suivant les étapes décrites dans [Créer un kit SDK](../extensibility/creating-a-software-development-kit.md), ou modifiez le fichier projet pour ajouter la propriété suivante :

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Si vous ajoutez la propriété, la build peut s'exécuter plus lentement.

## <a name="recent"></a>Récent

Les **assemblys**, **com**, **Windows** et **Parcourir** prennent tous en charge un onglet **récent** , qui énumère la liste des composants récemment ajoutés aux projets.

## <a name="search"></a>Recherche

La barre de recherche de la boîte de dialogue Gestionnaire de références fonctionne sur l’onglet actif. Par exemple, si un utilisateur tape « System » dans la barre de recherche alors que l’onglet **Solution** est actif, la recherche ne renvoie aucun résultat à moins que la solution soit composée d’un nom de projet contenant « System ».

## <a name="see-also"></a>Voir aussi

- [Gérer les références dans un projet](../ide/managing-references-in-a-project.md)
