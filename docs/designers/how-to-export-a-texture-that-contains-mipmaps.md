---
title: "Comment&#160;: exporter une texture qui contient des mipmaps | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 7
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 7
---
# Comment&#160;: exporter une texture qui contient des mipmaps
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le pipeline de contenu d'image peut générer des mipmaps à partir d'une image source dans le cadre de la phase de génération de votre projet.  Lorsque vous n'avez pas besoin de spécifier le contenu en image de chaque niveau MIP manuellement – comme ce pourrait être le cas pour obtenir certains effets – la génération des mipmaps au moment de la génération garantit que les contenus des mipmaps ne sont jamais désynchronisés et élimine le coût des performances de la génération des mipmaps au moment de l'exécution.  
  
 Ce document démontre les activités suivantes :  
  
-   Configurer l'image source de sorte qu'elle soit traitée par le pipeline de contenu d'image.  
  
-   Configurer le pipeline de contenu d'image pour générer des mipmap.  
  
## Exportation de mipmaps  
 Le mappage MIP fournit un niveau de détail automatique dans l'espace à l'écran pour les surfaces texturisées dans un jeu ou une application 3D.  Il améliore les performances de rendu d'un jeu ou d'une application en précalculant les versions sous\-échantillonnées d'une texture afin qu'il ne soit pas nécessaire de sous\-échantillonner la texture entière à chaque échantillonnage.  
  
#### Pour exporter une texture qui a des mipmaps  
  
1.  Démarrez avec une texture de base.  Chargez un fichier image existant, ou créez\-en un comme décrit dans [Comment : créer une texture de base](../Topic/How%20to:%20Create%20a%20Basic%20Texture.md).  Pour prendre en charge les mipmaps, spécifiez une texture qui a une largeur et une hauteur qui ont la même puissance de deux en taille, par exemple, 64x64, 256x256, ou 512x512.  
  
2.  Configurez le fichier de texture que vous venez de créer afin qu'il soit traité par le pipeline de contenu d'image.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel du fichier de texture que vous venez de créer, puis choisissez **Propriétés**.  Dans la page **Propriétés de configuration**, **Général**, affectez à la propriété **Type d'élément** la valeur **Pipeline de contenu d'image**.  Assurez\-vous que la propriété **Contenu** a la valeur **Oui** et que **Exclu de la génération** a la valeur **Non**, puis cliquez sur le bouton **Appliquer**.  La page de propriétés de configuration **Pipeline de contenu d'image** s'affiche.  
  
3.  Configurez le pipeline de contenu d'image pour générer des mipmap.  Dans la page **Propriétés de configuration**, **Pipeline de contenu d'image**, **Général**, affectez à la propriété **Générer des mips** la valeur **Oui \(\/generatemips\)**.  
  
4.  Cliquez sur le bouton **OK**.  
  
 Lorsque vous générez le projet, le pipeline de contenu d'image convertit l'image source depuis le format de travail vers le format de sortie que vous avez spécifié, niveaux MIP inclus, et le résultat est copié dans le répertoire de sortie du projet.