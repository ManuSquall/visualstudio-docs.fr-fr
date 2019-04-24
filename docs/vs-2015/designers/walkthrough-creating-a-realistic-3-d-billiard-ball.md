---
title: 'Procédure pas à pas : Création d’une boule de billard 3D réaliste | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: af8eb0f3-bf6a-4d1c-ab47-dcd88ab04efa
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 26dc068ca15de93cc2b0a3ac68b83d1d351bcad4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110594"
---
# <a name="walkthrough-creating-a-realistic-3-d-billiard-ball"></a>Procédure pas à pas : Création d’une boule de billard 3D réaliste
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment créer une boule de billard 3D réaliste en utilisant le concepteur Shader et l’Éditeur d’images dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. L’apparence 3D de la boule de billard s’obtient en combinant plusieurs techniques de nuanceur avec les ressources appropriées en texture.  
  
 Ce document illustre ces activités :  
  
- Création de l’apparence de base d’une boule de billard à l’aide des outils de forme et de texture  
  
- Ajout de profondeur à l’aide du modèle d’éclairage Lambert  
  
- Amélioration de l’apparence de base à l’aide des surbrillances spéculaires  
  
- Création d’un sens de l’espace en reflétant l’environnement  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous aurez besoin des composants et compétences suivants :  
  
- Un outil d’assemblage de textures dans un mappage de cube, tel que l’outil de texture DirectX fourni avec le SDK DirectX de juin 2010.  
  
- Une bonne connaissance de l’Éditeur d’images dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
- Une bonne connaissance du concepteur Shader dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
## <a name="creating-the-basic-appearance-with-shape-and-texture"></a>Création de l’apparence de base avec les outils de forme et de texture  
 En infographie, les éléments d’apparence les plus basiques sont la forme et la couleur. Dans une simulation sur ordinateur, il est courant d’utiliser un modèle 3D pour représenter la forme d’un objet réel. Le détail des couleurs est ensuite appliqué à la surface du modèle à l’aide d’une carte de texture.  
  
 En général, vous devrez peut-être demander à un artiste de créer un modèle 3D que vous pourrez utiliser, mais étant donné qu’une boule de billard est une forme commune (une sphère), le concepteur Shader a déjà un modèle approprié intégré.  
  
 La sphère est la forme d’aperçu par défaut dans le concepteur Shader. Si vous utilisez actuellement une forme différente pour prévisualiser votre nuanceur, rebasculez vers la sphère.  
  
#### <a name="to-preview-the-shader-by-using-a-sphere"></a>Pour afficher un aperçu du nuanceur à l’aide d’une sphère  
  
- Dans la barre d’outils du concepteur Shader, choisissez **Aperçu avec la sphère**.  
  
  À l’étape suivante, vous allez créer un programme de nuanceur qui applique une texture au modèle, mais vous devez commencer par créer une texture que vous pouvez utiliser. Cette procédure pas à pas montre comment créer la texture à l’aide de l’Éditeur d’images, qui fait partie de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], mais vous pouvez utiliser n’importe quel éditeur d’images capable d’enregistrer la texture dans un format approprié.  
  
  Assurez-vous que la fenêtre **Propriétés** et la **Boîte à outils** sont affichées.  
  
#### <a name="to-create-a-billiard-ball-texture-by-using-the-image-editor"></a>Pour créer une texture de boule de billard à l’aide de l’Éditeur d’images  
  
1. Créez une texture à utiliser. Pour plus d’informations sur l’ajout d’une texture à votre projet, consultez la section Mise en route de l’article [Éditeur d’images](../designers/image-editor.md).  
  
2. Définissez la taille de l’image afin que sa largeur soit deux fois supérieure à sa hauteur. Cela est nécessaire à cause du mode de mappage de la texture à la surface sphérique de la boule de billard. Pour redimensionner l’image, dans la fenêtre **Propriétés**, spécifiez les nouvelles valeurs des propriétés **Largeur** et **Hauteur**. Par exemple, définissez la largeur sur 512 et la hauteur sur 256.  
  
