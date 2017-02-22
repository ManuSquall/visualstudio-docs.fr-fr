---
title: "Comment&#160;: exporter une texture qui poss&#232;de des valeurs alpha pr&#233;multipli&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
caps.latest.revision: 4
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 4
---
# Comment&#160;: exporter une texture qui poss&#232;de des valeurs alpha pr&#233;multipli&#233;es
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le pipeline de contenu d'image peut générer des textures alpha prémultipliées à partir d'une image source.  Ils peuvent être plus simples à utiliser et plus fiables que les textures qui ne contiennent pas de données alpha prémultipliées.  
  
 Ce document démontre les activités suivantes :  
  
-   Configurer l'image source de sorte qu'elle soit traitée par le pipeline de contenu d'image.  
  
-   Configurer le pipeline de contenu d'image pour générer des données alpha prémultipliées.  
  
## Alpha prémultiplié  
 L'alpha prémultiplié offre plusieurs avantages par rapport à l'alpha conventionnel non prémultiplié, car il représente mieux l'interaction réelle de la lumière avec les matériaux physiques en séparant la contribution de couleur du texel \(la couleur qu'il ajoute à la scène\) de sa translucidité \(la quantité de couleur sous\-jacente qu'il laisse passer\).  L'utilisation de l'alpha prémultiplié présente les avantages suivants :  
  
-   Mélanger avec des données alpha prémultipliées est une opération associative ; le résultat du mélange de plusieurs textures translucides est identique, indépendamment de l'ordre dans lequel les textures sont mélangées.  
  
-   Étant donné la nature associative de la fusion avec l'alpha prémultiplié, le rendu multipasse des objets translucides est simplifié.  
  
-   En utilisant des données alpha prémultipliées, le mélange additif pur \(en définissant alpha à zéro\) et le mélange linéairement interpolé peuvent être réalisés simultanément.  Par exemple, dans un système de particules, une particule de feu fusionnée par ajout peut devenir une particule de fumée translucide fusionnée à l'aide de l'interpolation linéaire.  Sans alpha prémultiplié, vous devriez dessiner les particules de feu séparément des particules de fumée, et modifier l'état de rendu entre les appels de dessin.  
  
-   Les textures qui utilisent l'alpha prémultiplié compressent avec une qualité supérieure par rapport à celles qui ne l'utilisent pas, et elles n'exposent pas les bords décolorées ou « l'effet de halo » qui peut se produire lorsque vous fusionnez des textures qui n'utilisent pas l'alpha prémultiplié.  
  
#### Pour créer une texture qui utilise l'alpha prémultiplié  
  
1.  Démarrez avec une texture de base.  Chargez un fichier image existant, ou créez\-en un comme décrit dans [Comment : créer une texture de base](../Topic/How%20to:%20Create%20a%20Basic%20Texture.md).  
  
2.  Configurez le fichier de texture afin qu'il soit traité par le pipeline de contenu d'image.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel du fichier de texture, puis choisissez **Propriétés**.  Dans la page **Propriétés de configuration**, **Général**, affectez à la propriété **Type d'élément** la valeur **Pipeline de contenu d'image**.  Assurez\-vous que la propriété **Contenu** a la valeur **Oui** et que **Exclu de la génération** a la valeur **Non**, puis cliquez sur le bouton **Appliquer**.  La page de propriétés de configuration **Pipeline de contenu d'image** s'affiche.  
  
3.  Configurez le pipeline de contenu d'image pour générer des données alpha prémultipliées.  Dans la page **Propriétés de configuration**, **Pipeline de contenu d'image**, **Général**, affectez à la propriété **Convertir au format alpha prémultiplié** la valeur **Oui \(\/generatepremultipliedalpha\)**.  
  
4.  Cliquez sur le bouton **OK**.  
  
 Lorsque vous générez le projet, le pipeline de contenu d'image convertit l'image source depuis le format de travail vers le format de sortie que vous avez spécifié – conversion incluse de l'image au format alpha prémultiplié – et le résultat est copié dans le répertoire de sortie du projet.