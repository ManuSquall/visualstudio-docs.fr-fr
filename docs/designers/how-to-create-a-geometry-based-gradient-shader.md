---
title: "Comment&#160;: cr&#233;er un nuanceur de g&#233;om&#233;trie d&#233;grad&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
caps.latest.revision: 18
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 18
---
# Comment&#160;: cr&#233;er un nuanceur de g&#233;om&#233;trie d&#233;grad&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ce document montre comment utiliser le concepteur Shader et le langage DGSL \(Directed Graph Shader Language\) pour créer un nuanceur de dégradé basé sur la géométrie.  Ce nuanceur mesure une valeur de couleur RVB constante grâce à la hauteur de chaque point d'un objet dans l'espace universel.  
  
 Ce document démontre les activités suivantes :  
  
-   Ajout de nœuds dans un graphique shader  
  
-   Définition des propriétés du nœud  
  
-   Déconnexion de nœuds  
  
-   Connexion de nœuds  
  
## Création d'un shader de dégradé basé sur la géométrie  
 Vous pouvez implémenter un shader basé sur la géométrie en intégrant la position du pixel dans votre shader.  Dans les langages de shader, un pixel contient davantage d'informations que sa simple couleur et sa location sur un écran 2\-D.  Un pixel\- connu comme *un fragment* dans certains système est une collection de valeurs qui décrivent la surface qui correspond à un pixel.  Le shader décrit dans ce document utilise la hauteur de chaque pixel d'un objet 3D dans l'espace afin d'affecter la couleur de sortie finale du fragment.  
  
 Avant de commencer, assurez\-vous que la fenêtre **Propriétés** et que la **Boîte à outils** sont affichées.  
  
#### Pour créer un shader de dégradé basé sur la géométrie  
  
1.  Créez un shader DGSL à utiliser.  Pour plus d'informations sur l'ajout d'un shader DGSL à votre projet, consultez la section Mise en route dans [Concepteur Shader](../designers/shader-designer.md).  
  
2.  Déconnectez le nœud **Couleur du point** du nœud **Couleur finale**.  Choisissez le terminal **RGB** du nœud **Couleur du point**, puis choisissez **Rompre les liaisons**.  Le nœud ajouté à l'étape suivante bénéficie ainsi d'un espace supplémentaire.  
  
3.  Ajoutez un nœud **Multiplier** au graphique.  Dans **Boîte à outils**, sous **Math**, sélectionnez **Multiplier** et faites glisser cette option sur l'aire de conception.  
  
4.  Ajoutez un nœud **Vecteur de masque** au graphique.  Dans **Boîte à outils**, sous **Utilitaire**, sélectionnez **Vecteur de masque** et faites glisser cette option sur l'aire de conception.  
  
5.  Spécifiez les valeurs de masque pour le nœud **Vecteur de masque**.  En mode **Select**, sélectionnez le nœud **Vecteur de masque**, puis dans la fenêtre **Propriétés**, définissez la propriété **Vert \(Y\)** sur **True**, puis définissez les propriétés **Rouge \(X\)**, **Bleu \(Z\)** et **Alpha \(W\)** sur **False**.  Dans cet exemple, les propriétés **Rouge \(X\)**, **Vert \(Y\)** et **Bleu \(Z\)** correspondent aux composants x, y et z du nœud **Position du monde** et **Alpha \(W\)** n'est pas utilisé.  Comme **Vert \(Y\)** est défini à la valeur **True**, seul le composant y du vecteur d'entrée reste après qu'il soit masqué.  
  
6.  Ajoutez un nœud **Position universelle** au graphique.  Dans **Boîte à outils**, sous **Constantes**, sélectionnez **Position universelle** et faites glisser cette option sur l'aire de conception.  
  
7.  Masquez la position de l'espace universel du fragment.  En mode **Select**, déplacez le terminal **Sortie** du nœud **Position universelle** vers le terminal **Vecteur** du nœud **Vecteur de masque**.  Cette connexion masque la position du fragment pour ignorer les composants x et z.  
  
8.  Multipliez la constante de couleur RVB par la position de l'espace universel masquée.  Déplacez le terminal **RGB** du nœud **Couleur du Point** vers le terminal **Y** du nœud **Multiplier**, puis déplacez le terminal **Sortie** du nœud **Vecteur de masque** vers le terminal **X** du nœud **Multiplier**.  Cette connexion ajuste la valeur de couleur à la hauteur du pixel dans l'espace.  
  
9. Connectez la valeur de couleur mise à l'échelle à la couleur finale.  Déplacez le terminal **Sortie** du nœud **Multiplier** vers le terminal **RVB** du nœud **Couleur finale**.  
  
 L'illustration suivante montre le graphique de nuanceur terminé et un aperçu du nuanceur appliqué à une sphère.  
  
> [!NOTE]
>  Dans cette illustration, une couleur orange est spécifiée pour mieux illustrer l'effet du nuanceur, mais comme la forme d'aperçu n'a aucune position dans l'espace universel, le nuanceur ne peut pas être prévisualisé dans le Concepteur Shader.  Le nuanceur doit être prévisualisé dans une scène réelle afin d'illustrer l'effet complet.  
  
 ![Graphique du nuanceur et un aperçu de ses effets](../designers/media/digit-gradient-effect-graph.png "Digit\-Gradient\-Effect\-Graph")  
  
 Certaines formes peuvent fournir de meilleurs aperçus pour certains nuanceurs.  Pour plus d'informations sur la prévisualisation des shader dans le Shader Designer, consultez **Previewing shaders**dans [Concepteur Shader](../designers/shader-designer.md)  
  
 L'illustration suivante montre le shader décrit dans ce document appliqué à la scène 3D qui est présentée dans [Procédure : modéliser un terrain 3D](../designers/how-to-model-3-d-terrain.md).  L'intensité de la couleur augmente avec la hauteur du point dans le monde.  
  
 ![Effet dégradé appliqué à un modèle de terrain 3 D](../designers/media/digit-gradient-effect-result.png "Digit\-Gradient\-Effect\-Result")  
  
 Pour plus d'informations sur l'application d'un nuanceur à un modèle 3D, consultez [Comment : appliquer un nuanceur à un modèle 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## Voir aussi  
 [Comment : appliquer un nuanceur à un modèle 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Procédure : exporter un nuanceur](../designers/how-to-export-a-shader.md)   
 [Procédure : modéliser un terrain 3D](../designers/how-to-model-3-d-terrain.md)   
 [Comment : créer un nuanceur de texture avec nuances de gris](../designers/how-to-create-a-grayscale-texture-shader.md)   
 [Concepteur Shader](../designers/shader-designer.md)   
 [Nœuds du concepteur Shader](../designers/shader-designer-nodes.md)