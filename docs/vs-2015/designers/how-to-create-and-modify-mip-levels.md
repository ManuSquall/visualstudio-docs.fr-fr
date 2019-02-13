---
title: 'Procédure : Créer et modifier les niveaux MIP | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6495f9271114be5fcd35e38d9ed210e07a8b6f66
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774060"
---
# <a name="how-to-create-and-modify-mip-levels"></a>Guide pratique pour créer et modifier les niveaux MIP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ce document montre comment utiliser l’**Éditeur d’images** pour générer et modifier des *niveaux MIP* pour le niveau de détail de l’espace de texture.  
  
## <a name="generating-mip-levels"></a>Génération de niveaux MIP  
 Le *mappage MIP* est une technique utilisée pour augmenter la vitesse de rendu et réduire les artefacts de crénelage sur les objets texturés, consistant à précalculer et à stocker plusieurs copies d’une texture en différentes tailles. Chaque copie, appelée un niveau MIP, correspond à la moitié de la largeur et de la hauteur de la copie précédente. Quand une texture est rendue sur la surface d’un objet, le niveau MIP qui correspond le mieux à la zone d’espace de l’écran de la surface texturée est choisi automatiquement. Cela signifie que le matériel pour le rendu graphique n’a pas besoin de filtrer les textures surdimensionnées pour maintenir une qualité d’affichage cohérente. Bien que le coût en mémoire du stockage des niveaux MIP soit d’environ 33 % supérieur à celui de la texture d’origine seule, les gains en matière de performances et de qualité d’image le justifient.  
  
#### <a name="to-generate-mip-levels"></a>Pour générer des niveaux MIP  
  
1.  Commencez par une texture de base, comme décrit dans [Guide pratique pour créer une texture de base](../designers/how-to-create-a-basic-texture.md). Pour de meilleurs résultats, spécifiez une texture qui a une largeur et une hauteur qui sont une puissance de deux, par exemple, 256, 512, 1 024, etc.  
  
2.  Générez les niveaux MIP. Sur la barre d’outils **Mode de l’éditeur d’images**, choisissez **Avancé**, **Outils**, **Générer les mips**.  
  
     Notez que les boutons **Accéder au niveau MIP suivant** et **Accéder au niveau MIP précédent** apparaissent désormais dans la barre d’outils **Mode de l’éditeur d’images**. Si la fenêtre **Propriétés** est affichée, notez également que les propriétés en lecture seule **Niveau MIP** et **Nombre de niveaux MIP** apparaissent désormais dans les propriétés de l’image.  
  
## <a name="modifying-mip-levels"></a>Modification des niveaux MIP  
 Pour obtenir des effets spéciaux ou améliorer la qualité de l’image à des niveaux spécifiques de détail, vous pouvez modifier individuellement chaque niveau MIP. Par exemple, vous pouvez attribuer à un objet texturé une apparence différente à distance (une distance plus grande correspond à des niveaux MIP plus petits), ou vous pouvez faire en sorte que les textures contenant du texte ou des symboles restent lisibles même à des niveaux MIP plus petits.  
  
#### <a name="to-modify-an-individual-mip-level"></a>Pour modifier un niveau MIP individuel  
  
1.  Sélectionnez le niveau MIP que vous voulez modifier. Sur la barre d’outils **Mode de l’éditeur d’images**, utilisez les boutons **Accéder au niveau MIP suivant** et **Accéder au niveau MIP précédent** pour vous déplacer entre les niveaux MIP.  
  
2.  Après avoir sélectionné le niveau MIP que vous voulez modifier, vous pouvez utiliser les outils de dessin pour le modifier sans changer le contenu d’autres niveaux MIP. Les outils de dessin sont disponibles sur la barre d’outils **Éditeur d’images**. Après avoir sélectionné un outil, vous pouvez modifier ses propriétés dans la fenêtre **Propriétés**. Pour plus d’informations sur les outils de dessin et leurs propriétés, consultez [Éditeur d’images](../designers/image-editor.md).  
  
> [!NOTE]
>  Si vous n’avez pas besoin de modifier le contenu de niveaux MIP individuels, ce que vous pouvez faire pour obtenir certains effets, nous vous recommandons de générer des mappages MIP à partir de la texture source au moment de la génération. Ceci permet de garantir que les niveaux MIP restent synchronisés avec la texture source, car les modifications apportées à un niveau MIP ne sont pas propagées automatiquement vers les autres niveaux. Pour plus d’informations sur la façon de générer des mipmaps au moment de la génération, consultez [Comment : exporter une texture qui contient des mipmaps](../designers/how-to-export-a-texture-that-contains-mipmaps.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer une texture de base](../designers/how-to-create-a-basic-texture.md)
