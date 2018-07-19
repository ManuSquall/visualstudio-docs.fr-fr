---
title: Graphique de canalisation | Documents Microsoft
ms.custom: ''
ms.date: 02/09/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.pipeline
ms.assetid: 2bf5c12e-2a00-401c-8163-4e373d08ad3f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c708320442c32158ef193ccf7f08669882135d82
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481299"
---
# <a name="graphics-pipeline-stages"></a>Étapes de canalisation Graphics
La fenêtre Étapes de canalisation Graphics vous permet de comprendre comment un appel de dessin individuel est transformé par chaque étape de canalisation graphismes Direct3D.  
  
 Voici la fenêtre Étapes de canalisation :  
  
 ![Un objet 3D traverse les étapes du pipeline.](media/gfx_diag_demo_pipeline_stages_orientation.png)
  
## <a name="understanding-the-graphics-pipeline-stages-window"></a>Présentation de la fenêtre Étapes de canalisation Graphics  
 La fenêtre Étapes de canalisation affiche le résultat de chaque étape de canalisation Graphics séparément, pour chaque appel de dessin. Normalement, les résultats des étapes de canalisation intermédiaires sont masqués, ce qui complique la tâche consistant à déterminer l'origine d'un problème de rendu. En affichant chaque étape séparément, la fenêtre Étapes de canalisation facilite l'identification de l'origine du problème. Par exemple, vous pouvez voir aisément le moment où l'étape du nuanceur de sommets provoque soudainement le dessin d'un objet hors de l'écran.  
  
 Une fois que vous avez identifié l'étape durant laquelle le problème se produit, vous pouvez utiliser les autres outils Graphics Analyzer pour examiner la façon dont les données ont été interprétées ou transformées. Les problèmes de rendu qui apparaissent aux étapes de canalisation sont souvent liés à des descripteurs de format de sommet incorrects, à des programmes de nuanceur bogués ou à un état mal configuré.  
  
### <a name="links-to-related-graphics-objects"></a>Liens vers les objets graphiques connexes  
 Parfois, un contexte supplémentaire est nécessaire pour déterminer la raison pour laquelle un appel de dessin interagit de façon spécifique avec la canalisation Graphics. Pour faciliter la recherche de ce contexte supplémentaire, la fenêtre Étapes de canalisation Graphics comporte des liens vers un ou plusieurs objets qui fournissent un contexte supplémentaire relatif à ce qui se passe dans la canalisation Graphics.  
  
-   Dans Direct3D 12, cet objet est généralement une liste de commandes.  
  
-   Dans Direct3D 11, cet objet est généralement un contexte de périphérique graphique.  
  
 Ces liens font partie de la signature d'événement Graphics actuelle dans le coin supérieur gauche de la fenêtre Étapes de canalisation Graphics. Suivez ces liens pour obtenir des détails supplémentaires sur l'objet.  
  
### <a name="viewing-and-debugging-shader-code"></a>Affichage et débogage du code du nuanceur  
 Vous pouvez examiner et déboguer le code des nuanceurs de sommets, de coques, de domaines, de géométries et de pixels à l'aide des contrôles situés au bas de leurs étapes respectives dans la fenêtre Étapes de canalisation.  
  
#### <a name="to-view-a-shaders-source-code"></a>Pour afficher le code source d'un nuanceur  
  
-   Dans le **étapes de canalisation Graphics** fenêtre, localisez l’étape de nuanceur qui correspond au nuanceur à examiner. Ensuite, sous l’image d’aperçu, suivez le lien de titre d’étape du nuanceur, par exemple, suivez le lien **nuanceur de sommets obj : 30** pour afficher le code source de nuanceur de sommets.  
  
    > [!TIP]
    >  Le numéro d’objet, **obj : 30**, identifie ce nuanceur dans toute l’interface Graphics Analyzer par exemple, dans la fenêtre d’historique de l’objet table et de pixels.  
  
#### <a name="to-debug-a-shader"></a>Pour déboguer un nuanceur  
  
