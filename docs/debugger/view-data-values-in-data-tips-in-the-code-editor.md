---
title: "Afficher les valeurs des donn&#233;es dans les conseils de donn&#233;es de l&#39;&#233;diteur de code | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "outil DataTips"
  - "déboguer (Visual Studio), DataTips"
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Afficher les valeurs des donn&#233;es dans les conseils de donn&#233;es de l&#39;&#233;diteur de code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les DataTips sont un moyen pratique de visualiser des informations sur les variables de votre programme au cours du débogage.  Les DataTips ne fonctionnent qu'en mode arrêt, et uniquement avec les variables comprises dans la portée d'exécution actuelle.  
  
 Dans [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], les DataTips peuvent être épinglés à un emplacement spécifique d'un fichier source ou flotter au\-dessus de toutes les fenêtres [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### Pour afficher un DataTip \(en mode arrêt uniquement\)  
  
1.  Dans une fenêtre source, placez le pointeur de la souris sur une variable quelconque dans la portée actuelle.  
  
     Un DataTip apparaît.  
  
    > [!NOTE]
    >  Les conseils relatifs aux données sont toujours évalués dans le contexte où l'exécution est interrompue, et non pas lorsque le curseur pointe un élément.  Si vous pointez sur une variable dans une autre fonction portant le même nom qu'une variable qui est dans le contexte actuel, la variable dans l'autre fonction est affichée comme la valeur de la variable dans le contexte actuel.  
  
2.  Le DataTip disparaît lorsque vous retirez le pointeur de la souris.  Pour épingler un DataTip afin qu'il reste ouvert, cliquez sur l'icône **Épingler à la source** ou  
  
    -   cliquez avec le bouton droit sur une variable, puis cliquez sur **Épingler à la source**.  
  
     Le DataTip épinglé se ferme à la fin de la session de débogage.  
  
### Pour détacher un DataTip et le rendre flottant  
  
-   Dans un DataTip épinglé, cliquez sur l'icône **Détacher de la source**.  
  
     L'icône d'épingle reprend sa position détachée.  Le DataTip flotte à présent au\-dessus de toutes les fenêtres actives.  Le DataTip flottant se ferme à la fin de la session de débogage.  
  
### Pour réépingler un DataTip flottant  
  
-   Dans un DataTip, cliquez sur l'icône d'épingle.  
  
     L'icône d'épingle reprend sa position épinglée.  Si le DataTip se trouve à l'extérieur d'une fenêtre source, l'icône d'épingle est désactivée et le DataTip ne peut pas être épinglé.  
  
### Pour fermer un DataTip  
  
-   Placez le pointeur de la souris sur un DataTip, puis cliquez sur l'icône **Fermer**.  
  
### Pour fermer tous les DataTips  
  
-   Dans le menu **Déboguer**, cliquez sur **Effacer tous les DataTips**.  
  
### Pour fermer tous les DataTips d'un fichier spécifique  
  
-   Dans le menu **Déboguer**, cliquez sur **Effacer tous les DataTips épinglés à** *File*.  
  
## Développement et modification d'informations  
 Vous pouvez utiliser les DataTips pour développer un tableau, une structure ou un objet afin d'en afficher les membres.  Vous pouvez également modifier la valeur d'une variable depuis un DataTip.  
  
#### Développer une variable pour voir ses éléments  
  
-   Dans un DataTip, placez le pointeur de la souris sur le signe **\+** situé avant le nom de la variable.  
  
     La variable se développe et affiche ses éléments sous forme d'arborescence.  
  
     Une fois la variable développée, vous pouvez utiliser les touches de direction du clavier pour vous déplacer vers le haut ou vers le bas.  Vous pouvez également utiliser la souris.  
  
#### Pour modifier la valeur d'une variable à l'aide d'un DataTip  
  
1.  Dans un DataTip, cliquez sur la valeur.  Cette possibilité est désactivée pour les valeurs en lecture seule.  
  
2.  Tapez une nouvelle valeur et appuyez sur ENTRÉE.  
  
## Rendre un DataTip transparent  
 Si vous souhaitez visualiser le code masqué par un DataTip, vous pouvez rendre celui\-ci temporairement transparent.  Cela ne s'applique pas aux DataTips épinglés ou flottants.  
  
#### Pour rendre un DataTip transparent  
  
-   Dans un DataTip, appuyez sur CTRL.  
  
     Le DataTip reste transparent tant que vous maintenez la touche CTRL enfoncée.  
  
## Affichage de types de données complexes  
 Si une icône de loupe apparaît à côté d'un nom de variable dans un DataTip, cela signifie qu'un ou plusieurs [Visualiseurs](../debugger/create-custom-visualizers-of-data.md) sont disponibles pour les variables de ce type de données.  Les visualiseurs servent à afficher les informations de façon plus explicite \(en général graphique\).  
  
#### Voir le contenu d'une variable à l'aide d'un visualiseur  
  
-   Cliquez sur l'icône en forme de loupe pour sélectionner le visualiseur par défaut du type de données.  
  
     ou  
  
     Cliquez sur la flèche contextuelle à côté du visualiseur pour choisir dans une liste le visualiseur approprié pour ce type de données.  
  
     Un visualiseur apparaît et affiche les informations.  
  
## Ajouter des informations à une fenêtre Espion  
 Si vous voulez continuer à surveiller une variable, vous pouvez l'ajouter à la fenêtre **Espion** à partir d'un DataTip.  
  
#### Ajouter une variable à la fenêtre Espion  
  
-   Cliquez avec le bouton droit sur un DataTip, puis cliquez sur **Ajouter un espion**.  
  
     La variable est ajoutée à la fenêtre **Espion**.  Si vous utilisez une édition qui prend en charge plusieurs fenêtres **Espion**, la variable est ajoutée à **Espion 1**.  
  
## Importation et exportation de DataTips  
 Vous pouvez exporter des DataTips vers un fichier XML, qui peut être partagé avec un collègue ou modifié à l'aide d'un éditeur de texte.  
  
#### Pour exporter des DataTips  
  
1.  Dans le menu Déboguer, cliquez sur **Exporter les DataTips**.  
  
     La boîte de dialogue **Exporter les DataTips** s'affiche.  
  
2.  Utilisez les techniques standard pour naviguer jusqu'à l'emplacement où vous souhaitez enregistrer le fichier XML, attribuez\-lui un nom dans la zone **Nom de fichier**, puis cliquez sur **OK**.  
  
#### Pour importer des DataTips  
  
1.  Dans le menu Déboguer, cliquez sur **Importer les DataTips**.  
  
     La boîte de dialogue **Importer les DataTips** s'affiche.  
  
2.  Utilisez la boîte de dialogue pour rechercher le fichier XML à ouvrir et cliquez sur **OK**.  
  
## Voir aussi  
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Comment : utiliser la boîte de dialogue Espion express](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Visualiseurs](../debugger/create-custom-visualizers-of-data.md)   
 [Comment : modifier le format numérique des fenêtres du débogueur](../Topic/How%20to:%20Change%20the%20Numeric%20Format%20of%20Debugger%20Windows.md)