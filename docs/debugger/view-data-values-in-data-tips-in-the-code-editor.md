---
title: Afficher les valeurs de données dans DataTips dans l’éditeur de code | Microsoft Docs
ms.custom: ''
ms.date: 11/21/2018
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
ms.openlocfilehash: 4156ff8f81e7a011aeff0cf753af60bb3d6cd924
ms.sourcegitcommit: a811f6a194ccd40d844e74e618d847df87c85c16
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2018
ms.locfileid: "52621537"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Afficher les valeurs de données dans DataTips dans l’éditeur de code

Les DataTips sont un moyen pratique de visualiser des informations sur les variables de votre programme au cours du débogage. Les DataTips ne fonctionnent qu'en mode arrêt, et uniquement avec les variables comprises dans la portée d'exécution actuelle. S’il s’agit de la première fois que vous avez essayé de déboguer du code, il pouvez que vous souhaitez lire [corriger les bogues en écrivant mieux C# code](../debugger/write-better-code-with-visual-studio.md) et [débogage pour les débutants](../debugger/debugging-absolute-beginners.md) avant de poursuivre cet article.

S’il s’agit de la première fois que le débogage, il pouvez que vous souhaitez lire [écrire de meilleures C# code à l’aide de Visual Studio](../debugger/write-better-code-with-visual-studio.md) et [débogage pour les débutants](../debugger/debugging-absolute-beginners.md) avant de lire cet article.
  
## <a name="work-with-datatips"></a>Utiliser des DataTips

Les DataTips apparaissent uniquement en mode arrêt et uniquement sur des variables qui se trouvent dans la portée en cours d’exécution.

### <a name="display-a-datatip"></a>Afficher un DataTip  
  
1. Définissez un point d’arrêt dans votre code et démarrez le débogage en appuyant sur **F5** ou en sélectionnant **déboguer** > **démarrer le débogage**.
  
1. Cas de suspension au point d’arrêt, placez le curseur sur une variable quelconque dans la portée actuelle. Un DataTip apparaît, affichant le nom et la valeur actuelle de la variable.

### <a name="make-a-datatip-transparent"></a>Rendre un DataTip transparent  

Pour rendre un DataTip transparent pour afficher le code qui est situé en dessous, tandis que dans le DataTip, appuyez sur **Ctrl**. Le DataTip reste transparent tant que vous maintenez le **Ctrl** clé. Cela ne fonctionne pas pour les DataTips épinglés ou flottants.  
### <a name="pin-a-datatip"></a>Épingler un DataTip

Pour épingler un DataTip afin qu’elle reste ouverte, sélectionnez la punaise **épingler à la source** icône. 

![Épingler un DataTip](../debugger/media/dbg-tips-data-tips-pinned.png "épingler un DataTip")

Vous pouvez déplacer un DataTip épinglé en le faisant glisser autour de la fenêtre de code. Une icône de punaise apparaît dans la marge à côté de la ligne à que le DataTip est épinglé. 

>[!NOTE]
>Les DataTips sont toujours évalués dans le contexte où l’exécution est suspendue, pas le curseur actuel ou l’emplacement du DataTip. Si vous pointez sur une variable dans une autre fonction qui a le même nom qu’une variable dans le contexte actuel, la valeur de la variable dans le contexte actuel s’affiche.
  
### <a name="unpin-a-datatip-from-source"></a>Détacher un DataTip à partir de la source

Pour détacher un DataTip épinglé, pointez sur le DataTip, puis sélectionnez l’icône de punaise dans le menu contextuel. 

L’icône de punaise passe à reprend sa position, et le DataTip flotte maintenant ou peut être déplacé au-dessus de toutes les fenêtres. Les DataTips flottants fermer lorsque la session de débogage se termine.  
  
### <a name="repin-a-datatip"></a>Réépingler un DataTip  
  
Pour réépingler un DataTip flottant à source, placez le curseur dessus dans l’éditeur de code, puis sélectionnez l’icône de punaise. L’icône de punaise change sa position épinglée, et le DataTip est épinglé à nouveau uniquement dans la fenêtre de code. 

Si un DataTip flotte au-dessus d’une fenêtre de code non source, l’icône de punaise n’est pas disponible, et le DataTip ne peut pas être réépinglé. Pour accéder à l’icône de punaise, retourner le DataTip à la fenêtre d’éditeur de code en faisant glisser ou en donnant le focus de la fenêtre de code. 
  
### <a name="close-a-datatip"></a>Fermer un DataTip  
  
Pour fermer un DataTip, placez le curseur sur le DataTip, puis sélectionnez la fermeture (**x**) icône dans le menu contextuel.  
  
### <a name="close-all-datatips"></a>Fermer tous les DataTips  
  
Pour fermer tous les DataTips, sur le **déboguer** menu, sélectionnez **effacer tous les DataTips**.  
  
### <a name="close-all-datatips-for-a-specific-file"></a>Fermer tous les DataTips d’un fichier spécifique  
  
Pour fermer tous les DataTips d’un fichier spécifique, sur le **déboguer** menu, sélectionnez **effacer tous les DataTips épinglés à \<Filename >**.  
  
## <a name="expand-and-edit-information"></a>Développez et modifier les informations  
Vous pouvez utiliser les DataTips pour développer un tableau, une structure ou un objet afin d’en afficher les membres. Vous pouvez également modifier la valeur d'une variable depuis un DataTip.  
  
### <a name="expand-a-variable"></a>Développer une variable

Pour développer un objet dans un DataTip pour voir ses éléments, pointez sur les flèches de développement avant les noms d’élément pour afficher les éléments sous forme d’arborescence. Pour un DataTip épinglé, sélectionnez le **+** avant que la variable nom, puis développez l’arborescence. 

![Développez un DataTip](../debugger/media/dbg-tour-data-tips.png "développez un DataTip")

Vous pouvez utiliser la souris ou les touches de direction du clavier pour monter ou Descendre dans la vue développée. 

Vous pouvez également épingler des éléments développés pour le DataTip épinglé en pointant dessus et en sélectionnant leur icône de punaise. Les éléments apparaissent ensuite dans le DataTip épinglé une fois que l’arborescence est réduite. 

### <a name="edit-the-value-of-a-variable"></a>Modifier la valeur d’une variable

Pour modifier la valeur d’une variable ou d’un élément dans un DataTip, sélectionnez la valeur, tapez une nouvelle valeur, puis appuyez sur **entrée**. Sélection est désactivée pour les valeurs en lecture seule.  

## <a name="visualize-complex-data-types"></a>Visualiser les types de données complexes  

Une icône de loupe qui se trouve en regard d’une variable ou d’un élément dans un DataTip signifie qu’une ou plusieurs [visualiseurs](../debugger/create-custom-visualizers-of-data.md), telles que la [visualiseur de texte](../debugger/string-visualizer-dialog-box.md), sont disponibles pour la variable. Visualiseurs affichent des informations de manière plus explicite, parfois graphique.
  
Pour afficher l’élément en utilisant le visualiseur par défaut pour le type de données, sélectionnez l’icône de loupe ![icône de visualiseur](../debugger/media/dbg-tips-visualizer-icon.png "icône de visualiseur"). Sélectionnez la flèche en regard de l’icône de loupe pour sélectionner dans une liste de visualiseurs pour le type de données.  

## <a name="add-a-variable-to-a-watch-window"></a>Ajouter une variable à une fenêtre Espion  

Si vous souhaitez continuer à surveiller une variable, vous pouvez l’ajouter à un **espion** fenêtre à partir d’un DataTip. Avec le bouton droit de la variable dans le DataTip, puis sélectionnez **ajouter un espion**. 

La variable s’affiche dans le **espion** fenêtre. Si votre édition de Visual Studio prend en charge plusieurs **espion** fenêtre, la variable s’affiche dans **Espion 1**. 
  
## <a name="import-and-export-datatips"></a>Importer et exporter des DataTips  

Vous pouvez exporter des DataTips vers un fichier XML, que vous pouvez partager ou modifier à l’aide d’un éditeur de texte. Vous pouvez également importer un fichier DataTip XML reçu ou modifié. 
  
**Pour exporter des DataTips :** 
  
1. Sélectionnez **déboguer** > **exporter des DataTips**.  
   
1. Dans le **exporter les DataTips** boîte de dialogue, accédez à l’emplacement pour enregistrer le fichier XML, tapez un nom pour le fichier, puis sélectionnez **enregistrer**.  
  
**Pour importer des DataTips :** 
  
1. Sélectionnez **déboguer** > **importer les DataTips**.  
   
1. Dans le **importer les DataTips** boîte de dialogue, sélectionnez le fichier DataTips XML que vous souhaitez ouvrir, puis sélectionnez **ouvrir**.  

## <a name="see-also"></a>Voir aussi  
 [Qu’est-ce que le débogage ?](../debugger/what-is-debugging.md)  
 [Corriger les bogues en écrivant un meilleur code C#](../debugger/write-better-code-with-visual-studio.md)  
 [Premier aperçu de débogage](../debugger/debugger-feature-tour.md) [affichage de données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Espion et Espion express, fenêtres](../debugger/watch-and-quickwatch-windows.md)   
 [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)   