3. Dessinez une texture pour la boule de billard, en conservant à l’esprit la façon dont une texture est mappée à une sphère.  
  
    La texture doit ressembler à ceci :  
  
    ![Texture de la boule de billard](../designers/media/gfx-shader-demo-billiard-art-ball-texture.png "gfx_shader_demo_billiard_art_ball_texture")  
  
4. Vous pouvez éventuellement réduire les exigences en matière de stockage de cette texture. Pour cela, vous devez réduire la largeur de la texture afin qu’elle corresponde à sa hauteur. Cela compresse la texture par rapport à sa largeur, mais en raison de la manière dont la texture est mappée à la sphère, elle sera développée quand la balle de billard sera affichée. Après le redimensionnement, la texture doit ressembler à ceci :  
  
    ![Texture de la boule de billard compressée en carré](../designers/media/gfx-shader-demo-billiard-art-ball-texture-square.png "gfx_shader_demo_billiard_art_ball_texture_square")  
  
   Vous pouvez maintenant créer un nuanceur qui applique cette texture au modèle.  
  
#### <a name="to-create-a-basic-texture-shader"></a>Pour créer un nuanceur de texture de base  
  
1. Créez un shader DGSL à utiliser. Pour plus d’informations sur l’ajout d’un nuanceur DGSL à votre projet, consultez la section Prise en main de l’article [Concepteur de nuanceur](../designers/shader-designer.md).  
  
    Par défaut, un graphique de nuanceur ressemble à ceci :  
  
    ![Graphique du nuanceur par défaut](../designers/media/gfx-shader-demo-billiard-step-0.png "gfx_shader_demo_billiard_step_0")  
  
2. Modifiez le nuanceur par défaut pour qu’il applique la valeur d’un exemple de texture au pixel actuel. Le graphique de nuanceur doit ressembler à ceci :  
  
    ![Graphique du nuanceur qui applique la texture à un objet](../designers/media/gfx-shader-demo-billiard-step-1.png "gfx_shader_demo_billiard_step_1")  
  
3. Appliquez la texture que vous avez créée lors de la procédure précédente en configurant les propriétés de texture. Affectez **Texture1** comme valeur de la propriété **Texture** du nœud **Échantillon de texture**, puis spécifiez le fichier de texture en utilisant la propriété **Nom de fichier** du groupe de propriétés **Texture1** de la même fenêtre de propriétés.  
  
   Pour plus d’informations sur la façon d’appliquer une texture dans votre nuanceur, consultez [Guide pratique pour Créer un nuanceur de Texture de base](../designers/how-to-create-a-basic-texture-shader.md).  
  
   Votre boule de billard doit maintenant ressembler à ceci :  
  
   ![Gros plan de la boule de billard avec texture](../designers/media/gfx-shader-demo.png "gfx_shader_demo_")  
  
## <a name="creating-depth-with-the-lambert-lighting-model"></a>Création d’une profondeur avec le modèle d’éclairage Lambert  
 Jusqu’à présent, vous avez créé une boule de billard facilement reconnaissable. Toutefois, elle semble plate et inintéressante, et ressemble davantage à une représentation de boule de billard dans un dessin animé qu’à une réplique convaincante. L’apparence à deux dimensions résulte du nuanceur simpliste, qui se comporte comme si chaque pixel à la surface de la boule de billard recevait la même quantité de lumière.  
  
 Dans la réalité, la lumière semble plus forte sur les surfaces qui font directement face à une source de lumière et plus faible sur les surfaces qui font un angle oblique avec la source de lumière. C’est parce que l’énergie des rayons lumineux est distribuée sur la plus petite surface quand la surface fait directement face la source de lumière. À mesure que la surface s’éloigne de la source de lumière, la même quantité d’énergie est distribuée sur une surface de plus en plus grande. Une surface qui ne fait pas face à une source de lumière ne reçoit aucune énergie lumineuse, ce qui donne un aspect complètement sombre. Cette variation de luminosité sur la surface d’un objet est une aide visuelle importante qui indique la forme d’un objet. Sans elle, l’objet semble plat.  
  
 En infographie, les *modèles d’éclairage* (approximations simplifiées d’interactions d’éclairage réel complexe) sont utilisés pour reproduire l’apparence de l’éclairage réel. Le modèle d’éclairage Lambert varie la quantité de lumière diffusée sur la surface d’un objet, tel que décrit dans le paragraphe précédent. Vous pouvez ajouter le modèle d’éclairage Lambert à votre nuanceur pour donner à la boule de billard une apparence 3D plus convaincante.  
  
