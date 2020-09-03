---
title: Exporter une texture pour les applications Direct2D et JavaScript
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 546f7255b1c2846bdbd05bba0593b30bad9beacd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85769001"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascript-apps"></a>Comment : exporter une texture pour l’utiliser avec des applications Direct2D ou JavaScript

Le pipeline de contenus d’image peut générer des textures compatibles avec les conventions de rendu interne de Direct2D. Les textures de ce type sont appropriées pour une utilisation dans les applications qui utilisent Direct2D et dans les applications UWP créées à l’aide de JavaScript.

Ce document illustre ces activités :

- Configuration de l’image source à traiter par le pipeline de contenus d’image.

- Configuration du pipeline de contenus d’image pour générer une texture utilisable dans une application Direct2D ou Javascript.

  - Générez un fichier *. DDS* compressé par bloc.

  - Générer une valeur alpha prémultipliée.

  - Désactiver la génération de mipmap.

## <a name="rendering-conventions-in-direct2d"></a>Conventions de rendu dans Direct2D

Les textures qui sont utilisés dans le contexte de Direct2D doivent respecter ces conventions de rendu interne de Direct2D :

- Direct2D implémente la transparence et la translucidité en utilisant une valeur alpha prémultipliée. Les textures utilisées avec Direct2D doivent contenir une valeur alpha prémultipliée, même si la texture n’utilise pas la transparence ou la translucidité. Pour plus d’informations sur la valeur alpha prémultipliée, consultez [Comment : exporter une texture qui a des caractères alpha prémultipliés](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).

- La texture doit être fournie au format *. DDS* , en utilisant l’un de ces formats de compression de bloc :

  - Compression BC1_UNORM

  - Compression BC2_UNORM

  - Compression BC3_UNORM

- Les mipmaps ne sont pas pris en charge.

### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Pour créer une texture compatible avec les conventions de rendu de Direct2D

1. Commencez par une texture de base. Chargez une image existante ou créez-en une comme décrit dans [procédure : créer une texture de base](../designers/how-to-create-a-basic-texture.md). Pour prendre en charge la compression de bloc au format *. DDS* , spécifiez une texture qui a une largeur et une hauteur qui sont des multiples de quatre en taille, par exemple 100x100, 128 x 128 ou 256x192. Le mappage MIP n’étant pas pris en charge, la texture n’a pas besoin d’être carrée et ni d’être une puissance de deux en taille.

2. Configurez le fichier de texture pour qu’il soit traité par le pipeline de contenus d’image. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel pour le fichier de texture que vous venez de créer puis choisissez **Propriétés**. Dans la page **Propriétés de configuration**  >  **général** , définissez la propriété **type d’élément** sur **pipeline de contenu d’image**. Vérifiez que la propriété **Contenu** est définie sur **Oui** et que **Exclure de la génération** est défini sur **Non**, puis choisissez le bouton **Appliquer**. La page des propriétés de configuration du **Pipeline de contenus d’image** apparaît.

3. Définissez le format de sortie sur un des formats de compression de blocs. Dans la **page Propriétés de configuration**  >  **pipeline de contenu d’image**  >  **général** , définissez la propriété **compresser** sur **BC3_UNORM compression (/Compress : BC3_UNORM)**. Vous pouvez choisir un des autres formats BC1, BC2 ou BC3, selon vos besoins. Direct2D ne prend actuellement pas en charge les textures BC4, BC5, BC6 ou BC7. Pour plus d’informations sur les différents formats BC, consultez [compression par bloc (Direct3D 10)](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-resources-block-compression).

   > [!NOTE]
   > Le format de compression spécifié détermine le format du fichier produit par le pipeline de contenus d’image. Ceci est différent de la propriété **Format** de l’image source dans l’éditeur d’images, qui détermine le format du fichier image source stocké sur le disque, c’est-à-dire le *format de travail*. En règle générale, vous ne voulez pas qu’un format de travail soit compressé.

4. Configurez le pipeline de contenus d’image pour produire une sortie qui utilise une valeur alpha prémultipliée. Dans la page **Propriétés de configuration**  >  **pipeline de contenu d’image**  >  **général** , définissez la propriété **convertir au format alpha prémultiplié** sur **Oui (/generatepremultipliedalpha)**.

5. Configurez le pipeline de contenus d’image pour qu’il ne génère pas de mipmaps. Dans la **page Propriétés de configuration**  >  **pipeline de contenu d’image**  >  **général** , définissez la propriété **générer des mips** sur **non**.

6. Choisissez le bouton **OK**.

   Quand vous générez le projet, le pipeline de contenus d’image convertit l’image source du format de travail dans le format de sortie que vous avez spécifié (la conversion inclut la génération d’une valeur alpha prémultipliée) et le résultat est copié dans le répertoire de sortie du projet.
