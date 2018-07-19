---
title: Guide pratique pour exporter une texture qui contient des mipmaps
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b2126f38053cc8f83be92aeb5d3939df07e58c2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31923325"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Guide pratique pour exporter une texture qui contient des mipmaps

Le pipeline de contenus d’image peut générer des mipmaps à partir d’une image source dans la phase de génération de votre projet. Pour obtenir certains effets, vous devez parfois spécifier le contenu de l’image de chaque niveau MIP manuellement. Quand vous n’avez pas besoin de spécifier le contenu de l’image de chaque niveau MIP manuellement, la génération de mipmaps au moment de la génération garantit que le contenu mipmap n’est jamais hors synchronisation. Elle élimine également le coût en matière de performances de la génération des mipmaps au moment de l’exécution.

Cet article couvre les sujets suivants :

- Configuration de l’image source à traiter par le pipeline de contenus d’image.

- Configuration du pipeline de contenus d’image pour générer des mipmaps.

## <a name="export-mipmaps"></a>Exporter les mipmaps

Le mipmapping fournit automatiquement le niveau de détail de l’espace à l’écran pour les surfaces texturées dans une application ou un jeu 3D. Il améliore les performances du rendu d’un jeu ou d’une application en précalculant des versions sous-échantillonnées d’une texture. Le précalcul de versions sous-échantillonnées signifie que toute la texture ne doit pas être sous-échantillonnée chaque fois qu’elle est échantillonnée.

### <a name="to-export-a-texture-that-has-mipmaps"></a>Pour exporter une texture contenant des mipmaps

1.  Commencez par une texture de base. Chargez un fichier image existant ou créez-en un comme décrit dans [Guide pratique pour créer une texture de base](../designers/how-to-create-a-basic-texture.md). Pour prendre en charge les mipmaps, spécifiez une texture dont la largeur et la hauteur ont pour valeur la même puissance de deux (par exemple : 64x64, 256x256 ou 512x512).

2.  Configurez le fichier de texture que vous venez de créer pour qu’il soit traité par le pipeline de contenus d’image. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le fichier de texture que vous avez créé, puis choisissez **Propriétés**. Dans la page **Propriétés de configuration** > **Général**, définissez la propriété **Type d’élément** sur **Pipeline de contenus d’image**. Vérifiez que la propriété **Contenu** est définie sur **Oui** et que **Exclure de la génération** est défini sur **Non**. Sélectionnez **Appliquer**.

   La page des propriétés de configuration du **Pipeline de contenus d’image** apparaît.

3.  Configurez le pipeline de contenus d’image pour générer des mipmaps. Dans la page **Propriétés de configuration** > **Pipeline de contenus d’image** > **Général**, définissez la propriété **Générer des mips** sur **Oui (/generatemips)**.

4.  Sélectionnez **OK**.

Quand vous générez le projet, le pipeline de contenus d’image convertit l’image source du format de travail dans le format de sortie que vous avez spécifié, notamment les niveaux MIP. Le résultat est copié dans le répertoire de sortie du projet.