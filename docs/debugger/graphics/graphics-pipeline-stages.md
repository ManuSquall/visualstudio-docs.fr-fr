---
title: Étapes de canalisation Graphics | Microsoft Docs
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.pipeline
ms.assetid: 2bf5c12e-2a00-401c-8163-4e373d08ad3f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d697313289bbf00234764cc04603b7bc256f174
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735467"
---
# <a name="graphics-pipeline-stages"></a>Étapes de canalisation Graphics
La fenêtre Étapes de canalisation Graphics vous permet de comprendre comment un appel de dessin individuel est transformé par chaque étape de canalisation graphismes Direct3D.

 Voici la fenêtre Étapes de canalisation :

 ![Un objet 3D passe par les étapes de pipeline.](media/gfx_diag_demo_pipeline_stages_orientation.png)

## <a name="understanding-the-graphics-pipeline-stages-window"></a>Présentation de la fenêtre Étapes de canalisation Graphics
 La fenêtre Étapes de canalisation affiche le résultat de chaque étape de canalisation Graphics séparément, pour chaque appel de dessin. Normalement, les résultats des étapes de canalisation intermédiaires sont masqués, ce qui complique la tâche consistant à déterminer l'origine d'un problème de rendu. En affichant chaque étape séparément, la fenêtre Étapes de canalisation facilite l'identification de l'origine du problème. Par exemple, vous pouvez voir aisément le moment où l'étape du nuanceur de sommets provoque soudainement le dessin d'un objet hors de l'écran.

 Une fois que vous avez identifié l'étape durant laquelle le problème se produit, vous pouvez utiliser les autres outils Graphics Analyzer pour examiner la façon dont les données ont été interprétées ou transformées. Les problèmes de rendu qui apparaissent aux étapes de canalisation sont souvent liés à des descripteurs de format de sommet incorrects, à des programmes de nuanceur bogués ou à un état mal configuré.

### <a name="links-to-related-graphics-objects"></a>Liens vers les objets graphiques connexes
 Parfois, un contexte supplémentaire est nécessaire pour déterminer la raison pour laquelle un appel de dessin interagit de façon spécifique avec la canalisation Graphics. Pour faciliter la recherche de ce contexte supplémentaire, la fenêtre Étapes de canalisation Graphics comporte des liens vers un ou plusieurs objets qui fournissent un contexte supplémentaire relatif à ce qui se passe dans la canalisation Graphics.

- Dans Direct3D 12, cet objet est généralement une liste de commandes.

- Dans Direct3D 11, cet objet est généralement un contexte de périphérique graphique.

  Ces liens font partie de la signature d'événement Graphics actuelle dans le coin supérieur gauche de la fenêtre Étapes de canalisation Graphics. Suivez ces liens pour obtenir des détails supplémentaires sur l'objet.

### <a name="viewing-and-debugging-shader-code"></a>Affichage et débogage du code du nuanceur
 Vous pouvez examiner et déboguer le code des nuanceurs de sommets, de coques, de domaines, de géométries et de pixels à l'aide des contrôles situés au bas de leurs étapes respectives dans la fenêtre Étapes de canalisation.

#### <a name="to-view-a-shaders-source-code"></a>Pour afficher le code source d'un nuanceur

- Dans la fenêtre **Étapes de canalisation Graphics**, localisez l’étape de nuanceur qui correspond au nuanceur que vous souhaitez examiner. Sous l’image d’aperçu, suivez le lien du titre de l’étape de nuanceur. Par exemple, suivez le lien **Nuanceur de sommets obj:30** pour afficher le code source du nuanceur de sommets.

    > [!TIP]
    > Le numéro d’objet, **obj:30**, identifie ce nuanceur dans toute l’interface Graphics Analyzer, par exemple dans la table des objets et la fenêtre Historique des pixels.

#### <a name="to-debug-a-shader"></a>Pour déboguer un nuanceur

