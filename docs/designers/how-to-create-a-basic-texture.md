---
title: 'Comment : créer une texture de base'
description: Découvrez comment utiliser l’éditeur d’images pour créer une texture de base, notamment la définition de la taille de la texture, la définition des propriétés de l’outil et d’autres activités.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2ac90077831d852ba0361c46186d18fe39cf9e81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931069"
---
# <a name="how-to-create-a-basic-texture"></a>Guide pratique pour créer une texture de base

Cet article montre comment utiliser l’éditeur d’images pour créer une texture de base, et détaille notamment les activités suivantes :

- Définition de la taille de la texture

- Définition des couleurs de premier plan et d’arrière-plan

- Utilisation du canal alpha (transparence)

- Utilisation des outils **Remplissage** et **Ellipse**

- Définition des propriétés des outils

## <a name="create-a-basic-texture"></a>Créer une texture de base

Vous pouvez utiliser l’éditeur d’images pour créer et modifier des images et des textures pour votre jeu ou application.

Les étapes suivantes montrent comment créer une texture qui représente une cible. Une fois terminé, la texture doit ressembler à l’image suivante. Pour mettre en évidence la transparence de la texture, l’éditeur d’images a été configuré pour utiliser un modèle à damiers verts pour l’afficher.

![Cible « Bullseye » avec la transparence illustrée en vert](../designers/media/digit-bullseye-texture-in-editor.png)

Avant de commencer, assurez-vous que la fenêtre **Propriétés** est affichée. Vous utilisez la fenêtre **Propriétés** pour définir la taille de l'image,, modifier les propriétés des outils et spécifier des couleurs pendant que vous travaillez.

### <a name="create-a-bullseye-target-texture"></a>Créer une texture de type cible

1. Créez une texture avec laquelle travailler. Pour plus d’informations sur l’ajout d’une texture à un projet, voir [Éditeur d’images](../designers/image-editor.md#get-started).

2. Définissez la taille de l’image sur 512x512 pixels. Dans la fenêtre **Propriétés**, définissez les valeurs des propriétés **Largeur** et **Hauteur** sur `512`.

3. Dans la barre d’outils de l’éditeur d’images, choisissez l’outil **Remplissage**. À présent, la fenêtre **Propriétés** affiche les propriétés de l’outil **Remplissage** ainsi que les propriétés des images.

4. Définissez la couleur de premier plan en choisissant du noir complètement transparent. Dans la fenêtre **Propriétés**, dans le groupe de propriétés **Couleurs**, sélectionnez **Premier plan**. Définissez les valeurs des propriétés **R**, **V**, **B** et **A** situées en regard du sélecteur de couleurs sur `0`.

5. Dans la barre d’outils de l’éditeur d’images, choisissez l’outil **remplissage** , puis appuyez et maintenez la touche **MAJ** enfoncée et choisissez n’importe quel point dans l’image. Si vous utilisez la touche **MAJ** , la valeur alpha de la couleur de remplissage remplace la couleur dans l’image. dans le cas contraire, la valeur alpha est utilisée pour mélanger la couleur de remplissage avec la couleur de l’image.

    > [!IMPORTANT]
    > Cette étape, associée à la sélection de couleur de l’étape précédente, permet de s’assurer que l’image de base est préparée pour la texture de la cible que vous dessinez. Lorsque l’image est remplie de noir transparent, et parce que la bordure de la cible est noire, il n’existe pas d’artefact de crénelage autour de la cible.

6. Dans la barre d’outils de l’éditeur d’images, choisissez l’outil **Ellipse**.

7. Définissez la couleur de premier plan en choisissant du noir complètement opaque. Définissez les valeurs des propriétés **R**, **V** et **B** sur `0`, et la valeur de la propriété **A** sur `255`.

8. Définissez la couleur d’arrière-plan en choisissant du blanc complètement opaque. Dans la fenêtre **Propriétés**, dans le groupe de propriétés **Couleurs**, sélectionnez **Arrière-plan**. Définissez les valeurs des propriétés **R**, **V**, **B** et **A** sur `255`.

9. Définissez la largeur du contour de l’ellipse. Dans la fenêtre **Propriétés**, dans le groupe de propriétés **Apparence**, définissez la valeur de la propriété **Largeur** sur `8`.

10. Vérifiez que l’anticrénelage est activé. Dans la fenêtre **Propriétés**, dans le groupe de propriétés **Apparence**, assurez-vous que la propriété **Anticrénelage** est définie.

11. À l’aide de l’outil **Ellipse**, tracez un cercle des coordonnées de pixel `(3, 3)` aux coordonnées de pixel `(508, 508)`. Pour dessiner le cercle plus facilement, vous pouvez appuyer sur la touche **MAJ** et la maintenir enfoncée pendant que vous dessinez.

    > [!NOTE]
    > Les coordonnées en pixels de l’emplacement actuel du pointeur sont affichées sur la barre d’état Visual Studio.

12. Modifiez la couleur d’arrière-plan. Définissez **R** sur `44`, **V** sur `165`, **B** sur `211`, et **A** sur `255`.

13. Tracez un autre cercle des coordonnées de pixel `(64, 64)` aux coordonnées de pixel `(448, 448)`.

14. Changez à nouveau la couleur d’arrière-plan en choisissant du blanc complètement opaque. Définissez **R**, **V**, **B** et **A** sur `255`.

15. Tracez un autre cercle des coordonnées de pixel `(128, 128)` aux coordonnées de pixel `(384, 384)`.

16. Modifiez la couleur d’arrière-plan. Définissez **R** sur `255`, **V** et **B** sur `64`, et **A** sur `255`.

17. Tracez un autre cercle des coordonnées de pixel `(192, 192)` aux coordonnées de pixel `(320, 320)`.

La texture de cible est complète. Voici l’image finale, affichée avec la transparence.

![Texture cible « Bullseye » complète](../designers/media/gfx_image_demo_bullseye.png)

Ensuite, vous pouvez générer des niveaux MIP pour cette texture. Pour plus d’informations, consultez [Comment : créer et modifier des niveaux MIP](../designers/how-to-create-and-modify-mip-levels.md).

## <a name="see-also"></a>Voir aussi

- [Éditeur d’images](../designers/image-editor.md)