#### <a name="to-add-lambert-lighting-to-your-shader"></a>Pour ajouter un éclairage Lambert à votre nuanceur  
  
- Modifiez votre nuanceur pour moduler la valeur de l’exemple de texture par la valeur d’éclairage Lambert. Votre graphique de nuanceur doit ressembler à ceci :  
  
   ![Graphique du nuanceur avec éclairage Lambert ajouté](../designers/media/gfx-shader-demo-billiard-step-2.png "gfx_shader_demo_billiard_step_2")  
  
- Si vous le souhaitez, vous pouvez ajuster le comportement de l’éclairage en configurant la propriété **MaterialDiffuse** du graphique de nuanceur. Pour accéder aux propriétés du graphique de nuanceur, choisissez une zone vide de l’aire de conception puis, dans la fenêtre **Propriétés**, recherchez la propriété à laquelle vous souhaitez accéder.  
  
  Pour plus d’informations sur la façon d’appliquer l’éclairage Lambert dans votre nuanceur, consultez [Guide pratique pour Créer un nuanceur Lambert de base](../designers/how-to-create-a-basic-lambert-shader.md).  
  
  Quand l’éclairage Lambert est appliqué, la boule de billard doit ressembler à ceci :  
  
  ![Gros plan de la boule de billard éclairée et avec texture](../designers/media/gfx-shader-demo-billiard-ball-2.png "gfx_shader_demo_billiard_ball_2")  
  
## <a name="enhancing-the-basic-appearance-with-specular-highlights"></a>Amélioration de l’apparence de base avec les surbrillances spéculaires  
 Le modèle d’éclairage Lambert fournit le sens de la forme et des dimensions absent du nuanceur limité à la texture. Toutefois, la boule de billard a toujours une apparence quelque peu mate.  
  
 Une vraie boule de billard a généralement une finition brillante qui reflète une partie de la lumière qui y est projetée. Une partie de la lumière réfléchie est répercutée en surbrillances spéculaires, qui simulent les propriétés reflétantes d’une surface. En fonction des propriétés de la finition, les surbrillances peuvent être localisées ou étendues, intenses ou subtiles. Ces reflets spéculaires sont modelés à l’aide de la relation entre une source de lumière, l’orientation de la surface et la position de l’appareil photo. La surbrillance est plus intense quand l’orientation de la surface reflète la source de lumière directement dans l’appareil photo et moins intense quand le reflet est moins direct.  
  
 Le modèle d’éclairage Phong repose sur le modèle d’éclairage Lambert pour inclure des surbrillances spéculaires, comme décrit dans le paragraphe précédent. Vous pouvez ajouter le modèle d’éclairage Phong à votre nuanceur pour donner à la boule de billard une finition simulée entraînant une apparence plus intéressante.  
  
#### <a name="to-add-specular-highlights-to-your-shader"></a>Pour ajouter des surbrillances spéculaires à votre nuanceur  
  
1. Modifiez votre nuanceur pour y inclure la contribution spéculaire en utilisant une fusion additive. Votre graphique de nuanceur doit ressembler à ceci :  
  
    ![Graphique du nuanceur avec éclairage spéculaire ajouté](../designers/media/gfx-shader-demo-billiard-step-3.png "gfx_shader_demo_billiard_step_3")  
  