- Dans la fenêtre **Étapes de canalisation Graphics**, localisez l’étape de nuanceur qui correspond au nuanceur que vous souhaitez déboguer. Puis, sous l’image d’aperçu, choisissez **Démarrer le débogage**. La valeur par défaut de ce point d'entrée dans le débogueur HLSL correspond au premier appel du nuanceur pour l'étape correspondante, c'est-à-dire le premier pixel, le premier sommet ou la première primitive traitée par le nuanceur durant cet appel de dessin. Les appels de ce nuanceur pour un pixel ou un sommet spécifique sont accessibles via la fenêtre **Historique des pixels Graphics**.

### <a name="the-pipeline-stages"></a>Étapes de canalisation
 La fenêtre Étapes de canalisation affiche uniquement les étapes de canalisation actives durant l'appel de dessin. Chaque étape de canalisation Graphics transforme l'entrée de l'étape précédente et passe le résultat à l'étape suivante. La première étape (Assembleur d’entrée) récupère les données d’index et de sommet de votre application en entrée. La toute dernière étape (Fusion de sortie) combine les pixels qui viennent d’être rendus au contenu actuel du tampon de frame ou de la cible de rendu en tant que sortie pour produire l’image finale que vous voyez sur votre écran.

> [!NOTE]
> Les nuanceurs de calcul ne sont pas pris en charge dans la fenêtre **Étapes de canalisation Graphics**.

 **Assembleur d’entrée** L’assembleur d’entrée lit les données d’index et de vertex spécifiées par votre application et les assemble pour le matériel graphique.

 Dans la fenêtre Étapes de canalisation, la sortie de l'assembleur d'entrée est affichée sous la forme d'un modèle filaire. Pour mieux examiner le résultat, sélectionnez **Assembleur d’entrée** dans la fenêtre **Étapes de canalisation Graphics** afin d’afficher les sommets assemblés entièrement en 3D à l’aide de l’éditeur de modèle.

> [!NOTE]
> Si la sémantique `POSITION` n’est pas présente dans la sortie de l’assembleur d’entrée, rien ne s’affiche à l’étape **Assembleur d’entrée**.

 **Nuanceur de sommets** L’étape vertex shader traite les vertex, en effectuant généralement des opérations telles que la transformation, l’apparence et l’éclairage. Les nuanceurs de sommets produisent le même nombre de sommets que ceux qu'ils acceptent en entrée.

 Dans la fenêtre Étapes de canalisation, la sortie du nuanceur de sommets est affichée sous la forme d'une image raster filaire. Pour mieux examiner le résultat, sélectionnez **Nuanceur de sommets** dans la fenêtre **Étapes de canalisation Graphics** afin d’afficher les sommets traités dans l’éditeur d’images.

