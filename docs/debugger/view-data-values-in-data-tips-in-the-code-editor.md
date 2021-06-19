---
title: Afficher les valeurs des variables dans les DataTips | Microsoft Docs
description: Utilisez les DataTips pour afficher facilement des informations sur les variables, y compris les tableaux et les structures, pendant le débogage. Vous pouvez également modifier les valeurs.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a84c3379c04799aa1faea5b0e62afe0ef1aa11e9
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386473"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Afficher les valeurs de données dans les DataTips dans l’éditeur de code

Les DataTips sont un moyen pratique de visualiser des informations sur les variables de votre programme au cours du débogage. Les DataTips ne fonctionnent qu'en mode arrêt, et uniquement avec les variables comprises dans la portée d'exécution actuelle. S’il s’agit de la première fois que vous essayez de déboguer du code, vous souhaiterez peut-être lire le [débogage pour les débutants](../debugger/debugging-absolute-beginners.md) et les [techniques de débogage et les outils de débogage](../debugger/write-better-code-with-visual-studio.md) avant de passer en revue cet article.

## <a name="work-with-datatips"></a>Utiliser les DataTips

Les DataTips s’affichent uniquement en mode arrêt et uniquement sur les variables qui se trouvent dans la portée d’exécution actuelle.

### <a name="display-a-datatip"></a>Afficher un DataTip

1. Définissez un point d’arrêt dans votre code et démarrez le débogage en appuyant sur **F5** ou **en sélectionnant déboguer**  >  **Démarrer le débogage**.

1. Lorsqu’elle est suspendue au point d’arrêt, placez le curseur sur une variable de l’étendue actuelle. Un DataTip apparaît, affichant le nom et la valeur actuelle de la variable.

### <a name="make-a-datatip-transparent"></a>Rendre un DataTip transparent

Pour rendre un DataTip transparent pour voir le code qui se trouve en dessous, dans le DataTip, appuyez sur **CTRL**. Le DataTip reste transparent tant que vous maintenez la touche **CTRL** enfoncée. Cela ne fonctionne pas pour les DataTips épinglés ou flottants.
### <a name="pin-a-datatip"></a>Épingler un DataTip

Pour épingler un DataTip afin qu’il reste ouvert, sélectionnez l’icône **Épingler à la source** .

![Épingler un DataTip](../debugger/media/dbg-tips-data-tips-pinned.png "Épingler un DataTip")

Vous pouvez déplacer un DataTip épinglé en le faisant glisser dans la fenêtre de code. Une icône en punaise apparaît dans la reliure en regard de la ligne à laquelle le DataTip est épinglé.

>[!NOTE]
>Les DataTips sont toujours évalués dans le contexte où l’exécution est suspendue, et non l’emplacement actuel du curseur ou du DataTip. Si vous pointez sur une variable dans une autre fonction qui porte le même nom qu’une variable dans le contexte actuel, la valeur de la variable dans le contexte actuel est affichée.

### <a name="unpin-a-datatip-from-source"></a>Détacher un DataTip de la source

Pour détacher un DataTip épinglé, pointez sur le DataTip et sélectionnez l’icône de punaise dans le menu contextuel.

L’icône en forme de punaise passe à la position désépinglée et le DataTip flotte à présent ou peut être glissé au-dessus de toutes les fenêtres ouvertes. Les DataTips flottants se ferment lorsque la session de débogage se termine.

### <a name="repin-a-datatip"></a>Réépingler un DataTip

Pour réépingler un DataTip flottant à la source, pointez dessus dans l’éditeur de code, puis sélectionnez l’icône en punaise. L’icône en forme de punaise passe à la position épinglée et le DataTip est de nouveau épinglé uniquement à la fenêtre de code.

Si un DataTip flotte sur une fenêtre de code non source, l’icône de punaise n’est pas disponible et le DataTip ne peut pas être réépinglé. Pour accéder à l’icône de punaise, retournez le DataTip à la fenêtre de l’éditeur de code en le faisant glisser ou en donnant le focus à la fenêtre de code.

### <a name="close-a-datatip"></a>Fermer un DataTip

Pour fermer un DataTip, pointez sur le DataTip et sélectionnez l’icône Fermer (**x**) dans le menu contextuel.

### <a name="close-all-datatips"></a>Fermer tous les DataTips

Pour fermer tous les DataTips, dans le menu **Déboguer** , sélectionnez **Effacer tous les DataTips**.

### <a name="close-all-datatips-for-a-specific-file"></a>Fermer tous les DataTips pour un fichier spécifique

Pour fermer tous les DataTips d’un fichier spécifique, dans le menu **Déboguer** , sélectionnez **Effacer tous \<Filename> les DataTips épinglés à**.

## <a name="expand-and-edit-information"></a>Développer et modifier des informations
Vous pouvez utiliser les DataTips pour développer un tableau, une structure ou un objet afin d’en afficher les membres. Vous pouvez également modifier la valeur d'une variable depuis un DataTip.

### <a name="expand-a-variable"></a>Développer une variable