2. Si vous le souhaitez, vous pouvez ajuster le comportement de la surbrillance spéculaire en configurant les propriétés spéculaires (**MaterialSpecular** et **MaterialSpecularPower**) du graphique de nuanceur. Pour accéder aux propriétés du graphique de nuanceur, choisissez une zone vide de l’aire de conception puis, dans la fenêtre **Propriétés**, recherchez la propriété à laquelle vous souhaitez accéder.  
  
   Pour plus d’informations sur la façon d’appliquer les surbrillances spéculaires dans votre nuanceur, consultez [Guide pratique pour Créer un nuanceur Phong de base](../designers/how-to-create-a-basic-phong-shader.md).  
  
   Quand une mise en surbrillance spéculaire est appliquée, la boule de billard doit ressembler à ceci :  
  
   ![Gros plan de la boule de billard avec surbrillance spéculaire ajouté](../designers/media/gfx-shader-demo-billiard-ball-3.png "gfx_shader_demo_billiard_ball_3")  
  
## <a name="creating-a-sense-of-space-by-reflecting-the-environment"></a>Création d’un sens de l’espace en reflétant l’environnement  
 Quand des mises en surbrillances spéculaires sont appliquées, la boule de billard semble plutôt convaincante. Elle a la bonne forme, le bon travail de peinture et le bon fini. Toutefois, il existe encore une technique qui donnera à votre boule de billard une apparence tout à fait intégrée à son environnement.  
  
 Si vous examinez attentivement une vraie boule de billard, vous pouvez voir que sa surface brillante n’affiche pas simplement des surbrillances spéculaires, mais qu’elle reflète également faiblement une image du monde autour d’elle. Vous pouvez simuler ce reflet en utilisant une image de l’environnement comme texture et en la combinant avec la propre texture du modèle afin de déterminer la couleur finale de chaque pixel. En fonction du type de finition que vous souhaitez, vous pouvez combiner plus ou moins la texture du reflet avec le reste du nuanceur. Par exemple, un nuanceur qui simule une surface fortement réfléchissante comme un miroir peut utiliser uniquement la texture de reflet, mais un nuanceur qui simule un reflet plus subtil comme celui d’une boule de billard peut combiner seulement une petite partie de la valeur de la texture de reflet avec le reste du calcul de nuanceur.  
  
 Bien sûr, vous ne pouvez pas simplement appliquer l’image reflétée au modèle de la même façon que vous appliquez la carte de texture du modèle, car dans ce cas le reflet du monde se déplacerait avec la boule de billard comme si le reflet y était collé. Étant donné qu’un reflet peut provenir de n’importe quelle direction, vous avez besoin de fournir une valeur d’image de reflet pour n’importe quel angle, et d’un moyen de conserver l’image de reflet orientée selon le monde. Pour répondre à ces exigences, vous pouvez utiliser un type spécial de carte de texture, appelé *carte cubique*, qui fournit six textures organisées pour former les côtés d’un cube. À l’intérieur de ce cube, vous pouvez pointer vers n’importe quelle direction pour rechercher une valeur de texture. Si les textures de chaque côté du cube contiennent des images de l’environnement, vous pouvez simuler un reflet en échantillonnant l’emplacement approprié sur la surface du cube. En conservant le cube aligné sur le monde, vous obtenez un reflet précis de l’environnement. Pour déterminer où le cube doit être échantillonné, vous calculez uniquement le reflet du vecteur de la caméra sur la surface de l’objet, puis vous l’utilisez comme coordonnées de texture 3D. L’utilisation des cartes cubiques de cette manière est une technique courante appelée *mappage d’environnement*.  
  
 Le mappage d’environnement fournit une approximation efficace des vrais reflets comme décrit dans les paragraphes précédents. Vous pouvez fusionner des reflet mappés dans l’environnement dans votre nuanceur pour donner à la boule de billard une finition simulée qui donne l’impression qu’elle est davantage ancrée dans la scène.  
  
 La première étape consiste à créer une texture de carte cubique . Dans de nombreux genres d’applications, le contenu de la carte cubique ne doit pas être parfait pour être efficace, surtout quand le reflet est subtil ou n’occupe pas un espace significatif sur l’écran. Par exemple, de nombreux jeux utilisent des cartes cubiques précalculées pour le mappage d’environnement et n’utilisent que les plus proches de chaque objet réfléchi, bien que cela signifie que le reflet n’est pas correct. Même une approximation est relativement acceptable pour convaincre.  
  
