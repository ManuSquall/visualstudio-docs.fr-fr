---
title: "Guide pratique pour ajouter ou supprimer des références à l’aide du gestionnaire de références | Microsoft Docs"
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.ReferenceManager
helpviewer_keywords:
- Visual C# projects, references
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
ms.assetid: 1aabb520-99b0-46c6-9368-21b4d84793eb
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3c5e414ab56641171e9d3f5cddf758b6a13a6458
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Guide pratique pour ajouter ou supprimer des références à l’aide du gestionnaire de références
Vous pouvez utiliser la boîte de dialogue **Gestionnaire de références** pour ajouter et gérer des références aux composants développés par vous, par Microsoft ou par une autre société. Si vous développez une application Windows universelle, votre projet référence automatiquement toutes les DLL correctes du kit SDK Windows. Si vous développez une application .NET, votre projet référence automatiquement mscorlib.dll. Certaines API .NET sont exposées dans des composants que vous devez ajouter manuellement. Les références à des composants COM ou à des composants personnalisés doivent être ajoutées manuellement.  

## <a name="adding-and-removing-a-reference"></a>Ajout et suppression d'une référence  

#### <a name="to-add-a-reference"></a>Pour ajouter une référence  

1.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud Références et sélectionnez **Ajouter une référence**.  

2.  Spécifiez les références à ajouter, puis choisissez le bouton **OK**.  

 Le **Gestionnaire de références** s’ouvre et affiche la liste des références disponibles par groupe. Le type de projet détermine quel groupe parmi les suivants s'affiche :  

-   Assemblys, avec les sous-groupes Framework et Extensions.  

-   Solution, avec le sous-groupe Projets.  

-   Windows, avec les sous-groupes Principal et Extensions. Vous pouvez explorer les références dans le SDK Windows ou les SDK de l’extension à l’aide de l’**Explorateur d’objets**.  

-   Parcourir, avec le sous-groupe Récent.  

## <a name="assemblies-tab"></a>Onglet Assemblys  
 L’onglet **Assemblys** répertorie tous les assemblys .NET Framework qui sont disponibles pour le référencement. L’onglet **Assemblys** ne répertorie pas les assemblys du Global Assembly Cache (GAC), car ceux-ci appartiennent à l’environnement d’exécution. Si vous déployez ou copiez une application qui contient une référence à un assembly enregistré dans le GAC, cet assembly ne sera ni déployé ni copié avec l’application, quelle que soit la valeur du paramètre Copie locale. Pour plus d’informations, consultez [Gestion des références dans un projet](../ide/managing-references-in-a-project.md).  

 Lorsque vous ajoutez manuellement une référence à l'un des espaces de noms EnvDTE (EnvDTE, EnvDTE80, EnvDTE90, EnvDTE90a ou EnvDTE100), attribuez la valeur False à la propriété Incorporer les types interop, dans la fenêtre Propriétés. Si cette propriété a la valeur True, des problèmes de génération peuvent survenir car certaines propriétés EnvDTE ne peuvent pas être incorporées.  

 Tous les projets du Bureau contiennent une référence implicite à mscorlib. Les projets [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] contiennent une référence implicite à Microsoft.VisualBasic. Dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], tous les projets contiennent une référence implicite à System.Core, même s’il est supprimé de la liste des références.  

 Si un type de projet ne prend pas en charge les assemblys, l’onglet ne s’affiche pas dans la boîte de dialogue **Gestionnaire de références**.  

 L'onglet Assemblys comprend deux sous-onglets :  

1.  Framework : répertorie tous les assemblys qui constituent le Framework ciblé.  

    -   Les assemblys publiés se trouvent dans le Framework complet et sont énumérés dans la liste de Framework lorsque votre projet cible un profil de Framework ciblé. Les assemblys sont publiés en gris pour les différencier de ceux qui existent dans le profil de Framework ciblé du projet. Par exemple, si un projet cible le client .NET Framework 4, la liste Framework indique les assemblys publiés à partir de .NET Framework 4. Quand un utilisateur ajoute un assembly publié, cet utilisateur est averti qu’une fois la boîte de dialogue **Gestionnaire de références** fermée le projet sera reciblé vers .NET Framework 4 et l’assembly publié sera ajouté.  

    -   Les projets pour les applications [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] contiennent des références à tous les assemblys du [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] ciblé par défaut sur la création de projet. Dans les projets managés, un nœud en lecture seule dans le dossier Références de l’**Explorateur de solutions** indique la référence au Framework complet. Par conséquent, l’onglet Framework n’énumère pas les assemblys à partir du Framework et affiche à la place le message suivant : « Tous les assemblys .NET Framework sont déjà référencés. Utilisez l’Explorateur d’objets pour explorer les références dans le Framework. ». Pour les projets d'application de bureau, l'onglet Framework énumère les assemblys du .NET Framework ciblé. Par ailleurs, l'utilisateur doit ajouter les références nécessaires à l'application.  

