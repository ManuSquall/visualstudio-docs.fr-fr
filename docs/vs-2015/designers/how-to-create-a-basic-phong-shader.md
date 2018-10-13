---
title: 'Comment : créer un nuanceur Phong de base | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c7c69da8-142b-4d3b-9be9-4be0d5970b25
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3ad96b9ed53b7600417f3c3e8a283c7a4a372842
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286492"
---
# <a name="how-to-create-a-basic-phong-shader"></a>Comment : créer un nuanceur Phong de base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ce document indique comment utiliser le concepteur de nuanceur et DGSL (Directed Graph Shader Language) pour créer un nuanceur d’éclairage implémentant le modèle d’éclairage Phong classique.  
  
 Ce document illustre ces activités :  
  
-   Ajout de nœuds à un graphique de nuanceur  
  
-   Déconnexion de nœuds  
  
-   Connexion de nœuds  
  
## <a name="the-phong-lighting-model"></a>Modèle d’éclairage Phong  
 Le modèle d’éclairage Phong étend le modèle d’éclairage Lambert pour inclure une mise en surbrillance spéculaire, ce qui simule les propriétés de reflet d’une surface. Le composant spéculaire fournit un éclairage supplémentaire provenant des mêmes sources de lumière directionnelle que celles qui sont utilisées dans le modèle d’éclairage Lambert, mais sa contribution à la couleur finale est traitée différemment. L’éclairage spéculaire affecte différemment chaque surface de la scène, en fonction de la relation entre la direction de l’affichage, la direction des sources de lumière et l’orientation de la surface. Il s’agit d’un produit de la couleur spéculaire, de la puissance spéculaire, de l’orientation de la surface, et de la couleur, de l’intensité et de la direction des sources de lumière. Les surfaces qui reflètent directement la source de lumière à la visionneuse reçoivent la contribution spéculaire maximale, tandis que celles qui reflètent la source de lumière distante de la visionneuse ne reçoivent aucune contribution. Dans le modèle d’éclairage Phong, un ou plusieurs composants spéculaires sont combinés pour déterminer la couleur et l’intensité de la mise en surbrillance spéculaire de chaque point de l’objet. Ils sont ensuite ajoutés au résultat du modèle d’éclairage Lambert pour produire la couleur finale du pixel.  
  
 Pour plus d’informations sur le modèle d’éclairage Lambert, consultez l’article [Comment : créer un nuanceur Lambert de base](../designers/how-to-create-a-basic-lambert-shader.md).  
  
 Avant de commencer, assurez-vous que la fenêtre **Propriétés** et la **Boîte à outils** sont affichées.  
  
#### <a name="to-create-a-phong-shader"></a>Pour créer un nuanceur Phong  
  
1.  Créez un nuanceur Lambert, en suivant la description de l’article [Comment : créer un nuanceur Lambert de base](../designers/how-to-create-a-basic-lambert-shader.md).  
  
2.  Déconnectez le nœud **Lambert** du nœud **Couleur finale**. Choisissez le terminal **RVB** du nœud **Lambert**, puis choisissez **Rompre les liaisons**. Le nœud ajouté à l'étape suivante bénéficie ainsi d'un espace supplémentaire.  
  
3.  Ajoutez un nœud **Ajouter** au graphique. Dans la **Boîte à outils**, sous **Math**, sélectionnez **Ajouter** et déplacez-le vers l’aire de conception.  
  
4.  Ajoutez un nœud **Spéculaire** au graphique. Dans la **Boîte à outils**, sous **Utilitaire**, sélectionnez **Spéculaire** et déplacez-le vers l’aire de conception.  
  
5.  Ajoutez la contribution spéculaire. Déplacez le terminal **Sortie** du nœud **Spéculaire** vers le terminal **X** du nœud **Ajouter**, puis le terminal **Sortie** du nœud **Lambert** vers le terminal **Y** du nœud **Ajouter**. Ces connexions combinent les contributions de couleur spéculaire et diffuse totale du pixel.  
  
6.  Connectez la valeur de couleur calculée à la couleur finale. Déplacez le terminal **Sortie** du nœud **Ajouter** vers le terminal **RVB** du nœud **Couleur finale**.  
  
 L’illustration suivante présente le graphique du nuanceur terminé ainsi qu’un aperçu du nuanceur appliqué à un modèle de théière.  
  
> [!NOTE]
>  Pour mettre en évidence l’effet du nuanceur dans cette illustration, une couleur orange a été spécifiée à l’aide du paramètre **MaterialDiffuse** du nuanceur, et un fini d’aspect métallique a été spécifié à l’aide des paramètres **MaterialSpecular** et **MaterialSpecularPower**. Pour plus d’informations sur les paramètres de matériau, consultez la section Aperçu des nuanceurs de l’article [Concepteur de nuanceur](../designers/shader-designer.md).  
  
 ![Graphique du nuanceur et aperçu de son effet](../designers/media/digit-lighting-graph.png "Digit-Lighting-Graph")  
  
 Certaines formes peuvent fournir de meilleurs aperçus pour certains nuanceurs. Pour plus d’informations sur l’aperçu des nuanceurs dans le concepteur de nuanceur, consultez la section Aperçu des nuanceurs de l’article [Concepteur de nuanceur](../designers/shader-designer.md).  
  
 L’illustration suivante présente le nuanceur, décrit dans ce document, appliqué à un modèle 3D. La propriété **MaterialSpecular** est définie sur (1,00, 0,50, 0,20, 0,00), et sa propriété **MaterialSpecularPower** est définie sur 16.  
  
> [!NOTE]
>  La propriété **MaterialSpecular** détermine le fini apparent du matériau de surface. Une surface haute brillance comme le verre ou le plastique a tendance à avoir une couleur spéculaire, autrement dit une nuance de blanc lumineuse. Une surface métallique a tendance à avoir une couleur spéculaire proche de sa couleur diffuse. Une surface satinée a tendance à avoir une couleur spéculaire, autrement dit une nuance de gris foncée.  
>   
>  La propriété **MaterialSpecularPower** détermine l’intensité des mises en surbrillance spéculaires. Des puissances très spéculaires simulent des mises en surbrillance plus ternes et plus localisées. Des puissances faiblement spéculaires simulent des mises en surbrillance intenses et de grande envergure qui peuvent saturer et masquer la couleur de la surface totale.  
  
 ![Éclairage Phong appliqué à un modèle](../designers/media/digit-lighting-model.png "Digit-Lighting-Model")  
  
 Pour plus d’informations sur l’application d’un nuanceur à un modèle 3D, consultez l’article [Comment : appliquer un nuanceur à un modèle 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : appliquer un nuanceur à un modèle 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Comment : exporter un nuanceur](../designers/how-to-export-a-shader.md)   
 [Comment : créer un nuanceur Lambert de base](../designers/how-to-create-a-basic-lambert-shader.md)   
 [Concepteur de nuanceur](../designers/shader-designer.md)   
 [Nœuds du concepteur Shader](../designers/shader-designer-nodes.md)



