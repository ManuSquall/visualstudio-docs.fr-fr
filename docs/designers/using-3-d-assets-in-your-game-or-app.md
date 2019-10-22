---
title: Utilisation de composants 3D dans votre jeu ou votre application
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VC.Project.ImageContentTask.ContentOutput
- VC.Project.MeshContentTask.ContentOutput
- VC.Project.ImageContentTask.GeneratePremultipliedAlpha
- VC.Project.ImageContentTask.Compress
- VC.Project.ShaderGraphContentTask.ContentOutput
- VC.Project.ImageContentTask.GenerateMips
ms.assetid: ea587909-e434-46a8-abf8-9b3e95a58b4f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 400e69ddaf9ebd3596edf3b926484b623225d672
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72634535"
---
# <a name="how-to-use-3d-assets-in-your-game-or-app"></a>Comment : utiliser des composants 3D dans votre jeu ou votre application

Cet article explique comment vous pouvez utiliser Visual Studio pour traiter des composants 3D et les inclure dans vos builds.

Une fois que vous avez utilisé les outils de Visual Studio pour créer des composants 3D, l’étape suivante consiste à les utiliser dans votre application. Mais avant de pouvoir les utiliser, vous devez convertir vos ressources dans un format compatible avec DirectX. Pour vous aider à transformer vos composants, Visual Studio fournit des personnalisations de build pour chaque type de composant qu’il peut produire. Pour inclure les ressources dans votre build, il vous suffit de configurer votre projet pour utiliser les personnalisations de build, ajouter les ressources à votre projet, puis configurer les ressources pour utiliser la personnalisation de build appropriée. Ensuite, vous pouvez charger les ressources dans votre application et les utiliser en créant et complétant des ressources DirectX comme dans n'importe quelle autre application DirectX.

## <a name="configure-your-project"></a>Configurer votre projet

Avant de déployer vos composants 3D dans le cadre de votre build, Visual Studio doit savoir quels types de composants vous voulez déployer. Visual Studio connaît déjà de nombreux types de fichiers courants, mais comme seuls certains types d’applications utilisent des composants 3D, il ne fait pas l’hypothèse qu’un projet va générer ces types de fichiers. Vous pouvez indiquer à Visual Studio que votre application utilise ces types de composants avec des *personnalisations de build*, qui sont des fichiers fournis pour chaque type de composant, indiquant à Visual Studio comment traiter pratiquement les différents types de fichiers. Comme ces personnalisations sont appliquées projet par projet, tout ce que vous avez à faire est d'ajouter les personnalisations appropriées à votre projet.

### <a name="to-add-the-build-customizations-to-your-project"></a>Pour ajouter les personnalisations de la build à votre projet

1. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Dépendances de build** > **Personnalisations de la build**.

   La boîte de dialogue **Fichiers de personnalisation de la build Visual C++** apparaît.

2. Sous **Fichiers de personnalisation de la build disponibles**, cochez les cases qui correspondent aux types de ressources que vous voulez utiliser dans votre projet, comme décrit dans le tableau suivant :

    |Type de ressource|Nom de personnalisation de la build|
    |----------------| - |
    |Textures et images|**ImageContentTask(.targets, .props)**|
    |Modèles 3D|**MeshContentTask(.targets, .props)**|
    |Nuanceurs|**ShaderGraphContentTask(.targets, .props)**|

3. Sélectionnez le bouton **OK** .

## <a name="include-assets-in-your-build"></a>Inclure des composants dans votre build

Maintenant que votre projet sait quels types de ressources 3D vous voulez utiliser, l’étape suivante consiste à lui indiquer les fichiers qui sont des ressources 3D et à quels types de ressources ils correspondent.

### <a name="to-add-an-asset-to-your-build"></a>Pour ajouter une ressource à votre build

1. Dans **l’Explorateur de solutions**, dans votre projet, ouvrez le menu contextuel d’une ressource, puis choisissez **Propriétés**.

   La boîte de dialogue **Page de propriétés** de la ressource apparaît.

2. Vérifiez que les valeurs définies des propriétés **Configuration** et **Plateforme** sont celles auxquelles vous voulez que vos modifications s’appliquent.

