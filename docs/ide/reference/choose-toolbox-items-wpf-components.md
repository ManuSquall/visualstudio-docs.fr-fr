---
title: Choisir des éléments de boîte à outils, Composants WPF
description: Découvrez comment utiliser l’onglet Composants WPF pour afficher les contrôles Windows Presentation Foundation disponibles sur votre ordinateur local.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d23418cd784b9e0b7c916c1e5629a6da012b9d0b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836395"
---
# <a name="choose-toolbox-items-wpf-components"></a>Choisir des éléments de boîte à outils, composants WPF

Cet onglet de la boîte de dialogue **Choisir des éléments de boîte à outils** affiche la liste des contrôles Windows Presentation Foundation (WPF) disponibles sur votre ordinateur local. Pour afficher cette liste, sélectionnez **choisir des éléments de boîte à outils** dans le menu **Outils** pour afficher la boîte de dialogue choisir des **éléments de boîte à outils** , puis sélectionnez l’onglet **Composants WPF** . Pour trier les composants listés, sélectionnez n’importe quel en-tête de colonne.

- Lorsque la case en regard d’un composant est cochée, une icône de ce composant s’affiche dans la **boîte à outils**.

    > [!TIP]
    > Pour ajouter un contrôle WPF à un document de projet ouvert pour modification, faites glisser son icône de **boîte à outils** vers le mode Création. Le balisage et le code par défaut du composant sont insérés dans votre projet, prêts à être modifiés. Pour plus d'informations, consultez [Boîte à outils](../../ide/reference/toolbox.md).

- Lorsque la case en regard d’un composant est décochée, l’icône correspondante est retirée de **Boîte à outils**.

    > [!NOTE]
    > Les composants .NET installés sur votre ordinateur restent disponibles, que leurs icônes s’affichent ou non dans la **boîte à outils**.

Les colonnes de l’onglet **Composants WPF** contient les informations suivantes :

**Nom**

Répertorie les noms des contrôles WPF dont les entrées correspondantes se trouvent dans le Registre de votre ordinateur.

**Espace de noms**

Affiche la hiérarchie de l’espace de noms de l’[API .NET](/dotnet/api/?view=netframework-4.7&preserve-view=true) qui définit la structure du composant. Triez sur cette colonne pour lister les composants disponibles dans chaque espace de noms .NET installé sur votre ordinateur.

**Nom de l’assembly**

Affiche le nom de l’assembly .NET qui comprend l’espace de noms de chaque composant. Triez sur cette colonne pour lister les espaces de noms contenus dans chaque assembly .NET installé sur votre ordinateur.

**Directory**

Affiche l’emplacement de l’assembly .NET. L'emplacement par défaut de tous les assemblys est le Global Assembly Cache. Pour plus d’informations sur le Global Assembly Cache, consultez [Utilisation d’assemblys et du Global Assembly Cache](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac).

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

### <a name="filter"></a>Filtrer

Filtre la liste des contrôles WPF en fonction de la chaîne que vous entrez dans la zone de texte. Toutes les correspondances des quatre colonnes sont affichées.

**Effacer**

Efface la chaîne de filtrage.

**Parcourir**

Ouvre la boîte de dialogue **Ouvrir** qui permet d’accéder aux assemblys contenant des contrôles WPF. Utilisez cette boîte de dialogue pour charger les assemblys qui ne se trouvent pas dans le Global Assembly Cache.

**Langage**

Affiche la langue localisée de l’assembly qui contient le contrôle WPF sélectionné.

## <a name="limitations"></a>Limites

L’ajout d’un contrôle personnalisé ou d’un <xref:System.Windows.Controls.UserControl> à la boîte à outils présente les limitations suivantes :

- Cela fonctionne uniquement pour les contrôles personnalisés définis en dehors du projet actuel.

- Cela ne permet pas une mise à jour correcte lorsque vous passez d’une configuration de solution Debug à une configuration Release, et inversement. Cela est dû au fait que la référence n’est pas une référence de projet, mais une référence à l’assembly sur disque. Si le contrôle fait partie de la solution actuelle, lorsque vous passez de Debug à Release, votre projet continue à référencer la version Debug du contrôle.

En outre, si les métadonnées au moment du design sont appliquées au contrôle personnalisé et si ces métadonnées spécifient que [Microsoft.Windows.Design.ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) est défini sur `false`, le contrôle n’apparaît pas dans la boîte à outils.

Vous pouvez référencer directement vos contrôles dans la vue XAML en mappant l’espace de noms et l’assembly de votre contrôle.

## <a name="see-also"></a>Voir aussi

- [Boîte à outils](../../ide/reference/toolbox.md)
- [Bien démarrer avec WPF](../../designers/getting-started-with-wpf.md)