#### <a name="to-create-textures-for-an-environment-map-by-using-the-image-editor"></a>Pour créer des textures pour un mappage d’environnement à l’aide de l’Éditeur d’images  
  
1. Créez une texture à utiliser. Pour plus d’informations sur l’ajout d’une texture à votre projet, consultez la section Mise en route de l’article [Éditeur d’images](../designers/image-editor.md).  
  
2. Définissez la taille de l’image afin que sa largeur soit égale à sa hauteur, et qu’elle soit une puissance de deux ; cela est nécessaire en raison de la façon dont une carte cubique est indexée. Pour redimensionner l’image, dans la fenêtre **Propriétés**, spécifiez les nouvelles valeurs des propriétés **Largeur** et **Hauteur**. Par exemple, affectez la valeur 256 aux propriétés **Largeur** et **Hauteur**.  
  
3. Utilisez une couleur unie pour remplir la texture. Cette texture sera le bas de la carte cubique, qui correspond à la surface de la table de billard. Gardez en mémoire la couleur que vous avez utilisée pour la texture suivante.  
  
4. Créez une deuxième texture qui a la même taille que la première. Cette texture est répétée pour les quatre côtés de la carte cubique, qui correspondent à la surface et aux côtés d’une table de billard, ainsi qu’à la zone autour de la table de billard. Veillez à dessiner la surface de la table de billard dans cette texture en utilisant la même couleur que dans la texture du bas. La texture doit ressembler à ceci :  
  
    ![Texture des côtés de la carte cubique](../designers/media/gfx-shader-demo-billiard-art-env-texture-side.png "gfx_shader_demo_billiard_art_env_texture_side")  
  
    N’oubliez pas qu’une image de reflet ne doit pas être photoréaliste pour être efficace ; par exemple, la carte cubique utilisée pour créer des images dans cet article contient seulement quatre trous au lieu de six.  
  
5. Créez une troisième texture qui a la même taille que les autres. Cette texture sera le haut de la carte cubique, qui correspond au plafond situé au-dessus de la table de billard. Pour rendre cette partie du reflet plus intéressante, vous pouvez dessiner une lumière de plafond pour renforcer les surbrillances spéculaires que vous avez ajoutées au nuanceur lors de la procédure précédente. La texture doit ressembler à ceci :  
  
    ![Texture du haut de la carte cubique](../designers/media/gfx-shader-demo-billiard-art-env-texture-top2.png "gfx_shader_demo_billiard_art_env_texture_top2")  
  
   Maintenant que vous avez créé des textures individuelles pour les côtés de la carte cubique, vous pouvez utiliser un outil pour les assembler en une carte cubique qui peut être stockée dans une texture .dds unique. Vous pouvez utiliser le programme de votre choix pour créer la carte cubique tant qu’il peut l’enregistrer au format de texture .dds. Cette procédure pas à pas montre comment créer la texture à l’aide de l’outil de texture DirectX qui fait partie du SDK de juin 2010.  
  
#### <a name="to-assemble-a-cube-map-by-using-the-directx-texture-tool"></a>Pour assembler une carte cubique à l’aide de l’outil DirectX Texture  
  
1. Dans l’outil DirectX Texture, dans le menu principal, choisissez **File**, **New Texture**. La boîte de dialogue **New Texture** s’affiche.  
  
2. Dans le groupe **Texture Type**, choisissez **Cubemap Texture**.  
  
3. Dans le groupe **Dimensions**, entrez la valeur correcte pour **Width** et **Height**, puis choisissez **OK**. Un nouveau document de texture apparaît. Par défaut, la texture affichée en premier dans le document de texture correspond à la face de cube **Positive X**.  
  
