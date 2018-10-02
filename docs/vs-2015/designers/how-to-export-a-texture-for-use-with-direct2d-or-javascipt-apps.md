---
title: Guide pratique pour exporter une texture à utiliser avec des applications Javascript ou Direct2D | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b064620174a3a64194eee3ae18bffbe330ece13b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504046"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps"></a>Guide pratique pour exporter une texture à utiliser avec des applications Javascript ou Direct2D
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : exporter une Texture à utiliser avec Direct2D applications JavaScript ou Direct2d](https://docs.microsoft.com/visualstudio/designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps).  
  
Le pipeline de contenus d’image peut générer des textures compatibles avec les conventions de rendu interne de Direct2D. Les textures de ce type sont appropriées pour une utilisation dans les applications qui utilisent Direct2D et dans les applications du Windows Store créées à l’aide de JavaScript.  
  
 Ce document illustre ces activités :  
  
-   Configuration de l’image source à traiter par le pipeline de contenus d’image.  
  
-   Configuration du pipeline de contenus d’image pour générer une texture utilisable dans une application Direct2D ou Javascript.  
  
    -   Générer un fichier .dds compressé au niveau des blocs.  
  
    -   Générer une valeur alpha prémultipliée.  
  
    -   Désactiver la génération de mipmap.  
  
## <a name="rendering-conventions-in-direct2d"></a>Conventions de rendu dans Direct2D  
 Les textures qui sont utilisés dans le contexte de Direct2D doivent respecter ces conventions de rendu interne de Direct2D :  
  
-   Direct2D implémente la transparence et la translucidité en utilisant une valeur alpha prémultipliée. Les textures utilisées avec Direct2D doivent contenir une valeur alpha prémultipliée, même si la texture n’utilise pas la transparence ou la translucidité. Pour plus d’informations sur la valeur alpha prémultipliée, consultez [Guide pratique pour exporter une texture qui a des valeurs alpha prémultipliées](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).  
  
-   La texture doit être fournie au format .dds, en utilisant un de ces formats de compression de bloc :  
  
    -   Compression BC1_UNORM  
  
    -   Compression BC2_UNORM  
  
    -   Compression BC3_UNORM  
  
-   Les mipmaps ne sont pas pris en charge.  
  
#### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Pour créer une texture compatible avec les conventions de rendu de Direct2D  
  
1.  Commencez par une texture de base. Charger une image existante ou créez-en une comme décrit dans [Guide pratique pour créer une texture de base](../designers/how-to-create-a-basic-texture.md). Pour prendre en charge la compression de bloc au format .dds, spécifiez une texture qui a une largeur et une hauteur qui sont des multiples de quatre en taille, par exemple 100x100, 128x128 ou 256x192. Le mappage MIP n’étant pas pris en charge, la texture n’a pas besoin d’être carrée et ni d’être une puissance de deux en taille.  
  
2.  Configurez le fichier de texture pour qu’il soit traité par le pipeline de contenus d’image. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel pour le fichier de texture que vous venez de créer puis choisissez **Propriétés**. Dans la page **Propriétés de configuration**, **Général**, définissez la propriété **Type d’élément** sur **Pipeline de contenus d’image**. Vérifiez que la propriété **Contenu** est définie sur **Oui** et que **Exclure de la génération** est défini sur **Non**, puis choisissez le bouton **Appliquer**. La page des propriétés de configuration du **Pipeline de contenus d’image** apparaît.  
  
3.  Définissez le format de sortie sur un des formats de compression de blocs. Dans la page **Propriétés de configuration**, **Pipeline de contenus d’image**, **Général**, définissez la propriété **Compresser** sur **Compression BC3_UNORM (/compress:BC3_UNORM)**. Vous pouvez choisir un des autres formats BC1, BC2 ou BC3, selon vos besoins. Direct2D ne prend actuellement pas en charge les textures BC4, BC5, BC6 ou BC7. Pour plus d’informations sur les différents formats BC, consultez [Block Compression (Direct3D 10)](http://msdn.microsoft.com/library/windows/desktop/bb694531.aspx).  
  
    > [!NOTE]
    >  Le format de compression spécifié détermine le format du fichier produit par le pipeline de contenus d’image. Ceci est différent de la propriété **Format** de l’image source dans l’éditeur d’images, qui détermine le format du fichier image source stocké sur le disque, c’est-à-dire le *format de travail*. En règle générale, vous ne voulez pas qu’un format de travail soit compressé.  
  
4.  Configurez le pipeline de contenus d’image pour produire une sortie qui utilise une valeur alpha prémultipliée. Dans la page **Propriétés de configuration**, **Pipeline de contenus d’image**, **Général**, définissez la propriété **Convertir au format alpha prémultiplié** sur **Oui (/generatepremultipliedalpha)**.  
  
5.  Configurez le pipeline de contenus d’image pour qu’il ne génère pas de mipmaps. Dans la page **Propriétés de configuration**, **Pipeline de contenus d’image**, **Général**, définissez la propriété **Générer des mips** sur **Non**.  
  
6.  Sélectionnez le bouton **OK** .  
  
 Quand vous générez le projet, le pipeline de contenus d’image convertit l’image source du format de travail vers le format de sortie que vous avez spécifié (la conversion inclut la génération d’une valeur alpha prémultipliée) et le résultat est copié dans le répertoire de sortie du projet.