-   Dans le **étapes de canalisation Graphics** fenêtre, localisez l’étape de nuanceur qui correspond au nuanceur à déboguer. Puis, sous l’image d’aperçu, choisissez **démarrer le débogage**. La valeur par défaut de ce point d'entrée dans le débogueur HLSL correspond au premier appel du nuanceur pour l'étape correspondante, c'est-à-dire le premier pixel, le premier sommet ou la première primitive traitée par le nuanceur durant cet appel de dessin. Appels de ce nuanceur pour un pixel spécifique ou un sommet est accessible via la **historique des pixels Graphics**.  
  
### <a name="the-pipeline-stages"></a>Étapes de canalisation  
 La fenêtre Étapes de canalisation affiche uniquement les étapes de canalisation actives durant l'appel de dessin. Chaque étape de canalisation Graphics transforme l'entrée de l'étape précédente et passe le résultat à l'étape suivante. La première étape (Assembleur d’entrée) récupère les données d’index et de sommet de votre application en entrée. La toute dernière étape (Fusion de sortie) combine les pixels qui viennent d’être rendus au contenu actuel du tampon de frame ou de la cible de rendu en tant que sortie pour produire l’image finale que vous voyez sur votre écran.  
  
> [!NOTE]
>  Les nuanceurs de calcul ne sont pas pris en charge dans les **étapes de canalisation Graphics** fenêtre.  
  
 **Assembleur d’entrée**  
 L'assembleur d'entrée lit les données d'index et de sommet spécifiées par votre application, et les assemble pour le matériel graphique.  
  
 Dans la fenêtre Étapes de canalisation, la sortie de l'assembleur d'entrée est affichée sous la forme d'un modèle filaire. Pour mieux examiner le résultat, sélectionnez **assembleur d’entrée** dans les **étapes de canalisation Graphics** fenêtre pour afficher les sommets assemblés entièrement en 3D à l’aide de l’éditeur de modèle.  
  
> [!NOTE]
>  Si le `POSITION` sémantique n’est pas présent dans la sortie de l’assembleur d’entrée, alors rien ne s’affiche dans le **assembleur d’entrée** étape.  
  
 **Nuanceur de sommets**  
 L'étape du nuanceur de sommets traite les sommets, en effectuant généralement des opérations telles que la transformation, l'application d'apparences et l'éclairage. Les nuanceurs de sommets produisent le même nombre de sommets que ceux qu'ils acceptent en entrée.  
  
 Dans la fenêtre Étapes de canalisation, la sortie du nuanceur de sommets est affichée sous la forme d'une image raster filaire. Pour mieux examiner le résultat, sélectionnez **nuanceur de sommets** dans les **étapes de canalisation Graphics** afin d’afficher les sommets traités dans l’éditeur d’images.  
  
