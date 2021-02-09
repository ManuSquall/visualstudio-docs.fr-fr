---
title: Utilisation de composants 3D pour les jeux et les applications
description: Découvrez les outils Visual Studio que vous pouvez utiliser pour créer ou modifier des modèles 3D, des textures et des nuanceurs pour les jeux et les applications DirectX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8b622200832e42aa3900061125fe08271f5f3458
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896349"
---
# <a name="work-with-3d-assets-for-games-and-apps"></a>Utiliser des composants 3D pour les jeux et les applications

Cet article décrit les outils Visual Studio que vous pouvez utiliser pour créer ou modifier des modèles 3D, des textures et des nuanceurs pour les jeux et les applications DirectX.

## <a name="directx-app-development-in-visual-studio"></a>Développement d’applications DirectX dans Visual Studio

Une application DirectX combine généralement la logique de programmation, l’API DirectX et les programmes HLSL (High Level Shading Language) avec les ressources visuelle3D et audio pour fournir une expérience multimédia riche et interactive. Visual Studio inclut des outils que vous pouvez utiliser avec des images et des textures, des modèles 3D et des nuanceurs sans qu’il soit nécessaire de quitter l’IDE pour utiliser un autre outil. Les outils Visual Studio sont particulièrement adaptés pour créer les ressources *d’espace réservé*, que vous pouvez utiliser pour tester du code ou générer des prototypes avant de mettre en service les ressources prêtes pour la production, ainsi que pour examiner et modifier les ressources prêtes pour la production quand vous déboguez votre application.

Voici plus d’informations sur les types de ressources que vous pouvez utiliser dans Visual Studio.

### <a name="images-and-textures"></a>Images et textures

Les images et les textures fournissent des détails visuels et de couleur dans les jeux et les applications. Dans les graphiques 3D, les textures se présentent selon différents formats, types et géométries, qui permettent de prendre en charge différentes utilisations. Par exemple, les cartes de normales fournissent les normales de surface par pixel pour un éclairage plus détaillé des modèles 3D, et les cartes de cube fournissent la texture dans toutes les directions pour des utilisations telles que le sky-boxing, les réflexions et le mappage de texture sphérique. Les textures peuvent fournir des mipmaps pour prendre en charge un rendu efficace à différents niveaux de détail, et peuvent prendre en charge des canaux de couleur et des ordres de couleurs différents. Les textures peuvent être stockées dans divers formats compressés qui occupent moins de mémoire graphique dédiée et aident les GPU à accéder aux textures plus efficacement.

Vous pouvez utiliser l’éditeur d’images Visual Studio pour travailler avec des images et des textures dans de nombreux types et formats courants.

### <a name="3d-models"></a>Modèles 3D

Les modèles 3D créent des espaces et des formes dans les jeux et les applications. Au minimum, les modèles encodent la position des points dans l’espace 3D, appelés *sommets*, en même temps que les données d’indexation pour définir des lignes ou des triangles qui représentent la forme du modèle. Des données supplémentaires peuvent être associées à ces sommets, par exemple les informations de couleur, les vecteurs normaux ou les attributs spécifiques à l’application. Chaque modèle peut également définir des attributs spécifiques à l’objet, comme le nuanceur utilisé pour calculer l’apparence de la surface de l’objet ou la texture appliquée à celui-ci.

Vous pouvez utiliser l’éditeur de modèle Visual Studio pour travailler avec des modèles 3D dans plusieurs formats courants.

### <a name="shaders"></a>Nuanceurs

Les nuanceurs sont de petits programmes spécifiques au domaine qui s’exécutent sur l’unité de traitement graphique (GPU). Ils déterminent la façon dont les modèles 3D sont transformés en formes à l’écran et comment chaque pixel de ces formes est coloré. En créant un nuanceur et en l’appliquant à un objet dans votre jeu ou application, vous pouvez donner à l’objet une apparence unique.

Vous pouvez utiliser le concepteur Shader Visual Studio, qui est un outil de conception de nuanceur graphique, pour créer des effets visuels personnalisés sans connaître la programmation HLSL.

> [!NOTE]
> Pour plus d’informations sur la façon de démarrer avec la programmation DirectX, consultez [DirectX](/windows/win32/directx). Pour plus d’informations sur le débogage d’une application DirectX, consultez [Graphics Diagnostics (débogage DirectX Graphics) (](../debugger/graphics/visual-studio-graphics-diagnostics.md)en anglais).

## <a name="directx-version-compatibility"></a>Compatibilité des versions DirectX

Visual Studio utilise DirectX pour restituer les composants 2D et 3D. Vous pouvez sélectionner le renderer DirectX 11 ou le renderer logiciel de la plateforme WARP (Windows Advanced Rasterization Platform). Le renderer DirectX 11 fournit un rendu à accélération matérielle, hautes performances sur les GPU DirectX 11 et DirectX 10. Le renderer WARP aide à garantir que vos ressources s’exécutent avec une large gamme d’ordinateurs, dont les ordinateurs qui ne disposent pas de matériel graphique moderne et ceux qui disposent de matériel graphique intégré. Pour plus d’informations sur WARP, consultez le Guide de la [plateforme Windows Advanced rastérisation (Warp)](/windows/win32/direct3darticles/directx-warp).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Utilisation des textures et des images](../designers/working-with-textures-and-images.md)|Décrit comment utiliser Visual Studio pour travailler avec des images et des textures.|
|[Utilisation des modèles 3D](../designers/working-with-3-d-models.md)|Décrit comment utiliser Visual Studio pour travailler avec des modèles 3D.|
|[Utilisation des nuanceurs](../designers/working-with-shaders.md)|Décrit comment utiliser le concepteur Shader Visual Studio pour créer et modifier des effets de nuanceur personnalisés.|
|[Utilisation de composants 3D dans votre jeu ou votre application](../designers/using-3-d-assets-in-your-game-or-app.md)|Décrit comment utiliser les ressources que vous avez créées à l’aide de l’éditeur d’images, l’éditeur de modèle ou le concepteur Shader dans votre jeu ou application.|