2.  Les extensions répertorient tous les assemblys que les fournisseurs externes de composants et les contrôles ont développés pour étendre le Framework ciblé. Selon l'objectif de l'application utilisateur, ces assemblys peuvent être nécessaires.  

    -   Les extensions sont remplies en énumérant les assemblys stockés dans les emplacements suivants :  

        ```  
        32-bit machine:  
        HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        64-bit machine:  
        HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        And older versions of the [Target Framework Identifier]  
        ```  

         Par exemple, si un projet cible le .NET Framework 4 sur un ordinateur 32 bits, les extensions énumèrent les assemblys qui sont stockés dans \Microsoft\\.NETFramework\v4.0\AssemblyFoldersEx\\, \Microsoft\\.NETFramework\v3.5\AssemblyFoldersEx\\, \Microsoft\\.NETFramework\v3.0\AssemblyFoldersEx\\ et \Microsoft\\.NETFramework\v2.0\AssemblyFoldersEx\\.  

 Certains composants dans la liste peuvent ne pas être indiqués, selon la version [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de votre projet. Cela peut se produire dans les conditions suivantes :  

-   Un composant qui utilise une version récente du .NET Framework est incompatible avec un projet qui cible une version antérieure du .NET Framework.  

     Pour plus d’informations sur le changement de la version cible du .NET Framework pour un projet, consultez [Guide pratique pour cibler une version du .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  

-   Un composant qui utilise le [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] est incompatible avec un projet qui cible le [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)].  

     Lorsque vous créez une application, certains projets ciblent le [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] par défaut.  

-   Évitez si possible d'ajouter des références de fichier aux sorties d'un autre projet de la même solution, car cela risquerait de provoquer des erreurs de compilation. Utilisez l’onglet **Projets** de la boîte de dialogue **Ajouter une référence** afin de créer des références entre projets. Cela facilite le développement en équipe, en permettant une meilleure gestion des bibliothèques de classes créées dans vos projets. Pour plus d’informations, consultez [Dépannage de références rompues](../ide/troubleshooting-broken-references.md).  

-   > [!NOTE]
    >  Dans Visual Studio 2015 ou version ultérieure, une référence de fichier est créée au lieu d’une référence de projet si la version cible du .NET Framework d’un projet est la version 4.5 ou ultérieure et que la version cible du de l’autre projet est 2, 3, 3.5 ou 4.0.  

#### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Pour afficher un assembly dans la boîte de dialogue Ajouter une référence  

-   Déplacez ou copiez l'assembly vers l'un des emplacements suivants :  

    -   Le répertoire de projet actuel (vous pouvez rechercher ces assemblys via l’onglet **Parcourir** ).  

    -   Autres répertoires de projet de la même solution (vous pouvez rechercher ces assemblys à l’aide de l’onglet **Projets**)  

     \- ou -  

-   Définissez une clé de Registre qui spécifie l'emplacement des assemblys à afficher :  

     Sur un système d'exploitation 32 bits, ajoutez l'une des clés de Registre suivantes :  

    -   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"  

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"  

     Sur un système d'exploitation 64 bits, ajoutez l'une des clés de Registre suivantes dans une ruche du Registre 32 bits  :  

    -   [HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"  

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"  

     *VersionMinimum* représente la version la plus ancienne de .NET Framework qui peut être utilisée. Si *VersionMinimum* a la valeur v3.0, les dossiers spécifiés dans AssemblyFoldersEx s’appliquent aux projets qui ciblent .NET Framework 3.0 et les versions ultérieures.  

     *AssemblyLocation* désigne le répertoire des assemblys que vous souhaitez afficher dans la boîte de dialogue **Ajouter une référence** (par exemple, C:\MyAssemblies\\).  

     Créer la clé de Registre sous le nœud HKEY_LOCAL_MACHINE permet à tous les utilisateurs de voir les assemblys à l’emplacement spécifié dans la boîte de dialogue **Ajouter une référence**. Créer la clé de Registre sous le nœud HKEY_CURRENT_USER affecte uniquement le paramètre pour l'utilisateur actuel.  

     Rouvrez la boîte de dialogue **Ajouter une référence**. Les assemblys doivent apparaître sous l’onglet **.NET**. Si ce n’est pas le cas, vérifiez que les assemblys se trouvent dans le répertoire *AssemblyLocation* spécifié, redémarrez Visual Studio, puis réessayez.  

## <a name="com-tab"></a>Onglet COM  
 L'onglet COM répertorie tous les composants COM pouvant être référencés. Si vous souhaitez ajouter une référence à une DLL COM inscrite qui contient un manifeste interne, annulez d'abord l'inscription de la DLL. Sinon, Visual Studio ajoute la référence d'assembly comme contrôle ActiveX, et non comme DLL native.  

 Si un type de projet ne prend pas en charge COM, l’onglet ne s’affiche pas dans la boîte de dialogue **Gestionnaire de références**.  

## <a name="solution-tab"></a>Onglet Solution  
 L'onglet Solution répertorie tous les projets compatibles dans la solution actuelle, dans le sous-onglet Projets.  

 Un projet peut faire référence à un autre projet qui cible une version différente du .NET Framework. Par exemple, vous pouvez créer un projet qui cible [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] mais qui référence un assembly qui est généré pour .NET Framework 2. Toutefois, le projet .NET Framework 2 ne peut pas référencer un projet [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]. Pour plus d’informations, consultez [Ciblage d’une version spécifique du .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  

 Un projet qui cible le [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] est incompatible avec un projet qui cible le [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].  

 Dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], une référence de fichier est créée au lieu d'une référence de projet si un projet cible du .NET Framework d'un projet est 4 et si la version cible du .NET Framework de l'autre projet est antérieure.  

 Un projet qui cible [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] ne peut pas ajouter de référence de projet à un projet qui cible le .NET Framework et vice versa.  

## <a name="windows-tab"></a>Onglet Windows  
 L’onglet Windows liste tous les kits SDK qui sont spécifiques aux plateformes sur lesquelles s’exécutent les systèmes d'exploitation Windows.  

 Vous pouvez générer un fichier WinMD dans Visual Studio de deux façons :  

-   **Projets managés d’application [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]** : les projets d’application [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] peuvent générer les binaires de WinMD en définissant Propriétés de projet &#124; Type de sortie = fichier WinMD. Le nom de fichier WinMD doit être l'espace de noms du sur-ensemble de tous les espaces de noms qui existent dans celui-ci. Par exemple, si un projet comprend des espaces de noms A.B et A.B.C, les étiquettes possibles pour le WinMD généré sont A.winmd et A.B.winmd. Si un utilisateur entre une valeur Propriétés de projet &#124; Nom d’assembly ou Propriétés de projet &#124; Espace de noms qui est disjointe de l’ensemble d’espaces de noms du projet, ou s’il n’y a aucun espace de noms de sur-ensemble dans un projet, un avertissement de génération est créé : « A.winmd » n’est pas un nom de fichier .winmd valide pour cet assembly. Tous les types compris dans un fichier de métadonnées Windows doivent se trouver dans un sous-espace de noms du nom du fichier. Les types qui n’existent pas dans un sous espace de noms du nom de fichier ne peuvent pas être localisés lors de l’exécution. Dans cet assembly, le plus petit espace de noms courant est « CSWSClassLibrary1 ». Un projet Visual Basic ou Visual C# de bureau peut uniquement consommer des WinMD générés à l’aide des kits SDK [!INCLUDE[win8](../debugger/includes/win8_md.md)] (appelés WinMD internes) et ne peut pas générer de WinMD.  

-   **Projets d’application au format natif [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]** : un fichier WinMD natif comprend uniquement des métadonnées. Son implémentation existe dans un fichier DLL distinct. Il est possible de produire des binaires natifs en choisissant le modèle de projet Composant Windows Runtime dans la boîte de dialogue **Nouveau projet** ou en partant d’un projet vide et en modifiant les propriétés du projet pour générer un fichier WinMD. Si le projet se compose d'espaces de noms disjoints, une erreur de build indique à l'utilisateur de combiner les espaces de noms ou d'exécuter l'outil MSMerge.  

 L'onglet Windows comprend deux sous-groupes.  

### <a name="core-subgroup"></a>Sous-groupe Principal  
 Le sous-groupe Principal répertorie tous les WinMDs (pour les éléments Windows Runtime) dans le kit SDK de la version Windows ciblée.  

 Les projets d'application [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] contiennent des références à tous les WinMDs du kit SDK [!INCLUDE[win8](../debugger/includes/win8_md.md)] par défaut sur la création de projet. Dans les projets managés, un nœud en lecture seule dans le dossier Références de l’**Explorateur de solutions** indique la référence au SDK [!INCLUDE[win8](../debugger/includes/win8_md.md)] complet. Par conséquent, le sous-groupe Principal du Gestionnaire de références n’énumère pas les assemblys du kit SDK [!INCLUDE[win8](../debugger/includes/win8_md.md)] et affiche à la place le message : « Le Kit de développement logiciel Windows est déjà référencé. Utilisez l’Explorateur d’objets pour explorer les références dans le SDK Windows. ».  

 Dans les projets de bureau, le sous-groupe Principal ne s’affiche pas par défaut. Vous pouvez ajouter le Windows Runtime en ouvrant le menu contextuel du nœud du projet, en choisissant **Décharger le projet**, en ajoutant l’extrait de code suivant, et en rouvrant le projet (sur le nœud du projet, choisissez **Recharger le projet**). Quand vous appelez la boîte de dialogue**Gestionnaire de références**, le sous-groupe Principal s’affiche.  

```  
<PropertyGroup>  
  <TargetPlatformVersion>8.0</TargetPlatformVersion>  
</PropertyGroup>  
```  

 Cochez bien la case **Windows** sur ce sous-groupe. Vous devriez ensuite pouvoir utiliser les éléments Windows Runtime. Toutefois, vous voudrez également ajouter System.Runtime, dans lequel Windows Runtime définit des classes et des interfaces standard, telles que IEnumerable, qui sont utilisées dans toutes les bibliothèques Windows Runtime. Pour plus d’informations sur l’ajout du System.Runtime, consultez [Applications du Bureau managées et Windows Runtime](http://msdn.microsoft.com/library/windows/apps/jj856306.aspx#consuming_standard_windows_runtime_types).  

### <a name="extensions-subgroup"></a>Sous-groupe Extensions  
 Les extensions indiquent les Kits de développement logiciel utilisateur qui étendent la plateforme Windows ciblée. Cet onglet apparaît pour les projets d'application [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] uniquement. Les projets de bureau n’indiquent pas cet onglet car ils peuvent consommer uniquement des fichiers .winmd internes.  

 Un kit SDK est une collection de fichiers que Visual Studio traite comme un seul composant. Sous l’onglet Extensions, les SDK qui s’appliquent au projet à partir duquel la boîte de dialogue **Gestionnaire de références** a été appelée sont répertoriés sous forme d’entrées uniques. Une fois ajouté à un projet, tout le contenu du kit SDK est utilisé par Visual Studio afin que l’utilisateur n’ait rien d’autre à faire pour l’exploiter dans IntelliSense, la boîte à outils, les concepteurs, l’Explorateur d’objets, la création, le déploiement, le débogage et l’empaquetage. Pour plus d’informations sur l’affichage du SDK sous l’onglet Extensions, consultez [Création d’un SDK](../extensibility/creating-a-software-development-kit.md).  

> [!NOTE]
>  Si un projet référence un kit SDK qui dépend d’un autre kit SDK, Visual Studio n’utilise pas le second kit à moins que l’utilisateur ajoute manuellement une référence à celui-ci. Quand un utilisateur choisit un SDK sous l’onglet **Extensions**, la boîte de dialogue **Gestionnaire de références** l’aide à identifier les dépendances du SDK en répertoriant non seulement le nom et la version du SDK, mais également le nom de toutes les dépendances du SDK dans le volet d’informations. Si un utilisateur ne remarque pas les dépendances et ajoute uniquement ce kit SDK, MSBuild l’invite à ajouter les dépendances.  

 Si un type de projet ne prend pas en charge les **extensions**, l’onglet ne s’affiche pas dans la boîte de dialogue **Gestionnaire de références**.  

## <a name="browse-button"></a>Bouton Parcourir  
 Vous pouvez utiliser le bouton **Parcourir** pour rechercher un composant dans le système de fichiers.  

 Un projet peut faire référence à un composant qui cible une version différente du .NET Framework. Par exemple, vous pouvez créer une application qui cible le .NET Framework 4 Client Profile, qui référence un composant qui cible le .NET Framework 2. Pour plus d’informations, consultez [Ciblage d’une version spécifique du .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  

 Évitez, si possible, d'ajouter des références de fichier aux sorties d'un autre projet de la même solution, car cela risquerait de provoquer des erreurs de compilation. Utilisez plutôt l’onglet **Solution** de la boîte de dialogue **Gestionnaire de références** afin de créer des références entre projets. Cela facilite le développement en équipe, en permettant une meilleure gestion des bibliothèques de classes créées dans vos projets. Pour plus d’informations, consultez [Dépannage de références rompues](../ide/troubleshooting-broken-references.md).  

 Vous ne pouvez pas accéder à un kit SDK et l’ajouter à votre projet. Vous pouvez uniquement rechercher un fichier (par exemple, un assembly ou un fichier .winmd) et l'ajouter à votre projet.  

 Quand vous effectuez une référence de fichier pour un fichier WinMD, la disposition attendue est la suivante : les fichiers *nom_fichier*.winmd, *nom_fichier*.dll et *nom_fichier*.pri sont placés les uns aux côtés des autres. Si vous référencez un fichier WinMD dans les scénarios suivants, un ensemble incomplet de fichiers est copié dans le répertoire de sortie du projet et, par conséquent, des erreurs de rendu et d'exécution se produisent.  

-   **Composant natif** : un projet natif crée un fichier WinMD pour chaque ensemble d’espaces de noms disjoint et une DLL qui contient l’implémentation. Les WinMD auront des noms disparates. En référençant ce fichier de composant natif, MSBuild ne détecte pas que les WinMD nommés différemment constituent un même composant. Ainsi, seuls les fichiers *nom_fichier*.dll et *nom_fichier*.winmd portant le même nom sont copiés, et des erreurs d’exécution se produisent. Pour contourner ce problème, créez un kit SDK d’extension. Pour plus d’informations, consultez [Création d’un SDK](../extensibility/creating-a-software-development-kit.md).  

-   **Utilisation de contrôles** : au minimum, un contrôle XAML comprend un fichier *nom_fichier*.winmd, *nom_fichier*.dll, *nom_fichier*.pri, *nom_xaml*.xaml et *nom_image*.jpg. Quand le projet est généré, les fichiers de ressources associés à la référence de fichier ne sont pas copiés dans le répertoire de sortie du projet. Seuls les fichiers *nom_fichier*.winmd, *nom_fichier*.dll et *nom_fichier*.pri sont copiés. Une erreur de build est journalisée pour indiquer à l’utilisateur que les ressources *nom_xaml*.xaml et *nom_image*.jpg sont manquantes. Pour que l'opération réussisse, l'utilisateur doit copier manuellement les fichiers de ressources dans le répertoire de sortie du projet pour la génération et le débogage/l'exécution. Pour contourner ce problème, créez un SDK de l’extension en suivant les étapes décrites dans [Création d’un SDK](../extensibility/creating-a-software-development-kit.md), ou modifiez le fichier projet pour ajouter la propriété suivante :  

    ```  
    <PropertyGroup>  
    <GenerateLibraryOutput>True</GenerateLibraryOutput>  
    </PropertyGroup>  
    ```  

    > [!NOTE]
    >  Si vous ajoutez la propriété, la build peut s'exécuter plus lentement.  

## <a name="recent"></a>Récent  
 Les boutons Assemblys, COM, Windows et Parcourir prennent tous en charge un onglet Récent, qui énumère la liste des composants qui ont été récemment ajoutés aux projets.  

## <a name="search"></a>Rechercher  
 La barre de recherche de la boîte de dialogue **Gestionnaire de références** fonctionne sur l’onglet actif. Par exemple, si un utilisateur tape « System » dans la barre de recherche alors que l’onglet **Solution** est actif, la recherche ne renvoie aucun résultat à moins que la solution soit composée d’un nom de projet contenant « System ».  

## <a name="see-also"></a>Voir aussi  
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)
