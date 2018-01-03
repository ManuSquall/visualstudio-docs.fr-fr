---
title: "Choisir des éléments de boîte à outils, Composants WPF | Microsoft Docs"
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bd9959d6883eec10f048733d3119206cc5dea3bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="choose-toolbox-items-wpf-components"></a>Choisir des éléments de boîte à outils, Composants WPF
Cet onglet de la boîte de dialogue **Choisir des éléments de boîte à outils** affiche la liste des contrôles Windows Presentation Foundation (WPF) disponibles sur votre ordinateur local. Pour afficher la liste, sélectionnez **Choisir des éléments de boîte à outils** dans le menu **Outils** pour afficher la boîte de dialogue **Choisir des éléments de boîte à outils**, puis sélectionnez l’onglet **Composants WPF**. Pour trier la liste des composants, cliquez sur un en-tête de colonne.  

-   Lorsque la case en regard d’un composant est cochée, une icône de ce composant s’affiche dans la **boîte à outils**.  

    > [!TIP]
    >  Pour ajouter une instance d’un contrôle WPF à un document de projet ouvert pour modification, faites glisser son icône de **boîte à outils** vers le mode Création. Le balisage et le code par défaut du composant sont insérés dans votre projet, prêts à être modifiés. Pour plus d’informations, consultez [Utilisation de la boîte à outils](../../ide/using-the-toolbox.md).  

-   Lorsque la case en regard d’un composant est décochée, l’icône correspondante est retirée de la **boîte à outils**.  

    > [!NOTE]
    >  Les composants .NET Framework installés sur votre ordinateur restent disponibles, même si leurs icônes ne s’affichent pas dans la **boîte à outils**.  

Les colonnes de l’onglet **Composants WPF** contient les informations suivantes :  

Name  
Répertorie les noms des contrôles WPF dont les entrées correspondantes se trouvent dans le Registre de votre ordinateur.  

Espace de noms  
Affiche la hiérarchie de l’espace de noms de l’[API de classe .NET Framework](/dotnet/api/?view=netframework-4.7) qui définit la structure du composant. Triez cette colonne pour répertorier les composants disponibles dans chaque espace de noms .NET Framework installé sur votre ordinateur.  

Nom de l'assembly  
Affiche le nom de l’assembly .NET Framework qui comprend l’espace de noms de chaque composant. Triez cette colonne pour répertorier les espaces de noms contenus dans chaque assembly .NET Framework installé sur votre ordinateur.  

Répertoire  
Affiche l’emplacement de l’assembly .NET Framework. L'emplacement par défaut de tous les assemblys est le Global Assembly Cache. Pour plus d’informations sur le Global Assembly Cache, consultez [Utilisation d’assemblys et du Global Assembly Cache](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac).  

## <a name="uielement-list"></a>Liste des éléments d’interface  
**Filtrer**  
Filtre la liste des contrôles WPF en fonction de la chaîne que vous entrez dans la zone de texte. Toutes les correspondances des quatre colonnes sont affichées.  

**Effacer**  
Efface la chaîne de filtrage.  

**Parcourir**  
Ouvre la boîte de dialogue **Ouvrir** qui permet d’accéder aux assemblys contenant des contrôles WPF. Utilisez cette boîte de dialogue pour charger les assemblys qui ne se trouvent pas dans le Global Assembly Cache.  

**Language**  
Affiche la langue localisée de l’assembly qui contient le contrôle WPF sélectionné.  

## <a name="limitations"></a>Limitations  
L’ajout d’un contrôle personnalisé ou d’un <xref:System.Windows.Controls.UserControl> à la boîte à outils présente les limitations suivantes :  

-   Cela fonctionne uniquement pour les contrôles personnalisés définis en dehors du projet actuel.  

-   Cela ne permet pas une mise à jour correcte lorsque vous passez d’une configuration de solution Debug à une configuration Release, et inversement. Cela est dû au fait que la référence n’est pas une référence de projet, mais une référence à l’assembly sur disque. Si le contrôle fait partie de la solution actuelle, lorsque vous passez de Debug à Release, votre projet continue à référencer la version Debug du contrôle.  

En outre, si les métadonnées au moment du design sont appliquées au contrôle personnalisé et si ces métadonnées spécifient que <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> a la valeur `false`, le contrôle n’apparaît pas dans la boîte à outils.  

Vous pouvez référencer directement vos contrôles dans la vue XAML en mappant l’espace de noms et l’assembly de votre contrôle.  

## <a name="see-also"></a>Voir aussi  
[Boîte à outils](../../ide/reference/toolbox.md)  
[Prise en main de WPF](../../designers/getting-started-with-wpf.md)
