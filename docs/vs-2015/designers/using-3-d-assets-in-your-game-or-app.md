---
title: Utilisation de ressources 3D dans vos jeux et applications | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VC.Project.ImageContentTask.ContentOutput
- VC.Project.MeshContentTask.ContentOutput
- VC.Project.ImageContentTask.GeneratePremultipliedAlpha
- VC.Project.ImageContentTask.Compress
- VC.Project.ShaderGraphContentTask.ContentOutput
- VC.Project.ImageContentTask.GenerateMips
ms.assetid: ea587909-e434-46a8-abf8-9b3e95a58b4f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c475366c190e5ac008394f8642f64da022532a0a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064737"
---
# <a name="using-3-d-assets-in-your-game-or-app"></a>Utilisation de ressources 3D dans vos jeux et applications
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cet article explique comment vous pouvez utiliser [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour traiter les ressources 3D et les inclure dans vos builds.  
  
 Une fois que vous avez utilisé les outils de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour créer des ressources 3D, l'étape suivante consiste à les utiliser dans votre application. Mais avant de pouvoir les utiliser, vos ressources doivent être converties dans un format compatible avec DirectX. Pour vous aider à transformer vos ressources, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fournit des personnalisations de build pour chaque type de ressource qu'il peut générer. Pour inclure les ressources dans votre build, il vous suffit de configurer votre projet pour utiliser les personnalisations de build, ajouter les ressources à votre projet, puis configurer les ressources pour utiliser la personnalisation de build appropriée. Ensuite, vous pouvez charger les ressources dans votre application et les utiliser en créant et complétant des ressources DirectX comme dans n'importe quelle autre application DirectX.  
  
## <a name="configuring-your-project"></a>Configuration de votre projet  
 Avant de déployer vos ressources 3D dans le cadre de votre build, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] doit savoir quels types de ressources vous voulez déployer. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] connaît déjà de nombreux types de fichiers communs, mais comme seuls certains types d'applications utilisent des ressources 3D, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ne considère pas qu'un projet va générer ces types de fichiers. Vous pouvez informer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que votre application utilise ces types de ressources à l’aide des fichiers de *personnalisation de la build* fournis pour chaque type de ressource, qui indiquent à [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] comment traiter différents types de fichiers de manière utile. Comme ces personnalisations sont appliquées projet par projet, tout ce que vous avez à faire est d'ajouter les personnalisations appropriées à votre projet.  
  
#### <a name="to-add-the-build-customizations-to-your-project"></a>Pour ajouter les personnalisations de la build à votre projet  
  
1. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Dépendances de build**, **Personnalisations de la build**. La boîte de dialogue **Fichiers de personnalisation de la build Visual C++** s’affiche.  
  
2. Sous **Fichiers de personnalisation de la build disponibles**, cochez les cases qui correspondent aux types de ressources que vous voulez utiliser dans votre projet, comme décrit dans ce tableau :  
  
    |Type de ressource|Nom de personnalisation de la build|  
    |----------------|------------------------------|  
    |Textures et images|**ImageContentTask(.targets, .props)**|  
    |Modèles 3D|**MeshContentTask(.targets, .props)**|  
    |Nuanceurs|**ShaderGraphContentTask(.targets, .props)**|  
  
3. Sélectionnez le bouton **OK** .  
  
## <a name="including-assets-in-your-build"></a>Inclusion de ressources dans votre build  
 Maintenant que votre projet sait quels types de ressources 3D vous voulez utiliser, l'étape suivante consiste à lui indiquer les fichiers qui sont des ressources 3D et les types de ressources auxquels elles correspondent.  
  
#### <a name="to-add-an-asset-to-your-build"></a>Pour ajouter une ressource à votre build  
  
1. Dans **l’Explorateur de solutions**, dans votre projet, ouvrez le menu contextuel d’une ressource, puis choisissez **Propriétés**. La boîte de dialogue **Page de propriétés** de la ressource s’affiche.  
  
2. Vérifiez que les valeurs définies des propriétés **Configuration** et **Plateforme** sont celles auxquelles vous voulez que vos modifications s’appliquent.  
  
