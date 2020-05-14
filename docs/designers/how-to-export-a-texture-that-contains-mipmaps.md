---
title: Guide pratique pour exporter une texture qui contient des mipmaps
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71d570e6dc7544911ebe2bb279aafb3a07620cbc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589407"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Guide pratique pour exporter une texture qui contient des mipmaps

Le pipeline de contenus d’image peut générer des mipmaps à partir d’une image source dans la phase de génération de votre projet. Pour obtenir certains effets, vous devez parfois spécifier le contenu de l’image de chaque niveau MIP manuellement. Lorsque vous n’avez pas besoin de spécifier manuellement le contenu image de chaque niveau MIP, la génération de mipmaps au moment de la construction garantit que le contenu du mipmap ne devient jamais désynchronisé. Il élimine également le coût de performance de la génération de mipmaps au moment de l’exécution.

Cet article couvre les points suivants :

- Configuration de l’image source à traiter par le pipeline de contenus d’image.

- Configuration du pipeline de contenus d’image pour générer des mipmaps.

## <a name="export-mipmaps"></a>Exporter les mipmaps

Le mipmapping fournit automatiquement le niveau de détail de l’espace à l’écran pour les surfaces texturées dans une application ou un jeu 3D. Il améliore les performances du rendu d’un jeu ou d’une application en précalculant des versions sous-échantillonnées d’une texture. Le précalcul de versions sous-échantillonnées signifie que toute la texture ne doit pas être sous-échantillonnée chaque fois qu’elle est échantillonnée.

### <a name="to-export-a-texture-that-has-mipmaps"></a>Pour exporter une texture contenant des mipmaps

1. Commencez par une texture de base. Chargez un fichier image existant ou créez-en un comme décrit dans [Guide pratique pour créer une texture de base](../designers/how-to-create-a-basic-texture.md). Pour prendre en charge les mipmaps, spécifiez une texture dont la largeur et la hauteur ont pour valeur la même puissance de deux (par exemple : 64x64, 256x256 ou 512x512).

2. Configurez le fichier de texture que vous venez de créer pour qu’il soit traité par le pipeline de contenus d’image. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le fichier de texture que vous avez créé, puis choisissez **Propriétés**. Sur la page **Configuration Properties** > **General,** définissez la propriété **de type article** sur le pipeline de **contenu d’image**. Vérifiez que la propriété **Contenu** est définie sur **Oui** et que **Exclure de la génération** est défini sur **Non**. Sélectionnez **Appliquer**.

   La page des propriétés de configuration du **Pipeline de contenus d’image** apparaît.

3. Configurez le pipeline de contenus d’image pour générer des mipmaps. Sur la page **Configuration Properties** > **Image Content Pipeline** > **General,** définissez la propriété **Generate Mips** à Yes **(/generatemips).**

4. Sélectionnez **OK**.

Quand vous générez le projet, le pipeline de contenus d’image convertit l’image source du format de travail dans le format de sortie que vous avez spécifié, notamment les niveaux MIP. Le résultat est copié dans le répertoire de sortie du projet.