Pour développer un objet dans un DataTip et afficher ses éléments, pointez sur les flèches de développement avant les noms d’éléments pour afficher les éléments sous forme d’arborescence. Pour un DataTip épinglé, sélectionnez **+** avant le nom de la variable, puis développez l’arborescence.

![Développer un DataTip](../debugger/media/dbg-tour-data-tips.png "Développer un DataTip")

Vous pouvez utiliser la souris ou les touches de direction du clavier pour vous déplacer vers le haut et vers le bas de la vue développée.

Vous pouvez également épingler des éléments développés au DataTip épinglé en pointant dessus et en sélectionnant leurs icônes de punaise. Les éléments apparaissent alors dans le DataTip épinglé une fois l’arborescence réduite.

### <a name="edit-the-value-of-a-variable"></a>Modifier la valeur d’une variable

Pour modifier la valeur d’une variable ou d’un élément dans un DataTip, sélectionnez la valeur, tapez une nouvelle valeur, puis appuyez sur **entrée**. La sélection est désactivée pour les valeurs en lecture seule.

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips"></a>Épingler les propriétés dans les DataTips

> [!NOTE]
> Cette fonctionnalité est prise en charge pour .NET Core 3,0 ou version ultérieure.

Vous pouvez inspecter rapidement des objets en fonction de leurs propriétés dans DataTips avec l’outil **Propriétés regroupement** .  Pour utiliser cet outil, pointez sur une propriété et sélectionnez l’icône d’épingle qui s’affiche ou cliquez avec le bouton droit et sélectionnez l’option **épingler le membre en tant que favori** dans le menu contextuel résultant.  Cette propriété est propagée vers le haut de la liste de propriétés de l’objet, et le nom et la valeur de la propriété s’affichent dans la colonne de droite du DataTip.  Pour désépingler une propriété, sélectionnez à nouveau l’icône d’épingle ou sélectionnez l’option **détacher le membre en tant que favori** dans le menu contextuel.

![Épinglage d’une propriété dans un DataTip](../debugger/media/basic-pin-datatip.gif "Épinglage d’une propriété dans un DataTip")

Vous pouvez également activer/désactiver les noms de propriété et exclure les propriétés non épinglées lors de l’affichage de la liste de propriétés de l’objet dans un DataTip.  Vous pouvez accéder à l’une ou l’autre des options en cliquant avec le bouton droit sur une ligne contenant une propriété et en sélectionnant l’option **afficher uniquement les membres épinglés** ou **Masquer les noms de membres épinglés dans les valeurs** du menu contextuel.

::: moniker-end

## <a name="visualize-complex-data-types"></a>Visualiser les types de données complexes

Une icône de loupe située en regard d’une variable ou d’un élément dans un DataTip signifie qu’un ou plusieurs [visualiseurs](../debugger/create-custom-visualizers-of-data.md), tels que le [visualiseur de texte](../debugger/string-visualizer-dialog-box.md), sont disponibles pour la variable. Les visualiseurs affichent les informations d’une manière plus explicite, parfois graphique.

Pour afficher l’élément à l’aide du visualiseur par défaut pour le type de données, sélectionnez l' ![icône](../debugger/media/dbg-tips-visualizer-icon.png "Icône de visualiseur")représentant une icône de loupe. Sélectionnez la flèche en regard de l’icône de loupe pour effectuer une sélection dans une liste de visualiseurs pour le type de données.

## <a name="add-a-variable-to-a-watch-window"></a>Ajouter une variable à un Fenêtre Espion

Si vous souhaitez continuer à regarder une variable, vous pouvez l’ajouter à une fenêtre **Espion** à partir d’un DataTip. Cliquez avec le bouton droit sur la variable dans le DataTip, puis sélectionnez **Ajouter un espion**.

La variable s’affiche dans la fenêtre **Espion** . Si votre édition de Visual Studio prend en charge plusieurs fenêtres **Espion** , la variable apparaît dans **Watch 1**.

## <a name="import-and-export-datatips"></a>Importer et exporter des DataTips

Vous pouvez exporter des DataTips vers un fichier XML, que vous pouvez partager ou modifier à l’aide d’un éditeur de texte. Vous pouvez également importer un fichier XML DataTip que vous avez reçu ou modifié.

**Pour exporter les DataTips :**

1. Sélectionnez **Déboguer**  >  **Exporter les DataTips**.

1. Dans la boîte de dialogue **Exporter les DataTips** , accédez à l’emplacement d’enregistrement du fichier XML, tapez un nom pour le fichier, puis sélectionnez **Enregistrer**.

**Pour importer des DataTips :**

1. Sélectionnez **Déboguer**  >  **Importer les DataTips**.

1. Dans la boîte de dialogue **Importer les DataTips** , sélectionnez le fichier XML DataTips que vous souhaitez ouvrir, puis sélectionnez **ouvrir**.

## <a name="see-also"></a>Voir aussi
- [Qu’est-ce que le débogage ?](../debugger/what-is-debugging.md)
- [Techniques et outils de débogage](../debugger/write-better-code-with-visual-studio.md)
- [Premier aperçu du débogage](../debugger/debugger-feature-tour.md)
- [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)
- [Espion et Espion express, fenêtres](../debugger/watch-and-quickwatch-windows.md)
- [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)