4. Chargez la texture que vous avez créée pour le côté du cube de texture sur la face de cube. Dans le menu principal, choisissez **File**, **Open Onto This Cubemap Face**, sélectionnez la texture que vous avez créée pour le côté du cube, puis choisissez **Open**.  
  
5. Répétez l’étape 4 pour les faces de cube **Negative X**, **Positive Z** et **Negative Z**. Pour cela, vous devez afficher la face à charger. Pour afficher une face de carte cubique différente, dans le menu principal, choisissez **View**, **Cube Map Face**, puis sélectionnez la face que vous souhaitez afficher.  
  
6. Pour la face de cube **Positive Y**, chargez la texture que vous avez créée pour le haut du cube de texture.  
  
7. Pour la face de cube **Negative Y**, chargez la texture que vous avez créée pour le bas du cube de texture.  
  
8. Enregistrez la texture.  
  
   Vous pouvez imaginer la disposition de la carte cubique comme suit  :  
  
   ![Disposition de la carte cubique d’environnement](../designers/media/gfx-shader-demo-billiard-art-env-texture-top.png "gfx_shader_demo_billiard_art_env_texture_top")  
  
   L’image en haut est la face de cube Y positif (+Y) ; au milieu, de gauche à droite, il s’agit des faces de cube –X, +Z, +X et –Z ; en bas il s’agit de la face de cube –Y.  
  
   Vous pouvez maintenant modifier le nuanceur pour fusionner l’exemple de carte cubique dans le reste du nuanceur.  
  
#### <a name="to-add-environment-mapping-to-your-shader"></a>Pour ajouter un mappage d’environnement à votre nuanceur  
  
1. Modifiez votre nuanceur pour y inclure la contribution de mappage d’environnement en utilisant une fusion additive. Votre graphique de nuanceur doit ressembler à ceci :  
  
    ![Gros plan sur les deux genres de nœuds du nuanceur miroitants](../designers/media/gfx-shader-demo-billiard-step-4b.png "gfx_shader_demo_billiard_step_4b")  
  
    Notez que vous pouvez utiliser un nœud **Multiplier-Ajouter** pour simplifier le graphique de nuanceur.  
  
    Voici une vue plus détaillée des nœuds de nuanceurs qui implémentent le mappage d’environnement :  
  
    ![Graphique du nuanceur avec environnement de mappage ajouté](../designers/media/gfx-shader-demo-billiard-step-4a.png "gfx_shader_demo_billiard_step_4a")  
  
2. Appliquez la texture que vous avez créée lors de la procédure précédente en configurant les propriétés de texture de la carte cubique. Affectez **Texture2** comme valeur de la propriété **Texture** du nœud **Exemple de cubemap**, puis spécifiez le fichier de texture en utilisant la propriété **Nom de fichier** du groupe de propriétés **Texture2**.  
  
3. Si vous le souhaitez, vous pouvez ajuster la réflectivité de la boule de billard en configurant la propriété **Sortie** du nœud **Constante**. Pour accéder aux propriétés du nœud, sélectionnez-le puis, dans la fenêtre **Propriétés**, recherchez la propriété à laquelle vous souhaitez accéder.  
  
   Quand le mappage d’environnement est appliqué, la boule de billard doit ressembler à ceci :  
  
   ![Gros plan de la boule de billard mappée sur l’environnement](../designers/media/gfx-shader-demo-billiard-ball-4.png "gfx_shader_demo_billiard_ball_4")  
  
   Dans cette image finale, notez comment les effets que vous avez ajoutés se combinent pour créer une boule de billard très convaincante. La forme, la texture et l’éclairage créent l’apparence de base d’un objet 3D. Les reflets et les surbrillances spéculaires rendent la boule de billard plus intéressante et intégrée à l’environnement.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Exporter un nuanceur](../designers/how-to-export-a-shader.md)   
 [Guide pratique pour Appliquer un nuanceur à un modèle 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Concepteur de nuanceur](../designers/shader-designer.md)   
 [Éditeur d’images](../designers/image-editor.md)   
 [Nœuds du concepteur Shader](../designers/shader-designer-nodes.md)
