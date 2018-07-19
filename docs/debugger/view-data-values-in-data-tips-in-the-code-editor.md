---
title: Afficher les valeurs de données dans les DataTips dans l’éditeur de code | Documents Microsoft
ms.custom: ''
ms.date: 07/14/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b260cd8a4cd102683c4342d5f199102660cfbe90
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477327"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Affichage des valeurs de données dans les DataTips dans l’éditeur de code
Les DataTips sont un moyen pratique de visualiser des informations sur les variables de votre programme au cours du débogage. Les DataTips ne fonctionnent qu'en mode arrêt, et uniquement avec les variables comprises dans la portée d'exécution actuelle.
  
### <a name="to-display-a-datatip"></a>Pour afficher un DataTip  
  
1. Définir un point d’arrêt et démarrer le débogage (appuyez sur **F5**).

2. Où est suspendu dans le débogueur, placez le pointeur de la souris sur n’importe quelle variable dans la portée actuelle.
  
     Un DataTip apparaît.
  
3.  Le DataTip disparaît lorsque vous retirez le pointeur de la souris. Pour épingler un DataTip afin qu’il reste ouvert, cliquez sur le **épingler à la source** icône ou avec le bouton droit sur une variable, puis cliquez sur **épingler à la source**.

    ![L’épinglage d’une info-bulle](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

    > [!NOTE]
    > Les conseils relatifs aux données sont toujours évalués dans le contexte où l'exécution est interrompue, et non pas lorsque le curseur pointe un élément. Si vous pointez sur une variable dans une autre fonction portant le même nom qu'une variable qui est dans le contexte actuel, la variable dans l'autre fonction est affichée comme la valeur de la variable dans le contexte actuel.
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Pour détacher un DataTip et le rendre flottant  
  
-   Dans un DataTip épinglé, cliquez sur le **détacher de la source** icône.  
  
     L'icône d'épingle reprend sa position détachée. Le DataTip flotte à présent au-dessus de toutes les fenêtres actives. Le DataTip flottant se ferme à la fin de la session de débogage.  
  
### <a name="to-repin-a-floating-datatip"></a>Pour réépingler un DataTip flottant  
  
-   Dans un DataTip, cliquez sur l'icône d'épingle.  
  
     L'icône d'épingle reprend sa position épinglée. Si le DataTip se trouve à l'extérieur d'une fenêtre source, l'icône d'épingle est désactivée et le DataTip ne peut pas être épinglé.  
  
### <a name="to-close-a-datatip"></a>Pour fermer un DataTip  
  
-   Placez le pointeur de la souris sur un DataTip, puis cliquez sur le **fermer** icône.  
  
### <a name="to-close-all-datatips"></a>Pour fermer tous les DataTips  
  
-   Sur le **déboguer** menu, cliquez sur **effacer tous les DataTips**.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Pour fermer tous les DataTips d'un fichier spécifique  
  
-   Sur le **déboguer** menu, cliquez sur **effacer tous les DataTips épinglés à** *fichier*.  
  
## <a name="expand-and-edit-information"></a>Développer et modifier les informations  
 Vous pouvez utiliser les DataTips pour développer un tableau, une structure ou un objet afin d’en afficher les membres. Vous pouvez également modifier la valeur d'une variable depuis un DataTip.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Développer une variable pour voir ses éléments  
  
-   Dans un DataTip, placez le pointeur de la souris sur le **+** signe qui précède le nom de variable.  
  
    La variable se développe et affiche ses éléments sous forme d’arborescence.

    ![Afficher une info-bulle](../debugger/media/dbg-tour-data-tips.gif "afficher une info-bulle")
  
    Une fois la variable développée, vous pouvez utiliser les touches de direction du clavier pour vous déplacer vers le haut ou vers le bas. Vous pouvez également utiliser la souris.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>Pour modifier la valeur d'une variable à l'aide d'un DataTip  
  
1.  Dans un DataTip, cliquez sur la valeur. Cette possibilité est désactivée pour les valeurs en lecture seule.  
  
2.  Tapez une nouvelle valeur et appuyez sur ENTRÉE.  
  
## <a name="making-a-datatip-transparent"></a>Rendre un DataTip transparent  
 Si vous souhaitez visualiser le code masqué par un DataTip, vous pouvez rendre celui-ci temporairement transparent. Cela ne s'applique pas aux DataTips épinglés ou flottants.  
  
#### <a name="to-make-a-datatip-transparent"></a>Pour rendre un DataTip transparent  
  
-   Dans un DataTip, appuyez sur CTRL.  
  
     Le DataTip reste transparent tant que vous maintenez la touche CTRL enfoncée.  
  
## <a name="visualize-complex-data-types"></a>Visualiser les types de données complexes  
 Si une icône de loupe apparaît en regard d’un nom de variable dans un DataTip, un ou plusieurs [visualiseurs](../debugger/create-custom-visualizers-of-data.md), telles que la [chaîne visualiseurs](../debugger/string-visualizer-dialog-box.md), sont disponibles pour les variables de ce type de données. Les visualiseurs servent à afficher les informations de façon plus explicite (en général graphique).
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Voir le contenu d'une variable à l'aide d'un visualiseur  
  
-   Cliquez sur l’icône de loupe ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icône de visualiseur") pour sélectionner le visualiseur par défaut pour le type de données.  
  
     - ou -  
  
     Cliquez sur la flèche contextuelle à côté du visualiseur pour choisir dans une liste le visualiseur approprié pour ce type de données.  
  
     Un visualiseur apparaît et affiche les informations.  
  
## <a name="add-information-to-a-watch-window"></a>Ajouter des informations dans une fenêtre Espion  
 Si vous souhaitez continuer à surveiller une variable dans un affichage de liste, vous pouvez ajouter la variable à la **espion** fenêtre à partir d’un DataTip.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>Ajouter une variable à la fenêtre Espion  
  
-   Cliquez sur un DataTip, puis cliquez sur **ajouter un espion**.  
  
     La variable est ajoutée à la **espion** fenêtre. Si vous utilisez une édition qui prend en charge plusieurs **espion** windows, la variable est ajoutée à **Espion 1.**  
  
## <a name="import-and-export-datatips"></a>Importer et exporter des DataTips  
 Vous pouvez exporter des DataTips vers un fichier XML, qui peut être partagé avec un collègue ou modifié à l'aide d'un éditeur de texte.  
  
#### <a name="to-export-datatips"></a>Pour exporter des DataTips  
  
1.  Dans le menu Déboguer, cliquez sur **exporter les DataTips**.  
  
     Le **exporter les DataTips** boîte de dialogue s’affiche.  
  
2.  Utilisez les techniques standard pour naviguer jusqu'à l’emplacement où vous souhaitez enregistrer le fichier XML, tapez un nom pour le fichier dans le **nom de fichier** zone, puis cliquez sur **OK**.  
  
#### <a name="to-import-datatips"></a>Pour importer des DataTips  
  
1.  Dans le menu Déboguer, cliquez sur **importer les DataTips**.  
  
     Le **importer les DataTips** boîte de dialogue s’affiche.  
  
2.  Utilisez la boîte de dialogue pour rechercher le fichier XML que vous souhaitez ouvrir et cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Espion et Espion express, fenêtres](../debugger/watch-and-quickwatch-windows.md)   
 [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)   