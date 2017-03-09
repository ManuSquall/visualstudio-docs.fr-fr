---
title: "Gestion des références dans un projet | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- Visual C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
ms.assetid: 05d1c51b-44f3-4973-8a11-6c919b08ad62
caps.latest.revision: 54
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 4b82b8583ec54af9eee383255d20b40674e7c2c1
ms.lasthandoff: 02/22/2017

---
# <a name="managing-references-in-a-project"></a>Gestion des références dans un projet
Avant d’écrire du code pour un composant externe ou un service connecté, vous devez d’abord inclure une référence à celui-ci dans votre projet. Une référence est essentiellement une entrée dans un fichier projet qui contient les informations dont Visual Studio a besoin pour localiser le composant ou le service.  

 Pour ajouter une référence, cliquez avec le bouton droit sur le nœud Références dans l’Explorateur de solutions et choisissez **Ajouter une référence**. Pour plus d’informations, consultez [Guide pratique pour ajouter ou supprimer des références à l’aide du gestionnaire de références](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).  

 ![Ajouter une référence dans Visual C&#43;&#43;](../ide/media/vs2015_cpp_add_reference.png "vs2015_cpp_add_reference")  

 Vous pouvez créer une référence aux types de composant/service suivants :  

-   Références pour applications du Windows Store  

-   Bibliothèques de classes ou assemblys du .NET Framework  

-   Composants COM  

-   Autres assemblys ou bibliothèques de classes de projets dans la même solution  

-   Services web XML  

## <a name="windows-store-app-references"></a>Références pour applications du Windows Store  

### <a name="project-references"></a>Références de projets  
 Les projets d'applications de plateforme Windows universelle qui ciblent Windows 10 peuvent créer des références à d'autres projets de plateforme Windows universelle dans la solution, ou à des projets ou des fichiers binaires du Windows Store qui ciblent [!INCLUDE[win81](../debugger/includes/win81_md.md)], à condition que ces projets n'utilisent pas d’API qui ont été dépréciées dans Windows 10. Pour plus d’informations, consultez [Passer de Windows Runtime 8 à la plateforme Windows universelle](https://msdn.microsoft.com/en-us/library/windows/apps/dn954974.aspx).  

 Si vous choisissez de recibler des projets [!INCLUDE[win81](../debugger/includes/win81_md.md)] sur Windows 10, consultez [Portage, migration et mise à niveau des projets Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)  

### <a name="extension-sdk-references"></a>Références des kits SDK d’extension  
 Les projets du Windows Store Visual Basic, C#, C++  et JavaScript qui ciblent la plateforme Windows universelle peuvent référencer des kits SDK d’extension qui ciblent [!INCLUDE[win81](../debugger/includes/win81_md.md)], à condition que ces kits n’utilisent pas les API dépréciées dans Windows 10. Vérifiez sur le site du fournisseur de SDK d’extension si les kits peuvent être référencés par des projets du Windows Store qui ciblent la plateforme Windows universelle.  

 Si vous constatez que le SDK d’extension référencé par votre application n’est pas pris en charge, vous devez effectuer les étapes suivantes :  

1.  Recherchez le nom du projet qui provoque l’erreur. La plateforme ciblée par votre projet est indiquée entre parenthèses en regard du nom du projet. Par exemple, **NomDeMonProjet (Windows 8.1)** signifie que votre projet **NomDeMonProjet** cible la version de plateforme [!INCLUDE[win81](../debugger/includes/win81_md.md)].  

2.  Accédez au site du fournisseur propriétaire du SDK d’extension non pris en charge et installez la version de celui dont les dépendances sont compatibles avec la version de la plateforme ciblée par votre projet.  

    > [!NOTE]
    >  Pour savoir si un SDK d’extension a des dépendances vis-à-vis d’autres SDK d’extension, redémarrez Visual Studio, créez un projet du Windows Store C#, cliquez avec le bouton droit sur le projet et choisissez **Ajouter une référence**, accédez à l’onglet **Windows**, accédez au sous-onglet **Extensions**, sélectionnez le SDK d’extension et regardez le volet droit du **Gestionnaire de références**. S’il possède des dépendances, elles y sont répertoriées.  

    > [!IMPORTANT]
    >  Si votre projet cible Windows 10 et que le SDK d’extension installé au cours de l’étape précédente a une dépendance vis-à-vis de Microsoft Visual C++ Runtime Package, la version de Microsoft Visual C++ Runtime Package compatible avec Windows 10 est v14.0 et est installée avec Visual Studio.  

3.  Si le SDK d’extension que vous avez installé au cours de l’étape précédente a des dépendances vis-à-vis d’autres SDK d’extension, accédez au(x) site(s) du ou des fournisseurs qui ont des dépendances et installez les versions de ces dépendances qui sont compatibles avec la version de la plateforme ciblée par votre projet.  

4.  Redémarrez Visual Studio et ouvrez votre application.  

5.  Cliquez avec le bouton droit sur le nœud **Références** dans le projet qui a provoqué l’erreur, puis choisissez **Ajouter une référence**  

6.  Cliquez sur l’onglet **Windows** , sur le sous-onglet **Extensions** , décochez les cases des anciens SDK d’extension, puis cochez les cases des nouveaux. Cliquez sur **OK**.  

## <a name="adding-a-reference-at-design-time"></a>Ajout d’une référence au moment de la conception  
 Quand vous référencez un assembly dans votre projet, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] recherche cet assembly dans les emplacements suivants :  

