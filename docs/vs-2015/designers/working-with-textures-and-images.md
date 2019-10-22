---
title: Utilisation des textures et des images | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 93813aa734c615e7f045c98c776e600be4ee3fab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663939"
---
# <a name="working-with-textures-and-images"></a>Utilisation des textures et des images
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser l’Éditeur d’images de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour créer et modifier des textures et des images. L’Éditeur d’images prend en charge les formats enrichis de textures et d’images, tels que ceux utilisés dans le développement d’applications DirectX.

> [!NOTE]
> L’Éditeur d’images ne prend pas en charge les images présentant une couleur faible, comme les icônes ou les curseurs. Pour créer ou modifier ces types d’images, utilisez l’outil [Image Editor for Icons](https://msdn.microsoft.com/library/586d2b8b-0348-4883-a85d-1ff0ddbf14dd).

## <a name="textures-and-images"></a>Textures et images
 Les textures et les images, à un niveau de base, sont uniquement des tableaux de données procurant des détails visuels dans les applications graphiques. Le type de détail fourni par une texture ou une image dépend de son utilisation. Par exemple, citons les échantillons de couleur, les valeurs alpha (transparentes), les normales à la surface, ou encore les valeurs de hauteur. Quelle est la principale différence entre une texture et une image ? En fait, une texture est conçue pour être utilisée avec une représentation de forme (généralement un modèle 3D) pour exprimer un objet ou une scène complets, tandis qu’une image est une représentation autonome d’un objet ou d’une scène.

 Les types courants de textures sont les suivants :

 Les mappages de texture plaqués de texture contiennent des valeurs de couleur qui sont organisées en tant que matrice à une, deux ou trois dimensions. Elles fournissent des détails de couleur sur l’objet affecté. Le groupe des couleurs, souvent codé à l’aide de canaux de couleurs RVB (rouge, vert, bleu), peut comporter une quatrième composante, alpha, qui représente la transparence. Plus rarement, les couleurs peuvent être codées suivant un modèle différent, ou le quatrième canal peut contenir des données non alpha, par exemple de hauteur.

 Mappages normaux les cartes normales contiennent des normales à la surface. Elles fournissent des détails d’éclairage sur l’objet affecté. Généralement, les normales sont codées suivant le modèle RVB (rouge, vert, bleu), ceci pour stocker les dimensions x, y et z du vecteur. Toutefois, d’autres encodages existent, comme ceux qui sont basés sur des coordonnées polaires.

 Hauteur cartes les mappages de hauteur contiennent des données de champ de hauteur. Elles sont utilisées pour fournir une forme de détail géométrique sur l’objet affecté (par l’application d’un code de nuanceur pour calculer l’effet escompté) ou des points de données associés à des cas d’utilisation tels que la génération de terrains. Les valeurs de hauteur sont généralement codées à l’aide d’un canal dans une texture.

 Les mappages de cubes des mappages de cube peuvent contenir différents types de données, par exemple des couleurs ou des normales, mais sont organisés en six textures sur les faces d’un cube. De ce fait, des mappages de cube ne sont pas échantillonnés en fournissant des coordonnées de texture, mais en fournissant un vecteur dont l’origine est le centre du cube ; l’échantillon est prélevé au point d’intersection entre le vecteur et le cube. Les mappages de cube sont utilisés pour fournir une approximation de l’environnement pouvant être utilisé pour calculer les réflexions, appelée *mappage de l’environnement*, ou fournir une texture aux objets sphériques avec moins de distorsion que les textures de base, à deux dimensions.

 Une texture peut être encodée et compressée de plusieurs manières orthogonales par rapport au type de données contenu dans une texture, à la dimensionnalité ou à la « forme » de la texture. Toutefois, différentes méthodes d’encodage et de compression offrent de meilleurs résultats pour différents types de données.

 Vous pouvez utiliser l’Éditeur d’images pour créer et modifier des textures et des images avec des méthodes qui ressemblent à d’autres éditeurs d’images. L’Éditeur d’images fournit également le Mappage MIP et d’autres fonctionnalités à utiliser avec des graphiques 3D, et prend en charge plusieurs formats de texture hautement compressés et à accélération matérielle que DirectX prend en charge.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Image Editor](../designers/image-editor.md)|Décrit comment utiliser l’Éditeur d’images pour utiliser les textures et les images.|
|[Exemples de l’éditeur d’images](../designers/image-editor-examples.md)|Fournit des liens vers des rubriques qui expliquent comment utiliser l’Éditeur d’images pour effectuer des tâches de traitement d’images courantes.|