> [!NOTE]
> Si la sémantique `POSITION` ou `SV_POSITION` n’est pas présente dans la sortie du nuanceur de sommets, rien ne s’affiche à l’étape **Nuanceur de sommets**.

 **Nuanceur de coque** (Direct3D 11 et Direct3D 12 uniquement) la phase nuanceur de coque traite les points de contrôle qui définissent une surface de poids faible, telle qu’une ligne, un triangle ou un quadruple. En sortie, il génère un correctif de géométrie de poids supérieur et des constantes de correction qui sont passés à l’étape de pavage à fonction fixe.

 L'étape du nuanceur de coque n'est pas affichée dans la fenêtre Étapes de canalisation.

 **Étape du paveur** (Direct3D 11 et Direct3D 12 uniquement) l’étape du paveur est une unité matérielle à fonction fixe (non programmable) qui prétraite le domaine représenté par la sortie du nuanceur de coque. En sortie, il crée un modèle d’échantillonnage du domaine et un ensemble de primitives plus petites (points, lignes, triangles) qui connectent ces exemples.

 L'étape du paveur n'est pas affichée dans la fenêtre Étapes de canalisation.

 **Nuanceur de domaine** (Direct3D 11 et Direct3D 12 uniquement) l’étape du nuanceur de domaine traite les correctifs de géométrie de poids supérieur du nuanceur de coque, ainsi que les facteurs de pavage de l’étape de pavage. Les facteurs de pavage peuvent inclure les facteurs d'entrée du paveur, ainsi que les facteurs de sortie. En sortie, cette étape calcule la position du sommet d'un point dans le correctif de sortie en fonction des facteurs du paveur.

 L'étape du nuanceur de domaine n'est pas affichée dans la fenêtre Étapes de canalisation.

 **Nuanceur Geometry** L’étape de nuanceur Geometry traite les primitives entières (points, lignes ou triangles), ainsi que les données de vertex facultatives pour les primitives adjacentes au bord. Contrairement aux nuanceurs de sommets, les nuanceurs de géométries peuvent produire plus ou moins de primitives que ce qu'ils acceptent en entrée.

 Dans la fenêtre Étapes de canalisation, la sortie du nuanceur de géométrie est affichée sous la forme d'une image raster filaire. Pour mieux examiner le résultat, sélectionnez **Nuanceur de géométrie** dans la fenêtre **Étapes de canalisation Graphics** afin d’afficher les primitives traitées dans l’éditeur d’images.

 **Étape de sortie de flux** L’étape de sortie de flux peut intercepter les primitives transformées avant la pixellisation et les écrire dans la mémoire ; à partir de là, les données peuvent être redistribuées en entrée à des étapes antérieures du pipeline graphique ou être lues par l’UC.

 L'étape de sortie de flux n'est pas affichée dans la fenêtre Étapes de canalisation.

 **Étape de rastérisation** L’étape de rastérisation est une unité matérielle à fonction fixe (non programmable) qui convertit les primitives de vecteurs (points, lignes, triangles) en une image raster en effectuant une conversion de ligne d’analyse. Durant la rastérisation, les sommets sont transformés dans l'espace de détourage, puis détourés. En sortie, les nuanceurs de pixels sont mappés. Par ailleurs, les attributs de chaque sommet sont interpolés dans la primitive et préparés pour le nuanceur de pixels.

 L'étape du rastériseur n'est pas affichée dans la fenêtre Étapes de canalisation.

 **Nuanceur de pixels** L’étape nuanceur de pixels traite les primitives pixellisées en même temps que les données de vertex interpolées pour générer des valeurs par pixel telles que la couleur et la profondeur.

 Dans la fenêtre Étapes de canalisation, la sortie du nuanceur de pixels est affichée sous la forme d'une image raster en couleurs. Pour mieux examiner le résultat, sélectionnez **Nuanceur de pixels** dans la fenêtre **Étapes de canalisation Graphics** afin d’afficher les primitives traitées dans l’éditeur d’images.

 **Fusion de sortie** L’étape de fusion de sortie combine l’effet des pixels qui viennent d’être rendus, ainsi que le contenu existant de leurs mémoires tampons correspondantes (couleur, profondeur et gabarit) pour produire de nouvelles valeurs dans ces mémoires tampons.

 Dans la fenêtre Étapes de canalisation, la sortie de la fusion de sortie est affichée sous la forme d’une image raster en couleurs. Pour mieux examiner les résultats, sélectionnez **Fusion de sortie** dans la fenêtre **Étapes de canalisation Graphics** afin d’afficher le tampon de frame fusionné.

### <a name="vertex-and-geometry-shader-preview"></a>Aperçu du nuanceur de sommets et de géométrie
 Lorsque vous sélectionnez l’étape nuanceur de vertex ou Geometry dans la fenêtre **étapes de canalisation** , vous pouvez afficher les entrées et sorties du nuanceur dans le panneau ci-dessous.  Vous y trouverez des informations sur la liste des vertex fournis aux nuanceurs une fois qu’ils ont été assemblés par l’étape assembleur d’entrée.

 ![Visionneuse de mémoire tampon d'entrée de l'étape du nuanceur de sommets](media/gfx_diag_vertex_shader_inbuffers.png)

 Pour afficher le résultat de l'étape du nuanceur de sommets, choisissez la miniature de l'étape Nuanceur de sommets afin d'accéder à une image filaire rastérisée en taille réelle du maillage après sa transformation par le nuanceur de sommets.

 ![Aperçu du résultat de l'étape du nuanceur de sommets](media/gfx_diag_vertex_shader_preview.png)

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : objets manquants en raison de l’ombrage de vertex](walkthrough-missing-objects-due-to-vertex-shading.md)
- [Procédure pas à pas : débogage des erreurs de rendu dues à l’ombrage](walkthrough-debugging-rendering-errors-due-to-shading.md)