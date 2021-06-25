---
title: Manifest from Resources | Microsoft Docs
description: Découvrez comment utiliser l’outil Manifest from Resources pour ajouter des fichiers .png ou. Xaml à un fichier. imagemanifest pour une utilisation avec le service d’images Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f69a46362b3076025a63625adb1ee4a478622259
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903176"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
L’outil Manifest from Resources est une application console qui prend une liste de ressources d’image (fichiers .png ou. Xaml) et génère un fichier. imagemanifest qui permet d’utiliser ces images avec le service d’images Visual Studio. En outre, cet outil peut être utilisé pour ajouter des images à un. imagemanifest existant. Cet outil est utile pour ajouter la prise en charge de la haute résolution et de l’utilisation des images à une extension Visual Studio. Le fichier. imagemanifest généré doit être inclus dans et déployé dans le cadre d’une extension Visual Studio (. VSIX).

## <a name="how-to-use-the-tool"></a>Comment utiliser l’outil
 **Syntaxe**

 ManifestFromResources/Resources : \<Dir1> ; \<Img1> /assembly : \<AssemblyName>\<Optional Args>

 **Arguments**

|**Nom du commutateur**|**Remarques**|**Obligatoire ou facultatif**|
|-|-|-|
|/resources|Liste délimitée par des points-virgules d’images ou de répertoires. Cette liste doit toujours contenir la liste complète des images qui seront dans le manifeste. Si seule une liste partielle est indiquée, les entrées non incluses seront perdues.<br /><br /> Si un fichier de ressources donné est une bande d’image, l’outil le fractionne en images séparées avant d’ajouter chaque sous-image au manifeste.<br /><br /> Si l’image est un fichier .png, nous vous recommandons de mettre en forme le nom comme ceci afin que l’outil puisse remplir les attributs appropriés pour l’image : \<Name> . \<Width> . \<Height>.png.|Obligatoire|
|/assembly|Nom de l’assembly managé (sans l’extension), ou chemin d’accès au moment de l’exécution de l’assembly natif qui héberge les ressources (relatif à l’emplacement d’exécution du manifeste).|Obligatoire|
|/manifest|Nom à attribuer au fichier. imagemanifest généré. Cela peut également inclure un chemin d’accès absolu ou relatif pour créer le fichier dans un emplacement différent. Le nom par défaut correspond au nom de l’assembly.<br /><br /> Valeur par défaut : \<Current Directory> \\<assembly \> . imagemanifest|Facultatif|
|/guidName|Nom à attribuer au symbole GUID pour toutes les images dans le manifeste généré.<br /><br /> Valeur par défaut : AssetsGuid|Facultatif|
|/rootPath|Chemin d’accès racine qui doit être supprimé avant de créer des URI de ressource managée. (Cet indicateur est destiné à vous aider dans les cas où l’outil obtient le chemin d’accès de l’URI relatif incorrect, provoquant l’échec du chargement des ressources.)<br /><br /> Valeur par défaut : \<Current Directory>|Facultatif|
|/recursive|La définition de cet indicateur indique à l’outil de rechercher de manière récursive tous les répertoires dans l’argument/Resources. Si cet indicateur n’est pas spécifié, la recherche des répertoires est uniquement de niveau supérieur.|Facultatif|
|/isNative|Définissez cet indicateur lorsque l’argument assembly est un chemin d’accès pour un assembly natif. Omettez cet indicateur lorsque l’argument assembly est le nom d’un assembly managé. (Pour plus d’informations sur cet indicateur, consultez la section Remarques.)|Facultatif|
|/newGuids|La définition de cet indicateur indique à l’outil de créer une nouvelle valeur pour le symbole GUID des images au lieu de fusionner celui du manifeste existant.|Facultatif|
|/newIds|La définition de cet indicateur indique à l’outil de créer de nouvelles valeurs de symboles d’ID pour chaque image au lieu de fusionner les valeurs du manifeste existant.|Facultatif|
|/noLogo|La définition de cet indicateur arrête l’impression du produit et des informations de copyright.|Facultatif|
|/?|Imprimer les informations d’aide.|Facultatif|
|/help|Imprimer les informations d’aide.|Facultatif|

 **Exemples**

- ManifestFromResources/Resources : D:\Images/assembly : My. assembly. Name/isNative

- ManifestFromResources/resources:D:\Images\Image1.png ;D : \Images\Image1.xaml/assembly : My. assembly. Name/manifest : MyImageManifest. imagemanifest

- ManifestFromResources/resources:D:\Images\Image1.png ;D : \Images\Image1.xaml/assembly : My. assembly. Name/guidName : MyImages/newGuids/newIds

## <a name="notes"></a>Remarques

- L’outil ne prend en charge que les fichiers .png et. Xaml. Toutes les autres types d’images ou de fichiers seront ignorés. Un avertissement est généré pour tous les types non pris en charge rencontrés lors de l’analyse des ressources. Si aucune image prise en charge n’est trouvée lorsque l’outil a terminé l’analyse des ressources, une erreur est générée.

- En suivant le format suggéré pour les images .png, l’outil définit la taille/dimension de la .png sur la taille spécifiée au format, même si elle diffère de la taille réelle de l’image.

- Le format de largeur/hauteur peut être omis pour les images .png, mais l’outil lira la largeur/hauteur réelle de l’image et utilisera celles-ci pour la taille/la valeur de dimension de l’image.

- L’exécution de cet outil sur la même bande d’images à plusieurs reprises pour le même. imagemanifest entraîne la duplication des entrées de manifeste, car l’outil tente de fractionner la bande d’images en images autonomes et de les ajouter au manifeste existant.

- La fusion (omission de/newGuids ou/newIds) ne doit être effectuée que pour les manifestes générés par l’outil. Les manifestes qui ont été personnalisés ou générés par d’autres moyens peuvent ne pas être fusionnés correctement.

- Les manifestes générés pour les assemblys natifs devront peut-être être modifiés manuellement après la génération afin que les symboles d’ID correspondent aux ID de ressource du fichier. RC de l’assembly natif.

## <a name="sample-output"></a>Exemple de sortie
 **Manifeste d’image simple**

 Un manifeste d’image sera semblable à ce .xml fichier :

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImage" Value="0" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage)">
      <Source Uri="$(Resources)/Xaml/MyImage.xaml" />
      <Source Uri="$(Resources)/Png/MyImage.16.16.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```

 **Manifeste d’image pour une bande d’images**

 Un manifeste d’image pour une bande d’images sera semblable à ce .xml fichier :

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImageStrip_0" Value="1" />
    <ID Name="MyImageStrip_1" Value="2" />
    <ID Name="MyImageStrip" Value="3" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)">
      <Source Uri="$(Resources)/MyImageStrip_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)">
      <Source Uri="$(Resources)/MyImageStrip_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists>
    <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)">
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" />
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" />
    </ImageList>
  </ImageLists>
</ImageManifest>
```

 **Manifeste d’image pour les ressources d’image d’assembly Native**

 Un manifeste d’image pour les images natives sera semblable à ce .xml fichier :

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15198 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" />
    <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" />
    <ID Name="MyImage1" Value="0" />
    <ID Name="MyImage2" Value="1" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage1)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage1)" Type="PNG" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage2)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage2)" Type="PNG" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```
