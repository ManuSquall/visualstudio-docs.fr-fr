---
title: Guide pratique pour exporter une texture qui a des valeurs alpha prémultipliées | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6d15ac70fbbc9291dca32f25ed5f3c3378b6b848
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49239731"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Guide pratique pour exporter une texture qui a des valeurs alpha prémultipliées
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le pipeline de contenus d’image peut générer des textures alpha prémultipliées à partir d’une image source. Ces textures peuvent être plus faciles à utiliser et plus robustes que celles ne contenant pas de valeurs alpha prémultipliées.  
  
 Ce document illustre ces activités :  
  
-   Configuration de l’image source à traiter par le pipeline de contenus d’image.  
  
-   Configuration du pipeline de contenus d’image pour générer des valeurs alpha prémultipliées.  
  
## <a name="premultiplied-alpha"></a>Valeurs alpha prémultipliées  
 Valeurs alpha prémultipliées offre plusieurs avantages sur alpha conventionnel non prémultipliées, car il représente mieux l’interaction réelle de la lumière avec les matériaux physiques en séparant la contribution de texel color (couleur qu’il ajoute à la scène) de sa translucidité (la quantité de couleur sous-jacente qu’il laisse passer). L’utilisation de valeurs alpha prémultipliées présente les avantages suivants :  
  
-   Le mélange avec des données alpha prémultipliées est une opération associative ; le résultat du mélange de plusieurs textures translucides est identique, indépendamment de l’ordre dans lequel les textures sont mélangées.  
  
-   En raison de la nature associative du mélange avec les valeurs alpha prémultipliées, le rendu multipasse des objets translucides est simplifié.  
  
-   En utilisant des valeurs alpha prémultipliées, vous pouvez réaliser simultanément le mélange additif pur (en définissant la valeur alpha à zéro) et le mélange linéairement interpolé. Par exemple, dans un système de particules, une particule de feu mélangée peut devenir une particule de fumée translucide mélangée à en utilisant une interpolation linéaire. Sans valeur alpha prémultipliée, vous devriez dessiner les particules de feu séparément des particules de fumée, et modifier l’état de rendu entre les appels de dessin.  
  
-   Compresser les textures qui utilisent l’alpha prémultiplié avec une qualité supérieure que celles qui ne le font, et elles n’exposent pas les bords décolorés, ou « l’effet de halo », qui peut se produire lorsque vous fusionnez des textures qui n’utilisent des valeurs alpha prémultipliées.  
  
#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Pour créer une texture qui utilise des valeurs alpha prémultipliées  
  
1.  Commencez par une texture de base. Chargez un fichier image existant ou créez-en un comme décrit dans [Guide pratique pour créer une texture de base](../designers/how-to-create-a-basic-texture.md).  
  
2.  Configurer le fichier de texture afin qu’il soit traité par le Pipeline de contenus d’Image. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du fichier de texture, puis choisissez **Propriétés**. Dans la page **Propriétés de configuration**, **Général**, définissez la propriété **Type d’élément** sur **Pipeline de contenus d’image**. Vérifiez que la propriété **Contenu** est définie sur **Oui** et que **Exclure de la génération** est défini sur **Non**, puis choisissez le bouton **Appliquer**. La page des propriétés de configuration du **Pipeline de contenus d’image** apparaît.  
  
3.  Configurez le pipeline de contenus d’image pour générer des valeurs alpha prémultipliées. Dans la page **Propriétés de configuration**, **Pipeline de contenus d’image**, **Général**, définissez la propriété **Convertir au format alpha prémultiplié** sur **Oui (/generatepremultipliedalpha)**.  
  
4.  Sélectionnez le bouton **OK** .  
  
 Lorsque vous générez le projet, le Pipeline de contenus d’Image convertit l’image source du format de travail au format de sortie que vous avez spécifié – conversion incluse de l’image au format alpha prémultiplié, et le résultat est copié dans la sortie du projet répertoire.