3. Sous **Propriétés de configuration**, choisissez **Général** puis, dans la grille des propriétés, sous **Général**, affectez à la propriété **Type d’élément** le type d’élément de pipeline de contenu approprié. Par exemple, pour un fichier image ou de texture, choisissez le **pipeline de contenu d’image**.

    > [!IMPORTANT]
    > Par défaut, Visual Studio considère que de nombreux types de fichiers image doivent être classés dans la catégorie des types d’éléments **Image**, qui est intégrée à Visual Studio. Ainsi, vous devez modifier la propriété **Type d’élément** de chaque image qui doit être traitée par le pipeline de contenu d’image. Les autres types de fichiers sources du pipeline de contenu pour les modèles 3D et les graphismes des nuanceurs visuels ont pour valeur par défaut le **Type d’élément** approprié.

4. Sélectionnez le bouton **OK** .

Voici les trois types d’éléments de pipeline de contenu et leurs types de fichiers sources et de sortie associés.

|Type d'élément|Types de fichiers sources|Format des fichiers de sortie|
|---------------| - | - |
|**Pipeline de contenu d’image**|Portable Network Graphics ( *.png*)<br /><br /> JPEG ( *.jpg*, *.jpeg*, *.jpe*, *.jfif*)<br /><br /> Direct Draw Surface ( *.dds*)<br /><br /> Graphics Interchange Format ( *.gif*)<br /><br /> Bitmap ( *.bmp*, *.dib*)<br /><br /> Tagged Image File Format ( *.tif*, *.tiff*)<br /><br /> Targa ( *.tga*)|DirectDraw Surface ( *.dds*)|
|**Pipeline de contenu de maillage**|Fichier d’échange AutoDesk FBX ( *.fbx*)<br /><br /> Fichier DAE Collada ( *.dae*)<br /><br /> Fichier Wavefront OBJ ( *.obj*)|Fichier de maillage 3D ( *.cmo*)|
|**Pipeline de contenu de nuanceur**|Graphe de nuanceur visuel ( *.dgsl*)|Sortie de nuanceur compilé ( *.cso*)|

## <a name="configure-asset-content-pipeline-properties"></a>Configurer les propriétés du pipeline de contenu des composants

Vous pouvez définir les propriétés du pipeline de contenu de chaque fichier de ressources afin qu'il soit généré de manière spécifique.

### <a name="to-configure-content-pipeline-properties"></a>Pour configurer les propriétés du pipeline de contenu

1. Dans **l’Explorateur de solutions**, dans votre projet, ouvrez le menu contextuel du fichier de ressources, puis choisissez **Propriétés**.

   La boîte de dialogue **Page de propriétés** de la ressource apparaît.

2. Vérifiez que les valeurs définies des propriétés **Configuration** et **Plateforme** sont celles auxquelles vous voulez que vos modifications s’appliquent.

3. Sous **Propriétés de configuration**, choisissez le nœud de pipeline de contenu (par exemple **Pipeline de contenu d’image** pour des ressources de texture et d’image) puis, dans la grille des propriétés, affectez aux propriétés les valeurs appropriées. Par exemple, pour générer des mipmaps pour une ressource de texture au moment de la génération, affectez à la propriété **Générer des mips** la valeur **Oui**.

4. Sélectionnez le bouton **OK** .

### <a name="image-content-pipeline-configuration"></a>Configuration du pipeline de contenu d'image

Quand vous utilisez l'outil de pipeline de contenu d'image pour générer une ressource de texture, vous pouvez compresser la texture de différentes manières, indiquer si les niveaux MIP doivent être générés au moment de la génération, puis modifier le nom du fichier de sortie.

