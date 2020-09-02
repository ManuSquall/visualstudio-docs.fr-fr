---
title: Afficher les valeurs de données dans les conseils de données dans l’éditeur de code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fd2c7bf67b5c2e7f25b4193462883b53cda8db87
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700105"
---
# <a name="view-data-values-in-data-tips--in-the-code-editor"></a>Afficher les valeurs des données dans les conseils de données de l'éditeur de code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les DataTips sont un moyen pratique de visualiser des informations sur les variables de votre programme au cours du débogage. Les DataTips ne fonctionnent qu'en mode arrêt, et uniquement avec les variables comprises dans la portée d'exécution actuelle.  
  
 Dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] , les DataTips peuvent être épinglés à un emplacement spécifique dans un fichier source ou flotter au-dessus de toutes les [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fenêtres.  
  
### <a name="to-display-a-datatip-in-break-mode-only"></a>Pour afficher un DataTip (en mode arrêt uniquement)  
  
1. Dans une fenêtre source, placez le pointeur de la souris sur une variable quelconque dans la portée actuelle.  
  
    Un DataTip apparaît.  
  
   > [!NOTE]
   > Les conseils relatifs aux données sont toujours évalués dans le contexte où l'exécution est interrompue, et non pas lorsque le curseur pointe un élément. Si vous pointez sur une variable dans une autre fonction portant le même nom qu'une variable qui est dans le contexte actuel, la variable dans l'autre fonction est affichée comme la valeur de la variable dans le contexte actuel.  
  
2. Le DataTip disparaît lorsque vous retirez le pointeur de la souris. Pour épingler le DataTip afin qu’il reste ouvert, cliquez sur l’icône **Épingler à la source** ou  
  
   - Cliquez avec le bouton droit sur une variable, puis cliquez sur **Épingler à la source**.  
  
     Le DataTip épinglé se ferme à la fin de la session de débogage.  
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Pour détacher un DataTip et le rendre flottant  
  
- Dans un DataTip épinglé, cliquez sur l’icône **détacher de la source** .  
  
     L'icône d'épingle reprend sa position détachée. Le DataTip flotte à présent au-dessus de toutes les fenêtres actives. Le DataTip flottant se ferme à la fin de la session de débogage.  
  
### <a name="to-repin-a-floating-datatip"></a>Pour réépingler un DataTip flottant  
  
- Dans un DataTip, cliquez sur l'icône d'épingle.  
  
     L'icône d'épingle reprend sa position épinglée. Si le DataTip se trouve à l'extérieur d'une fenêtre source, l'icône d'épingle est désactivée et le DataTip ne peut pas être épinglé.  
  
### <a name="to-close-a-datatip"></a>Pour fermer un DataTip  
  
- Placez le pointeur de la souris sur un DataTip, puis cliquez sur l’icône de **fermeture** .  
  
### <a name="to-close-all-datatips"></a>Pour fermer tous les DataTips  
  
- Dans le menu **Déboguer** , cliquez sur **Effacer tous les DataTips**.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Pour fermer tous les DataTips d'un fichier spécifique  
  
- Dans le menu **Déboguer** , cliquez sur **Effacer tous les DataTips épinglés au** *fichier*.  
  
## <a name="expanding-and-editing-information"></a>Développement et modification d’informations  
 Vous pouvez utiliser les DataTips pour développer un tableau, une structure ou un objet afin d’en afficher les membres. Vous pouvez également modifier la valeur d'une variable depuis un DataTip.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Développer une variable pour voir ses éléments  
  
- Dans un DataTip, placez le pointeur de la souris sur le **+** signe qui précède le nom de la variable.  
  
     La variable se développe et affiche ses éléments sous forme d'arborescence.  
  
     Une fois la variable développée, vous pouvez utiliser les touches de direction du clavier pour vous déplacer vers le haut ou vers le bas. Vous pouvez également utiliser la souris.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>Pour modifier la valeur d'une variable à l'aide d'un DataTip  
  
1. Dans un DataTip, cliquez sur la valeur. Cette possibilité est désactivée pour les valeurs en lecture seule.  
  
2. Tapez une nouvelle valeur et appuyez sur ENTRÉE.  
  
## <a name="making-a-datatip-transparent"></a>Rendre un DataTip transparent  
 Si vous souhaitez visualiser le code masqué par un DataTip, vous pouvez rendre celui-ci temporairement transparent. Cela ne s'applique pas aux DataTips épinglés ou flottants.  
  
#### <a name="to-make-a-datatip-transparent"></a>Pour rendre un DataTip transparent  
  
- Dans un DataTip, appuyez sur CTRL.  
  
     Le DataTip reste transparent tant que vous maintenez la touche CTRL enfoncée.  
  
## <a name="visualizing-complex-data-types"></a>Affichage de types de données complexes  
 Si une icône de loupe apparaît à côté d’un nom de variable dans un DataTip, un ou plusieurs [visualiseurs de création personnalisés](../debugger/create-custom-visualizers-of-data.md) sont disponibles pour les variables de ce type de données. Les visualiseurs servent à afficher les informations de façon plus explicite (en général graphique).  
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Voir le contenu d'une variable à l'aide d'un visualiseur  
  
- Cliquez sur l'icône en forme de loupe pour sélectionner le visualiseur par défaut du type de données.  
  
     - ou -  
  
     Cliquez sur la flèche contextuelle à côté du visualiseur pour choisir dans une liste le visualiseur approprié pour ce type de données.  
  
     Un visualiseur apparaît et affiche les informations.  
  
## <a name="adding-information-to-a-watch-window"></a>Ajouter des informations à une fenêtre Espion  
 Si vous souhaitez continuer à regarder une variable, vous pouvez ajouter la variable à la fenêtre **Espion** à partir d’un DataTip.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>Ajouter une variable à la fenêtre Espion  
  
- Cliquez avec le bouton droit sur un DataTip, puis cliquez sur **Ajouter un espion**.  
  
     La variable est ajoutée à la fenêtre **Espion** . Si vous utilisez une édition qui prend en charge plusieurs fenêtres **Espion** , la variable est ajoutée à **Watch 1.**  
  
## <a name="importing-and-exporting-datatips"></a>Importation et exportation de DataTips  
 Vous pouvez exporter des DataTips vers un fichier XML, qui peut être partagé avec un collègue ou modifié à l'aide d'un éditeur de texte.  
  
#### <a name="to-export-datatips"></a>Pour exporter des DataTips  
  
1. Dans le menu Déboguer, cliquez sur **Exporter les DataTips**.  
  
     La boîte de dialogue **Exporter les DataTips** s’affiche.  
  
2. Utilisez les techniques de fichier standard pour naviguer jusqu’à l’emplacement où vous souhaitez enregistrer le fichier XML, tapez un nom pour le fichier dans la zone **nom de fichier** , puis cliquez sur **OK**.  
  
#### <a name="to-import-datatips"></a>Pour importer des DataTips  
  
1. Dans le menu Déboguer, cliquez sur **Importer les DataTips**.  
  
     La boîte de dialogue **Importer les DataTips** s’affiche.  
  
2. Utilisez la boîte de dialogue pour rechercher le fichier XML que vous souhaitez ouvrir, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Comment : utiliser la boîte de dialogue Espion express](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)   
 [Comment : modifier le format numérique des fenêtres du débogueur](https://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)
