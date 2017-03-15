---
title: "Utilisation de ressources 3D pour les jeux et les applications | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.graphics"
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
caps.latest.revision: 24
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 24
---
# Utilisation de ressources 3D pour les jeux et les applications
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ce document décrit les outils [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que vous pouvez utiliser pour créer ou modifier les modèles 3D, les textures et les nuanceurs pour les jeux et les applications basés sur DirectX.  
  
## Développement d'applications DirectX dans Visual Studio  
 Une application DirectX combine généralement la logique de programmation, l'API DirectX, les programmes HLSL \(High Level Shading Language\), ainsi que les ressources visuels 3D et audio pour fournir une expérience multimédia riche et interactive.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inclut des outils que vous pouvez utiliser avec des images et des textures, des modèles 3D et des nuanceurs sans laisser l'IDE utiliser un autre outil.  Les outils Visual Studio sont particulièrement adaptés pour créer les ressources *d'espace réservé*, que vous pouvez utiliser pour tester du code ou générer des prototypes avant de mettre en service les ressources prêtes pour la production, ainsi que pour examiner et modifier les ressources prêtes pour la production lorsque vous déboguez votre application.  
  
 Voici plus d'informations sur les types de ressources que vous pouvez utiliser dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### Images et textures  
 Les images et les textures fournissent des détails visuels et de couleur dans les jeux et les applications.  Dans les graphiques 3D, les textures se présentent sous divers formats, types et géométries pour prendre en charge différentes utilisations.  Par exemple, les cartes normales fournissent les normales de surface par pixel pour l'éclairage plus détaillé des modèles 3D, et les cartes de cube fournissent la texture dans toutes les directions à des fins d'utilisation en tant que sky\-boxing, réflexions et mappage de texture sphérique.  Les textures peuvent fournir des cartes MIP pour prendre en charge un rendu efficace à différents niveaux de détail, et peuvent prendre en charge des canaux de couleur et des ordres de couleurs différents.  Les textures peuvent être stockées dans divers formats compressés qui occupent moins de mémoire graphique dédiée et aident les GPU à accéder aux textures plus efficacement.  
  
 Vous pouvez utiliser l'Éditeur d'images [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour utiliser des images et des textures dans de nombreux types et formats courants.  
  
### Modèles 3D  
 Les modèles 3D créent l'espace et la forme dans les jeux et les applications.  Au minimum, les modèles encodent la position des points dans l'espace 3D, appelés *vertex* en même temps que les données sont indexées pour définir des lignes ou des triangles qui représentent la forme du modèle.  Des données supplémentaires peuvent être associées à ces sommets, par exemple, les informations de couleur, les vecteurs normaux ou les attributs spécifiques à l'application.  Chaque modèle peut également définir des attributs spécifiques à l'objet, comme le nuanceur utilisé pour calculer l'apparence de la surface de l'objet, ou la texture appliquée à celui\-ci.  
  
 Vous pouvez utiliser l'éditeur de modèle [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour utiliser les modèles 3D dans plusieurs formats courants.  
  
### Shaders  
 Les Shaders sont de petits programmes spécifiques au domaine qui s'exécutent sur l'unité de traitement graphique \(GPU\),  Les Shaders déterminent la façon dont les modèles 3D sont transformés en formes à l'écran et comment chaque pixel de ces formes est coloré.  En créant un shader et en l'appliquant à un objet dans votre jeu ou application, vous pouvez donner à l'objet une apparence unique.  
  
 Vous pouvez utiliser le concepteur Shader [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , qui est un outil de conception Shader graphique, pour créer des effets visuels personnalisés sans connaître la programmation HLSL.  
  
> [!NOTE]
>  Pour plus d'informations sur comment démarrer avec la programmation DIrectX, consultez [DirectX](http://go.microsoft.com/fwlink/p/?LinkId=224633).  Pour plus d'informations sur le débogage d'une application DirectX, consultez [Graphics Diagnostics \(débogage DirectX Graphics\)](../debugger/visual-studio-graphics-diagnostics.md).  
  
## Compatibilité des versions DirectX  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilise DirectX pour afficher des ressources 2D et 3D.  Vous pouvez sélectionner le convertisseur DirectX 11, ou le convertisseur logiciel de la plateforme WARP \(Windows Advanced Rasterization Platform\).  Le convertisseur DirectX 11 fournit un rendu à accélération matérielle, hautes performances sur les GPU DirectX 11 et DirectX 10.  Le convertisseur WARP aide à garantir que vos ressources s'exécutent avec une large gamme d'ordinateurs, y compris les ordinateurs qui ne disposent pas de matériel graphique moderne et ceux qui disposent de matériel graphique intégré.  Pour plus d'informations sur le WRAP consultez [Windows Advanced Rasterization Platform \(WARP\) Guide](http://go.microsoft.com/fwlink/p/?LinkId=224634).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Utilisation des textures et des images](../designers/working-with-textures-and-images.md)|Décrit comment utiliser [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour traiter des images et des textures.|  
|[Utilisation des modèles 3D](../designers/working-with-3-d-models.md)|Décrit comment utiliser [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour utiliser les modèles 3D.|  
|[Utilisation des nuanceurs](../designers/working-with-shaders.md)|Décrit comment utiliser le concepteur Shader [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour créer et modifier des effets de nuanceur personnalisés.|  
|[Utilisation de ressources 3D dans vos jeux et applications](../designers/using-3-d-assets-in-your-game-or-app.md)|Décrit comment utiliser les ressources que vous avez créées à l'aide de l'Éditeur d'images, de l'Éditeur de modèle ou du concepteur Shader, dans votre jeu ou application.|