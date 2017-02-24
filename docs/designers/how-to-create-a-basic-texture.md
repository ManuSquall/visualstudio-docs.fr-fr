---
title: "Comment : créer une texture de base | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
caps.latest.revision: 15
author: BrianPeek
ms.author: brpeek
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
ms.openlocfilehash: e8455a68a2be88e177746433ad3b41e412c8de38

---
# <a name="how-to-create-a-basic-texture"></a>Comment : créer une texture de base
Ce document montre comment utiliser l’éditeur d’images pour créer une texture de base.  
  
 Ce document illustre ces activités :  
  
-   Définition de la taille de la texture  
  
-   Définition des couleurs de premier plan et d’arrière-plan  
  
-   Utilisation du canal alpha (transparence)  
  
-   Utilisation des outils **Remplissage** et **Ellipse**  
  
-   Définition des propriétés des outils  
  
## <a name="creating-a-basic-texture"></a>Création d’une texture de base  
 Vous pouvez utiliser l’éditeur d’images pour créer et modifier des images et des textures pour votre jeu ou application.  
  
 Les étapes suivantes montrent comment créer une texture représentant une cible. Lorsque vous avez terminé, la texture doit ressembler à l’image suivante. Pour mettre en évidence la transparence de la texture, l’éditeur d’images a été configuré pour utiliser un modèle à damiers verts pour l’afficher.  
  
 ![Cible avec transparence affichée en vert](../designers/media/digit-bullseye-texture-in-editor.png "Digit-Bullseye-Texture-In-Editor")  
  
 Avant de commencer, assurez-vous que la fenêtre **Propriétés** est affichée. Vous allez l’utiliser pour définir la taille de l’image, modifier les propriétés des outils et spécifier des couleurs pendant que vous travaillez.  
  
#### <a name="to-create-a-bullseye-target-texture"></a>Pour créer une texture de cible  
  
1.  Créez une texture à utiliser. Pour plus d’informations sur l’ajout d’une texture à votre projet, consultez la section Mise en route de l’article [Éditeur d’images](../designers/image-editor.md).  
  
2.  Définissez la taille de l’image sur 512x512 pixels. Dans la fenêtre **Propriétés**, définissez les valeurs des propriétés **Largeur** et **Hauteur** sur `512`.  
  
3.  Dans la barre d’outils de l’éditeur d’images, choisissez l’outil **Remplissage**. À présent, la fenêtre **Propriétés** affiche les propriétés de l’outil **Remplissage** ainsi que les propriétés des images.  
  
4.  Définissez la couleur de premier plan sur noir entièrement transparent. Dans la fenêtre **Propriétés**, dans le groupe de propriétés **Couleurs**, sélectionnez **Premier plan**. Définissez les valeurs des propriétés **R**, **V**, **B** et **A** situées en regard du sélecteur de couleurs sur `0`.  
  
5.  Dans la barre d’outils de l’éditeur d’images, choisissez l’outil **Remplissage**, puis appuyez sur la touche Maj de façon prolongée et choisissez un point de l’image. L’utilisation de la touche Maj provoque le remplacement de la couleur de l’image par la valeur alpha de la couleur de remplissage. Par ailleurs, la valeur alpha permet de fusionner la couleur de remplissage avec la couleur de l’image.  
  
    > [!IMPORTANT]
    >  Cette étape, associée à la sélection de couleur de l’étape précédente, permet de s’assurer que l’image de base est préparée pour la texture de la cible que vous dessinez. Lorsque l’image est remplie de noir transparent, et parce que la bordure de la cible est noire, il n’existe pas d’artefact de crénelage autour de la cible.  
  
6.  Dans la barre d’outils de l’éditeur d’images, choisissez l’outil **Ellipse**.  
  
7.  Définissez la couleur de premier plan sur noir entièrement opaque. Définissez les valeurs des propriétés **R**, **V** et **B** sur `0`, et la valeur de la propriété **A** sur `255`.  
  
8.  Définissez la couleur d’arrière-plan sur blanc entièrement opaque. Dans la fenêtre **Propriétés**, dans le groupe de propriétés **Couleurs**, sélectionnez **Arrière-plan**. Définissez les valeurs des propriétés **R**, **V**, **B** et **A** sur `255`.  
  
9. Définissez la largeur du contour de l’ellipse. Dans la fenêtre **Propriétés**, dans le groupe de propriétés **Apparence**, définissez la valeur de la propriété **Largeur** sur `8`.  
  
10. Vérifiez que l’anticrénelage est activé. Dans la fenêtre **Propriétés**, dans le groupe de propriétés **Apparence**, assurez-vous que la propriété **Anticrénelage** est définie.  
  
11. À l’aide de l’outil **Ellipse**, tracez un cercle des coordonnées de pixel `(3, 3)` aux coordonnées de pixel `(508, 508)`. Pour tracer le cercle plus facilement, vous pouvez appuyer sur la touche Maj de façon prolongée tout en effectuant le tracé.  
  
    > [!NOTE]
    >  Les coordonnées en pixels de l’emplacement actuel du pointeur sont affichées sur la barre d’état [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
12. Modifiez la couleur d’arrière-plan. Définissez **R** sur `44`, **V** sur `165`, **B** sur `211`, et **A** sur `255`.  
  
13. Tracez un autre cercle des coordonnées de pixel `(64, 64)` aux coordonnées de pixel `(448, 448)`.  
  
14. Modifiez la couleur d’arrière-plan de nouveau sur blanc entièrement opaque. Définissez **R**, **V**, **B** et **A** sur `255`.  
  
15. Tracez un autre cercle des coordonnées de pixel `(128, 128)` aux coordonnées de pixel `(384, 384)`.  
  
16. Modifiez la couleur d’arrière-plan. Définissez **R** sur `255`, **V** et **B** sur `64`, et **A** sur `255`.  
  
17. Tracez un autre cercle des coordonnées de pixel `(192, 192)` aux coordonnées de pixel `(320, 320)`.  
  
 La texture de cible est complète. Voici l’image finale, affichée avec la transparence.  
  
 ![Texture de cible complète](../designers/media/gfx_image_demo_bullseye.png "gfx_image_demo_bullseye")  
  
 Ensuite, vous pouvez générer des niveaux MIP pour cette texture. Pour plus d’informations, consultez l’article [Comment : créer et modifier les niveaux MIP](../designers/how-to-create-and-modify-mip-levels.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur d’images](../designers/image-editor.md)


<!--HONumber=Feb17_HO4-->