-   Le répertoire de projet actuel (vous pouvez rechercher ces assemblys via l’onglet **Parcourir** ).  

-   Autres répertoires de projet de la même solution (vous pouvez rechercher ces assemblys sous l’onglet **Projets** ).  

> [!NOTE]
>  Tous les projets contiennent une référence implicite à mscorlib. Les projets Visual Basic contiennent une référence implicite à `Microsoft.VisualBasic`.  
>   
>  Tous les projets dans Visual Studio contiennent une référence implicite à `System.Core`, même si `System.Core` est supprimé de la liste des références.  

## <a name="references-to-shared-components-at-run-time"></a>Références à des composants partagés au moment de l’exécution  
 Au moment de l’exécution, les composants doivent se trouver dans le chemin de sortie du projet ou dans le Global Assembly Cache (GAC). Si le projet contient une référence à un objet qui ne se trouve pas à l’un de ces emplacements, vous devez copier la référence au chemin de sortie du projet quand vous générez ce dernier. La propriété <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> indique si cette copie doit être effectuée. Si la valeur est **True**, la référence est copiée dans le répertoire du projet quand vous générez le projet. Si la valeur est **False**, la référence n’est pas copiée.  

 Si vous déployez une application qui contient une référence à un composant personnalisé inscrit dans le GAC, ce composant ne sera pas déployé avec l’application, quelle que soit la valeur du paramètre <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A>. Dans les versions antérieures de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pouviez définir la propriété <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> sur une référence pour vous assurer que l’assembly était bien déployé. À présent, vous devez ajouter manuellement l’assembly au dossier \Bin. Cela permet de placer tout le code personnalisé sous surveillance et de réduire le risque de publication d’un code personnalisé qui ne vous est pas familier.  

 Par défaut, la propriété <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> a la valeur **False** si l’assembly ou le composant se trouve dans le Global Assembly Cache ou s’il correspond à un composant de framework. Sinon, la valeur est **True**. Les références entre projets ont toujours la valeur **True**.  

## <a name="referencing-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Référence à un projet ou un assembly qui cible une autre version du .NET Framework  
 Vous pouvez créer des applications qui référencent des projets ou des assemblys ciblant une version différente du .NET Framework. Par exemple, vous pouvez créer une application ciblant [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] qui référence un assembly ciblant [!INCLUDE[dnprdnext](../ide/includes/dnprdnext_md.md)]. Si vous créez un projet ciblant une version antérieure du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], vous ne pouvez pas définir une référence à un projet ou à un assembly qui cible le [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] ou le .NET Framework version 4 dans ce projet.  

 Pour plus d’informations, consultez [Ciblage d’une version spécifique du .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  

## <a name="project-to-project-references"></a>Références entre projets  
 Les références entre projets sont des références à des projets qui contiennent des assemblys. Vous les créez en utilisant l’onglet **Projet** . Visual Studio peut trouver un assembly si vous indiquez un chemin d’accès au projet.  

 Quand vous avez un projet qui produit un assembly, vous devez référencer le projet et non pas utiliser une référence de fichier (voir ci-dessous). Une référence entre projets présente l’avantage de créer une dépendance entre les projets dans le système de build. Le projet dépendant est généré s’il a été modifié depuis la dernière build du projet qui référence. Une référence de fichier ne crée pas de dépendance de build, il est donc possible de générer le projet de référence sans générer le projet dépendant, et la référence peut devenir obsolète. Autrement dit, le projet peut référencer une version précédemment générée du projet. Cela peut entraîner la présence de plusieurs versions d’une même DLL nécessaire dans le répertoire bin, ce qui n’est pas admis. Quand ce conflit intervient, vous obtenez un message de ce type : [Avertissement : impossible de copier la dépendance 'fichier' du projet 'projet' dans le répertoire d’exécution, car elle remplacerait la référence 'fichier'](../misc/warning-the-dependency-file-in-project-project-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-file.md). Pour plus d’informations, consultez [Dépannage de références rompues](../ide/troubleshooting-broken-references.md) et [Guide pratique pour créer et supprimer les dépendances d’un projet](../ide/how-to-create-and-remove-project-dependencies.md).  

> [!NOTE]
>  Une référence de fichier est créée à la place d’une référence entre projets si la version cible du .NET Framework d’un projet est la version 4.5, et si la version cible du .NET Framework de l’autre projet est la version 2, 3, 3.5 ou 4.0.  

## <a name="file-references"></a>Références de fichier  
 Les références de fichier sont des références directes à des assemblys qui se trouvent hors du contexte d’un projet Visual Studio. Vous les créez en utilisant l’onglet **Parcourir** de la boîte de dialogue **Gestionnaire de références**. Utilisez une référence de fichier quand vous avez seulement un assembly ou un composant et que vous n’avez pas le projet qui le crée comme sortie.  

## <a name="see-also"></a>Voir aussi  
 [Dépannage de références rompues](../ide/troubleshooting-broken-references.md)   
 [Guide pratique pour ajouter ou supprimer des références à l’aide du gestionnaire de références](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)