3. Sous **Propriétés de configuration**, choisissez **Général** puis, dans la grille des propriétés, sous **Général**, affectez à la propriété **Type d’élément** le type d’élément de pipeline de contenu approprié. Par exemple, pour un fichier image ou de texture, choisissez le **pipeline de contenu d’image**.  
  
   > [!IMPORTANT]
   >  Par défaut, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] suppose que de nombreux types de fichiers image doivent être classés à l’aide du type d’élément **Image** intégré à [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Ainsi, vous devez modifier la propriété **Type d’élément** de chaque image qui doit être traitée par le pipeline de contenu d’image. Les autres types de fichiers sources de pipeline de contenu pour les modèles 3D et les graphiques de nuanceurs visuels ont pour valeur par défaut le **Type d’élément** approprié.  
  
4. Sélectionnez le bouton **OK** .  
  
   Voici les trois types d'éléments de pipeline de contenu et leurs types de fichiers sources et de sortie associés.  
  
|Type d'élément|Types de fichiers sources|Format des fichiers de sortie|  
|---------------|-----------------------|------------------------|  
|**Pipeline de contenu d’image**|Portable Network Graphics (.png)<br /><br /> JPEG (.jpg, .jpeg, .jpe, .jfif)<br /><br /> Direct Draw Surface (.dds)<br /><br /> Graphics Interchange Format (.gif)<br /><br /> Bitmap (.bmp, .dib)<br /><br /> Tagged Image File Format (.tif, .tiff)<br /><br /> Targa (.tga)|DirectDraw Surface (.dds)|  
|**Pipeline de contenu de maillage**|Fichier d'échange AutoDesk FBX (.fbx)<br /><br /> Fichier DAE Collada (.dae)<br /><br /> Fichier Wavefront OBJ (.obj)|Fichier de maillage 3D (.cmo)|  
|**Pipeline de contenu de nuanceur**|Graphe de nuanceur visuel (.dgsl)|Sortie de nuanceur compilé (.cso)|  
  
## <a name="configuring-asset-content-pipeline-properties"></a>Configuration des propriétés du pipeline de contenu des ressources  
 Vous pouvez définir les propriétés du pipeline de contenu de chaque fichier de ressources afin qu'il soit généré de manière spécifique.  
  
#### <a name="to-configure-content-pipeline-properties"></a>Pour configurer les propriétés du pipeline de contenu  
  
1. Dans **l’Explorateur de solutions**, dans votre projet, ouvrez le menu contextuel du fichier de ressources, puis choisissez **Propriétés**. La boîte de dialogue **Page de propriétés** de la ressource s’affiche.  
  
2. Vérifiez que les valeurs définies des propriétés **Configuration** et **Plateforme** sont celles auxquelles vous voulez que vos modifications s’appliquent.  
  
3. Sous **Propriétés de configuration**, choisissez le nœud de pipeline de contenu (par exemple, **Pipeline de contenu d’image** pour les ressources de texture et d’image) puis, dans la grille des propriétés, affectez aux propriétés les valeurs appropriées. Par exemple, pour générer des mipmaps pour une ressource de texture au moment de la génération, affectez à la propriété **Générer des mips** la valeur **Oui**.  
  
4. Sélectionnez le bouton **OK** .  
  
### <a name="image-content-pipeline-configuration"></a>Configuration du pipeline de contenu d'image  
 Quand vous utilisez l'outil de pipeline de contenu d'image pour générer une ressource de texture, vous pouvez compresser la texture de différentes manières, indiquer si les niveaux MIP doivent être générés au moment de la génération, puis modifier le nom du fichier de sortie.  
  
|Propriété|Description|  
|--------------|-----------------|  
|**Compresser**|Spécifie le type de compression utilisé pour le fichier de sortie.<br /><br /> Les options disponibles sont les suivantes :<br /><br /> -   **Aucune compression**<br />-   **Compression BC1_UNORM**<br />-   **Compression BC1_UNORM_SRGB**<br />-   **Compression BC2_UNORM**<br />-   **Compression BC2_UNORM_SRGB**<br />-   **Compression BC3_UNORM**<br />-   **Compression BC3_UNORM_SRGB**<br />-   **Compression BC4_UNORM**<br />-   **Compression BC4_SNORM**<br />-   **Compression BC5_UNORM**<br />-   **Compression BC5_SNORM**<br />-   **Compression BC6H_UF16**<br />-   **Compression BC6H_SF16**<br />-   **Compression BC7_UNORM**<br />-   **Compression BC7_UNORM_SRGB**<br /><br /> Pour plus d’informations sur les formats de compression pris en charge dans les différentes versions de DirectX, consultez [Guide de programmation pour DXGI](http://go.microsoft.com/fwlink/p/?LinkId=246265).|  
|Convertir dans un format alpha prémultiplié|**Oui** pour convertir l’image dans un format alpha prémultiplié dans le fichier de sortie ; sinon, **Non**. Seul le fichier de sortie est modifié ; l'image source est inchangée.|  
|**Générer des mips**|**Oui** pour générer une chaîne MIP complète au moment de la génération et l’inclure dans le fichier de sortie ; sinon, **Non**. Si la valeur **Non** est sélectionnée et que le fichier source contient déjà une chaîne mipmap, le fichier de sortie a une chaîne MIP ; sinon, le fichier de sortie n’a pas de chaîne MIP.|  
|**Sortie de contenu**|Spécifie le nom du fichier de sortie. **Important :**  La modification de l'extension de nom de fichier du fichier de sortie n'a aucun effet sur son format.|  
  
### <a name="mesh-content-pipeline-configuration"></a>Configuration du pipeline de contenu de maillage  
 Quand vous utilisez l'outil de pipeline de contenu de maillage pour générer une ressource de maillage, vous pouvez modifier le nom du fichier de sortie.  
  
|Propriété|Description|  
|--------------|-----------------|  
|**Sortie de contenu**|Spécifie le nom du fichier de sortie. **Important :**  La modification de l'extension de nom de fichier du fichier de sortie n'a aucun effet sur son format.|  
  
### <a name="shader-content-pipeline-configuration"></a>Configuration du pipeline de contenu de nuanceur  
 Quand vous utilisez l'outil de pipeline de contenu de nuanceur pour générer une ressource de nuanceur, vous pouvez modifier le nom du fichier de sortie.  
  
|Propriété|Description|  
|--------------|-----------------|  
|**Sortie de contenu**|Spécifie le nom du fichier de sortie. **Important :**  La modification de l'extension de nom de fichier du fichier de sortie n'a aucun effet sur son format.|  
  
## <a name="loading-and-using-3-d-assets-at-run-time"></a>Chargement et utilisation de ressources 3D au moment de l'exécution  
  
### <a name="using-textures-and-images"></a>Utilisation de textures et d'images  
 Direct3D propose des fonctions de création de ressources de texture. Dans Direct3D 11, la bibliothèque d'utilitaires D3DX11 fournit des fonctions supplémentaires pour créer des ressources de texture et des affichages de ressources directement à partir de fichiers image. Pour plus d’informations sur la création d’une ressource de texture dans Direct3D 11, consultez [Textures](http://go.microsoft.com/fwlink/p/?LinkID=246267). Pour plus d’informations sur la façon d’utiliser la bibliothèque D3DX11 pour créer une ressource de texture ou un affichage des ressources à partir d’un fichier image, consultez [Guide pratique pour Initialiser une Texture à partir d’un fichier](http://go.microsoft.com/fwlink/p/?LinkId=246268).  
  
### <a name="using-3-d-models"></a>Utilisation de modèles 3D  
 Direct3D 11 ne propose pas de fonctions permettant de créer des ressources à partir de modèles 3D. À la place, vous devez écrire du code qui lise le fichier de modèle 3D et crée des mémoires tampons de vertex et d'index qui représentent le modèle 3D et toutes les ressources nécessaires au modèle (par exemple, des textures ou des nuanceurs).  
  
### <a name="using-shaders"></a>Utilisation de nuanceurs  
 Direct3D propose des fonctions permettant de créer des ressources de nuanceur et de les lier au pipeline graphique programmable. Pour plus d’informations sur la façon de créer une ressource de nuanceur dans Direct3D et de la lier au pipeline, consultez [Guide de programmation pour HLSL](http://go.microsoft.com/fwlink/p/?LinkID=261521).  
  
 Dans le pipeline graphique programmable, chaque étape du pipeline doit fournir à l'étape suivante du pipeline un résultat mis en forme de manière intelligible. Sachant que le concepteur Shader ne peut créer que des nuanceurs de pixels, il appartient à votre application de vérifier que les données qu'elle reçoit sont au format attendu. Plusieurs étapes de nuanceur programmables se produisent avant le nuanceur de pixels et effectuent des transformations géométriques (le nuanceur de sommets, le nuanceur Hull Shader, le nuanceur de domaine et le nuanceur de géométrie). L'étape de pavage non programmable se produit également avant le nuanceur de pixels. Quelle que soit l'étape qui précède directement le nuanceur de pixels, son résultat doit se présenter au format suivant :  
  
```hlsl  
  
struct PixelShaderInput  
{  
    float4 pos : SV_POSITION;  
    float4 diffuse : COLOR;  
    float2 uv : TEXCOORD0;  
    float3 worldNorm : TEXCOORD1;  
    float3 worldPos : TEXCOORD2;  
    float3 toEye : TEXCOORD3;  
    float4 tangent : TEXCOORD4;  
    float3 normal : TEXCOORD5;  
};  
```  
  
 Selon les nœuds du concepteur Shader que vous utilisez dans votre nuanceur, vous devrez peut-être aussi fournir des informations supplémentaires formatées en fonction de ces définitions :  
  
```  
  
Texture2D Texture1 : register( t0 );  
Texture2D Texture2 : register( t1 );  
Texture2D Texture3 : register( t2 );  
Texture2D Texture4 : register( t3 );  
Texture2D Texture5 : register( t4 );  
Texture2D Texture6 : register( t5 );  
Texture2D Texture7 : register( t6 );  
Texture2D Texture8 : register( t7 );  
  
TextureCube CubeTexture1 : register( t8 );  
TextureCube CubeTexture2 : register( t9 );  
TextureCube CubeTexture3 : register( t10 );  
TextureCube CubeTexture4 : register( t11 );  
TextureCube CubeTexture5 : register( t12 );  
TextureCube CubeTexture6 : register( t13 );  
TextureCube CubeTexture7 : register( t14 );  
TextureCube CubeTexture8 : register( t15 );  
  
SamplerState TexSampler : register( s0 );  
  
cbuffer MaterialVars : register (b0)  
{  
    float4 MaterialAmbient;  
    float4 MaterialDiffuse;  
    float4 MaterialSpecular;  
    float4 MaterialEmissive;  
    float MaterialSpecularPower;  
};  
  
cbuffer LightVars : register (b1)  
{  
    float4 AmbientLight;  
    float4 LightColor[4];  
    float4 LightAttenuation[4];  
    float3 LightDirection[4];  
    float LightSpecularIntensity[4];  
    uint IsPointLight[4];  
    uint ActiveLights;  
}  
  
cbuffer ObjectVars : register(b2)  
{  
    float4x4 LocalToWorld4x4;  
    float4x4 LocalToProjected4x4;  
    float4x4 WorldToLocal4x4;  
    float4x4 WorldToView4x4;  
    float4x4 UVTransform4x4;  
    float3 EyePosition;  
};  
  
cbuffer MiscVars : register(b3)  
{  
    float ViewportWidth;  
    float ViewportHeight;  
    float Time;  
};  
```  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Guide pratique pour Exporter une Texture qui contient des Mipmaps](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|Explique comment utiliser le pipeline de contenu d'image pour exporter une texture qui contient des mipmaps précalculés.|  
|[Guide pratique pour Exporter une Texture qui a des valeurs Alpha prémultipliées](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|Explique comment utiliser le pipeline de contenu d'image pour exporter une texture qui contient des valeurs alpha prémultipliées.|  
|[Guide pratique pour Exporter une Texture à utiliser avec Direct2D applications JavaScript ou Direct2d](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|Explique comment utiliser le pipeline de contenu d'image pour exporter une texture utilisable dans une application Direct2D ou Javascript.|  
|[Utilisation de ressources 3D pour les jeux et les applications](../designers/working-with-3-d-assets-for-games-and-apps.md)|Décrit les outils d'édition fournis par Visual Studio en vue de créer et manipuler des ressources 3D, à savoir, textures, images, modèles 3D et nuanceurs.|  
|[Guide pratique pour exporter un nuanceur](../designers/how-to-export-a-shader.md)|Explique comment exporter un nuanceur à partir du concepteur Shader.|