|Property|Description|
|--------------|-----------------|
|**Compresser**|Spécifie le type de compression utilisé pour le fichier de sortie.<br /><br /> Les options disponibles sont les suivantes :<br /><br /> -   **Aucune compression**<br />-   **Compression BC1_UNORM**<br />-   **Compression BC1_UNORM_SRGB**<br />-   **Compression BC2_UNORM**<br />-   **Compression BC2_UNORM_SRGB**<br />-   **Compression BC3_UNORM**<br />-   **Compression BC3_UNORM_SRGB**<br />-   **Compression BC4_UNORM**<br />-   **Compression BC4_SNORM**<br />-   **Compression BC5_UNORM**<br />-   **Compression BC5_SNORM**<br />-   **Compression BC6H_UF16**<br />-   **Compression BC6H_SF16**<br />-   **Compression BC7_UNORM**<br />-   **Compression BC7_UNORM_SRGB**<br /><br /> Pour plus d’informations sur les formats de compression pris en charge dans les différentes versions de DirectX, consultez [Guide de programmation pour DXGI](http://go.microsoft.com/fwlink/p/?LinkId=246265).|
|Convertir dans un format alpha prémultiplié|**Oui** pour convertir l’image dans un format alpha prémultiplié dans le fichier de sortie ; sinon, **Non**. Seul le fichier de sortie est modifié ; l'image source est inchangée.|
|**Générer des mips**|**Oui** pour générer une chaîne MIP complète au moment de la génération et l’inclure dans le fichier de sortie ; sinon, **Non**. Si la valeur **Non** est sélectionnée et que le fichier source contient déjà une chaîne mipmap, le fichier de sortie a une chaîne MIP ; sinon, le fichier de sortie n’a pas de chaîne MIP.|
|**Sortie de contenu**|Spécifie le nom du fichier de sortie. **Important :** La modification de l’extension du nom de fichier de sortie n’a aucun effet sur son format.|

### <a name="mesh-content-pipeline-configuration"></a>Configuration du pipeline de contenu de maillage

Quand vous utilisez l'outil de pipeline de contenu de maillage pour générer une ressource de maillage, vous pouvez modifier le nom du fichier de sortie.

|Property|Description|
|--------------|-----------------|
|**Sortie de contenu**|Spécifie le nom du fichier de sortie. **Important :** La modification de l’extension du nom de fichier de sortie n’a aucun effet sur son format.|

### <a name="shader-content-pipeline-configuration"></a>Configuration du pipeline de contenu de nuanceur

Quand vous utilisez l'outil de pipeline de contenu de nuanceur pour générer une ressource de nuanceur, vous pouvez modifier le nom du fichier de sortie.

|Property|Description|
|--------------|-----------------|
|**Sortie de contenu**|Spécifie le nom du fichier de sortie. **Important :** La modification de l’extension du nom de fichier de sortie n’a aucun effet sur son format.|

## <a name="load-and-use-3d-assets-at-run-time"></a>Charger et utiliser des composants 3D lors de l’exécution

### <a name="use-textures-and-images"></a>Utiliser des textures et des images

Direct3D propose des fonctions de création de ressources de texture. Dans Direct3D 11, la bibliothèque d'utilitaires D3DX11 fournit des fonctions supplémentaires pour créer des ressources de texture et des affichages de ressources directement à partir de fichiers image. Pour plus d’informations sur la création d’une ressource de texture dans Direct3D 11, consultez [Textures](http://go.microsoft.com/fwlink/p/?LinkID=246267). Pour plus d’informations sur la façon d’utiliser la bibliothèque D3DX11 pour créer une ressource de texture ou un affichage des ressources à partir d’un fichier image, consultez [Guide pratique pour initialiser une texture à partir d’un fichier](http://go.microsoft.com/fwlink/p/?LinkId=246268).

### <a name="use-3d-models"></a>Utiliser des modèles 3D

Direct3D 11 ne fournit pas de fonctions permettant de créer des ressources à partir de modèles 3D. Au lieu de cela, vous devez écrire du code qui lise le fichier de modèle 3D et crée des sommets et des mémoires tampons d’index, qui représentent le modèle 3D et toutes les ressources nécessaires au modèle (par exemple, des textures ou des nuanceurs).

### <a name="use-shaders"></a>Utiliser des nuanceurs

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

```hlsl
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
|[Guide pratique pour exporter une texture qui contient des mipmaps](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|Explique comment utiliser le pipeline de contenu d'image pour exporter une texture qui contient des mipmaps précalculés.|
|[Guide pratique pour exporter une texture qui contient des valeurs alpha prémultipliées](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|Explique comment utiliser le pipeline de contenu d'image pour exporter une texture qui contient des valeurs alpha prémultipliées.|
|[Comment : exporter une texture pour l’utiliser avec des applications Direct2D ou JavaScript](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|Explique comment utiliser le pipeline de contenu d'image pour exporter une texture utilisable dans une application Direct2D ou Javascript.|
|[Utilisation de composants 3D pour les jeux et les applications](../designers/working-with-3-d-assets-for-games-and-apps.md)|Décrit les outils d’édition fournis par Visual Studio pour créer et manipuler des composants 3D, qui comprennent les textures, les images, les modèles 3D et les nuanceurs.|
|[Guide pratique pour exporter un nuanceur](../designers/how-to-export-a-shader.md)|Explique comment exporter un nuanceur à partir du concepteur Shader.|