> [!NOTE]
>  Si le `POSITION` ou `SV_POSITION` sémantique n’est pas présente dans la sortie du nuanceur de sommets, alors rien ne s’affiche dans le **nuanceur de sommets** étape.  
  
 **Nuanceur de coque** (Direct3D 11 et Direct3D 12 uniquement)  
 L'étape du nuanceur de coque traite les points de contrôle qui définissent une surface de poids faible comme une ligne, un triangle ou un quadrilatère. En sortie, il génère un correctif de géométrie de poids supérieur et des constantes de correction qui sont passés à l'étape de pavage à fonction fixe.  
  
 L'étape du nuanceur de coque n'est pas affichée dans la fenêtre Étapes de canalisation.  
  
 **Étape du paveur** (Direct3D 11 et Direct3D 12 uniquement)  
 L'étape du paveur est une unité matérielle à fonction fixe (non programmable) qui prétraite le domaine représenté par la sortie du nuanceur de coque. En sortie, il crée un modèle d'échantillonnage du domaine et un ensemble de primitives plus petites (points, lignes, triangles) qui connectent ces exemples.  
  
 L'étape du paveur n'est pas affichée dans la fenêtre Étapes de canalisation.  
  
 **Nuanceur de domaine** (Direct3D 11 et Direct3D 12 uniquement)  
 L’étape du nuanceur de domaine traite les correctifs de géométrie de poids supérieur du nuanceur de coque, ainsi que les facteurs de pavage de l’étape de pavage. Les facteurs de pavage peuvent inclure les facteurs d'entrée du paveur, ainsi que les facteurs de sortie. En sortie, cette étape calcule la position du sommet d'un point dans le correctif de sortie en fonction des facteurs du paveur.  
  
 L'étape du nuanceur de domaine n'est pas affichée dans la fenêtre Étapes de canalisation.  
  
 **Nuanceur de géométrie**  
 L'étape du nuanceur de géométrie traite les primitives entières (points, lignes ou triangles), ainsi que les données de sommet facultatives des primitives à bords adjacents. Contrairement aux nuanceurs de sommets, les nuanceurs de géométries peuvent produire plus ou moins de primitives que ce qu'ils acceptent en entrée.  
  
 Dans la fenêtre Étapes de canalisation, la sortie du nuanceur de géométrie est affichée sous la forme d'une image raster filaire. Pour mieux examiner le résultat, sélectionnez **nuanceur de géométrie** dans les **étapes de canalisation Graphics** fenêtre pour afficher les primitives traitées dans l’éditeur d’images.  
  
 **Étape de sortie de flux de données**  
 L'étape de sortie de flux peut intercepter les primitives transformées avant la rastérisation, et les écrire en mémoire. Les données peuvent ensuite être recyclées en entrée à des étapes antérieures de la canalisation Graphics, ou être relues par l'UC.  
  
 L'étape de sortie de flux n'est pas affichée dans la fenêtre Étapes de canalisation.  
  
 **Étape du rastériseur**  
 L'étape du rastériseur est une unité matérielle à fonction fixe (non programmable) qui convertit les primitives vectorielles (points, lignes, triangles) en image raster en effectuant une conversion de lignes de balayage. Durant la rastérisation, les sommets sont transformés dans l'espace de détourage, puis détourés. En sortie, les nuanceurs de pixels sont mappés. Par ailleurs, les attributs de chaque sommet sont interpolés dans la primitive et préparés pour le nuanceur de pixels.  
  
 L'étape du rastériseur n'est pas affichée dans la fenêtre Étapes de canalisation.  
  
 **Nuanceur de pixels**  
 L'étape du nuanceur de pixels traite les primitives rastérisées, ainsi que les données de sommet interpolées pour générer des valeurs spécifiques à chaque pixel, par exemple la couleur et la profondeur.  
  
 Dans la fenêtre Étapes de canalisation, la sortie du nuanceur de pixels est affichée sous la forme d'une image raster en couleurs. Pour mieux examiner le résultat, sélectionnez **nuanceur de pixels** dans les **étapes de canalisation Graphics** fenêtre pour afficher les primitives traitées dans l’éditeur d’images.  
  
 **Fusion de sortie**  
 L’étape de fusion de sortie combine l’effet des pixels qui viennent d’être rendus au contenu existant de leurs mémoires tampons correspondantes (couleur, profondeur et gabarit) pour produire de nouvelles valeurs dans ces mémoires tampons.  
  
 Dans la fenêtre Étapes de canalisation, la sortie de la fusion de sortie est affichée sous la forme d’une image raster en couleurs. Pour étudier les résultats, sélectionnez **fusion de sortie** dans les **étapes de canalisation Graphics** fenêtre pour afficher le tampon de frame fusionné.  
  
### <a name="vertex-and-geometry-shader-preview"></a>Aperçu du nuanceur de géométrie et de sommet  
 Lorsque vous sélectionnez l’étape du nuanceur de sommets ou de géométrie dans le **canalisation** , vous pouvez afficher les entrées et les sorties du nuanceur de dans le panneau de configuration ci-dessous.  Ici, vous trouverez plus d’informations sur la liste des sommets fournis pour les nuanceurs, une fois qu’ils ont été assemblés à l’étape de l’assembleur d’entrée.  

 ![Visionneuse de mémoire tampon d'entrée de l'étape du nuanceur de sommets](media/gfx_diag_vertex_shader_inbuffers.png)  
  
 Pour afficher le résultat de l'étape du nuanceur de sommets, choisissez la miniature de l'étape Nuanceur de sommets afin d'accéder à une image filaire rastérisée en taille réelle du maillage après sa transformation par le nuanceur de sommets.  
  
 ![Aperçu du résultat de l'étape du nuanceur de sommets](media/gfx_diag_vertex_shader_preview.png)  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Objets manquants en raison Vertex Shader](walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Procédure pas à pas : débogage des erreurs de rendu dues à l’ombrage](walkthrough-debugging-rendering-errors-due-to-shading.md)