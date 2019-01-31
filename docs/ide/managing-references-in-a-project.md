---
title: Gérer les références dans un projet
ms.date: 04/11/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3612e3b04fc27460922f90e48666397ce9fb3b73
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042984"
---
# <a name="manage-references-in-a-project"></a>Gérer les références dans un projet

Avant d’écrire du code pour un composant externe ou un service connecté, vous devez d’abord inclure une référence à celui-ci dans votre projet. Une référence est essentiellement une entrée dans un fichier projet qui contient les informations dont Visual Studio a besoin pour localiser le composant ou le service.

Pour ajouter une référence, cliquez avec le bouton droit sur le nœud **Références** ou **Dépendances** dans l’**Explorateur de solutions**, puis choisissez **Ajouter une référence**. Vous pouvez également cliquer avec le bouton droit sur le nœud de projet, et sélectionner **Ajouter** > **Référence**. Pour plus d'informations, voir [Procédure : Ajouter ou supprimer des références](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

![Ajouter une référence en Visual C&#43;&#43;](../ide/media/vs2015_cpp_add_reference.png)

Vous pouvez ajouter une référence aux types de composant et service suivants :

- Bibliothèques de classes ou assemblys du .NET Framework

- Applications UWP

- Composants COM

- Autres assemblys ou bibliothèques de classes de projets dans la même solution

- Services web XML

## <a name="uwp-app-references"></a>Références d’applications UWP

### <a name="project-references"></a>Références de projets

Les projets de plateforme Windows universelle (UWP) peuvent créer des références à d’autres projets UWP dans la solution ou à des projets ou fichiers binaires Windows 8.1, à condition que ces projets n’utilisent pas des API dépréciées dans Windows 10. Pour plus d’informations, consultez [Passer de Windows Runtime 8 à la plateforme Windows universelle](/windows/uwp/porting/w8x-to-uwp-root).

Si vous choisissez de recibler les projets Windows 8.1 vers Windows 10, consultez [Porter, migrer et mettre à niveau des projets Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

### <a name="extension-sdk-references"></a>Références du kit SDK d’extension

Les applications de plateforme Windows universelle (UWP) Visual Basic, C#, C++ et JavaScript peuvent référencer des SDK d’extension qui ciblent Windows 8.1, à condition que ces SDK d’extension n’utilisent pas des API dépréciées dans Windows 10. Vérifiez auprès du site du fournisseur de SDK d’extension s’ils peuvent être référencés par des applications UWP.

Si vous constatez que le SDK d’extension référencé par votre application n’est pas pris en charge, vous devez effectuer les étapes suivantes :

1. Recherchez le nom du projet qui provoque l’erreur. La plateforme ciblée par votre projet est indiquée entre parenthèses en regard du nom du projet. Par exemple, **NomDeMonProjet (Windows 8.1)** signifie que votre projet **NomDeMonProjet** cible la version de plateforme Windows 8.1.

1. Accédez au site du fournisseur propriétaire du SDK d’extension non pris en charge et installez la version de celui dont les dépendances sont compatibles avec la version de la plateforme ciblée par votre projet.

    > [!NOTE]
    > L’une des manières de vérifier si un SDK d’extension a des dépendances vis-à-vis d’autres SDK d’extension consiste à regarder dans le **Gestionnaire de références**. Redémarrez Visual Studio, créez un projet d’application UWP C#, puis cliquez avec le bouton droit sur le projet et choisissez **Ajouter une référence**. Accédez à l’onglet **Windows** et au sous-onglet **Extensions**, puis sélectionnez le SDK d’extension. Examinez le volet droit dans le **Gestionnaire de références**. S’il possède des dépendances, elles y sont répertoriées.

    > [!IMPORTANT]
    > Si votre projet cible Windows 10 et que le SDK d’extension installé au cours de l’étape précédente a une dépendance vis-à-vis de Microsoft Visual C++ Runtime Package, la version de Microsoft Visual C++ Runtime Package compatible avec Windows 10 est la version 14.0 et est installée avec Visual Studio.

1. Si le SDK d’extension que vous avez installé au cours de l’étape précédente a des dépendances vis-à-vis d’autres SDK d’extension, accédez aux sites des fournisseurs qui ont des dépendances et installez les versions de ces dépendances qui sont compatibles avec la version de la plateforme ciblée par votre projet.

1. Redémarrez Visual Studio et ouvrez votre application.

1. Cliquez avec le bouton droit sur le nœud **Références** ou **Dépendances** dans le projet ayant déclenché l’erreur, puis choisissez **Ajouter une référence**.

1. Cliquez sur l’onglet **Windows**, sur le sous-onglet **Extensions**, décochez les cases des anciens SDK d’extension, puis cochez les cases des nouveaux. Cliquez sur **OK**.

## <a name="add-a-reference-at-design-time"></a>Ajouter une référence au moment du design

Quand vous référencez un assembly dans votre projet, Visual Studio recherche cet assembly aux emplacements suivants :

- Le répertoire de projet actuel (vous pouvez rechercher ces assemblys via l’onglet **Parcourir** ).

- Autres répertoires de projet de la même solution (vous pouvez rechercher ces assemblys sous l’onglet **Projets** ).

> [!NOTE]
> - Tous les projets contiennent une référence implicite à **mscorlib**.
> - Tous les projets contiennent une référence implicite à `System.Core`, même si `System.Core` est supprimé de la liste de références.
> - Les projets Visual Basic contiennent une référence implicite à <xref:Microsoft.VisualBasic>.

## <a name="references-to-shared-components-at-run-time"></a>Références à des composants partagés au moment de l’exécution

Au moment de l’exécution, les composants doivent se trouver dans le chemin de sortie du projet ou dans le Global Assembly Cache (GAC). Si le projet contient une référence à un objet qui ne se trouve pas à l’un de ces emplacements, vous devez copier la référence au chemin de sortie du projet quand vous générez ce dernier. La propriété <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> indique si cette copie doit être effectuée. Si la valeur est **True**, la référence est copiée dans le répertoire du projet quand vous générez le projet. Si la valeur est **False**, la référence n’est pas copiée.

Si vous déployez une application qui contient une référence à un composant personnalisé inscrit dans le GAC, ce composant ne sera pas déployé avec l’application, quelle que soit la valeur du paramètre <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> . Dans les versions antérieures de Visual Studio, vous pouviez définir la propriété <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> sur une référence pour vous assurer que l’assembly a été déployé. À présent, vous devez ajouter manuellement l’assembly au dossier \Bin. Cela permet de placer tout le code personnalisé sous surveillance et de réduire le risque de publication d’un code personnalisé qui ne vous est pas familier.

Par défaut, la propriété <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> a la valeur **False** si l’assembly ou le composant se trouve dans le Global Assembly Cache ou s’il correspond à un composant d’infrastructure. Sinon, la valeur est **True**. Les références entre projets ont toujours la valeur **True**.

## <a name="reference-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Référencer un projet ou un assembly qui cible une autre version du .NET Framework

Vous pouvez créer des applications qui référencent des projets ou des assemblys ciblant une version différente du .NET Framework. Par exemple, vous pouvez créer une application qui cible .NET Framework 4.6, qui référence un assembly ciblant .NET Framework 4.5. Si vous créez un projet qui cible une version antérieure du .NET Framework, vous ne pouvez pas définir dans ce projet une référence à un projet ou un assembly ciblant une version plus récente.

Pour plus d’informations, consultez [Vue d’ensemble du multiciblage](../ide/visual-studio-multi-targeting-overview.md).

## <a name="project-to-project-references"></a>Références entre projets

Les références entre projets sont des références à des projets qui contiennent des assemblys. Vous les créez en utilisant l’onglet **Projet** . Visual Studio peut trouver un assembly si vous indiquez un chemin d’accès au projet.

Quand vous avez un projet qui produit un assembly, vous devez référencer le projet et non pas utiliser une référence de fichier (voir ci-dessous). Une référence entre projets présente l’avantage de créer une dépendance entre les projets dans le système de build. Le projet dépendant est généré s’il a été modifié depuis la dernière build du projet qui référence. Une référence de fichier ne crée pas de dépendance de build, il est donc possible de générer le projet de référence sans générer le projet dépendant, et la référence peut devenir obsolète. Autrement dit, le projet peut référencer une version précédemment générée du projet. Cela peut entraîner la présence de plusieurs versions d’une même DLL nécessaire dans le répertoire *bin*, ce qui n’est pas admis. Quand ce conflit intervient, vous obtenez un message de ce type : « Avertissement : impossible de copier la dépendance ’fichier’ du projet ’projet’ dans le répertoire d’exécution, car elle remplacerait la référence ’fichier’. ». Pour plus d’informations, consultez [Dépanner des références rompues](../ide/troubleshooting-broken-references.md) et [Guide pratique pour créer et supprimer les dépendances d’un projet](../ide/how-to-create-and-remove-project-dependencies.md).

> [!NOTE]
> Une référence de fichier est créée à la place d’une référence entre projets si la version cible du .NET Framework d’un projet est la version 4.5, et si la version cible du .NET Framework de l’autre projet est la version 2, 3, 3.5 ou 4.0.

## <a name="file-references"></a>Références de fichiers

Les références de fichiers sont des références directes à des assemblys qui se trouvent hors du contexte d’un projet Visual Studio. Vous les créez en utilisant l’onglet **Parcourir** du **Gestionnaire de références**. Utilisez une référence de fichier quand vous avez seulement un assembly ou un composant, et pas le projet qui le crée comme sortie.

## <a name="see-also"></a>Voir aussi

- [Dépanner des références rompues](../ide/troubleshooting-broken-references.md)
- [Guide pratique pour ajouter ou supprimer des références](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
