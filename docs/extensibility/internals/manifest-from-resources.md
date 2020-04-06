---
title: Manifeste des ressources (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb853963cc5ca6fbe6080249daa8fcf9c08bf943
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707279"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
L’outil Manifest from Resources est une application console qui prend une liste de ressources d’image (.png ou .xaml fichiers) et génère un fichier .imagemanifest qui permet à ces images d’être utilisées avec le Visual Studio Image Service. En outre, cet outil peut être utilisé pour ajouter des images à un .imagemanifest existant. Cet outil est utile pour ajouter de l’IDD élevé et le support thématique pour les images à une extension Visual Studio. Le fichier généré .imagemanifest doit être inclus et déployé dans le cadre d’une extension Visual Studio (.vsix).

## <a name="how-to-use-the-tool"></a>Comment utiliser l’outil
 **Syntaxe**

 ManifestDeResources/ressources:\<Dir1>; \<Img1>/assemblage:\<AssemblyName> \<Optional Args>

 **Arguments**

||||
|-|-|-|
|**Nom de commutateur**|**Remarques**|**Requis ou facultatif**|
|/ressources|Une liste d’images ou de répertoires délimitées par des semi-marines. Cette liste doit toujours contenir la liste complète des images qui seront dans le manifeste. Si seulement une liste partielle est donnée, les entrées non incluses seront perdues.<br /><br /> Si un fichier de ressources donné est une bande d’image, l’outil le divisera en images séparées avant d’ajouter chaque sous-image au manifeste.<br /><br /> Si l’image est un fichier .png, nous vous avons recommandé de formater le nom \<comme celui-ci afin que l’outil puisse remplir les attributs droits pour l’image: Nom>. \<Largeur>. \<Hauteur>.png.|Obligatoire|
|/assemblage|Le nom de l’assemblage géré (sans compter l’extension), ou le chemin de course de l’assemblée autochtone qui héberge les ressources (par rapport à l’emplacement de l’heure d’exécution du manifeste).|Obligatoire|
|/manifeste|Le nom à donner au fichier généré .imagemanifest. Cela peut également inclure un chemin absolu ou relatif pour créer le fichier dans un endroit différent. Le nom par défaut correspond au nom de l’assemblage.<br /><br /> Défaut: \<Actuel Répertoire>\\<Assemblée\>.imagemanifest|Facultatif|
|/guidName|Le nom à donner au symbole GUID pour toutes les images dans le manifeste généré.<br /><br /> Défaut : AssetsGuid|Facultatif|
|/rootPath|Le chemin de racine qui doit être dépouillé avant de créer des URI de ressources gérées. (Ce drapeau est d’aider avec les cas où l’outil obtient le chemin relatif URI mal, causant des ressources à ne pas charger.)<br /><br /> Défaut \<: Actuelle> d’annuaire|Facultatif|
|/récursif|La configuration de ce drapeau indique à l’outil de rechercher de façon récursive les répertoires dans l’argument /ressources. L’omission de ce drapeau se traduira par une recherche de haut niveau seulement des répertoires.|Facultatif|
|/isNative|Définissez ce drapeau lorsque l’argument de l’assemblage est un chemin pour une assemblée autochtone. Omettre ce drapeau lorsque l’argument de l’assemblée est le nom d’une assemblée gérée. (Voir la section Notes pour plus d’informations sur ce drapeau.)|Facultatif|
|/newGuids|La configuration de ce drapeau indique à l’outil de créer une nouvelle valeur pour le symbole GUID des images au lieu de fusionner celle du manifeste existant.|Facultatif|
|/newIds|La configuration de ce drapeau indique l’outil pour créer de nouvelles valeurs de symbole d’identification pour chaque image au lieu de fusionner les valeurs à partir du manifeste existant.|Facultatif|
|/noLogo|La configuration de ce drapeau empêche l’impression des informations sur les produits et le droit d’auteur.|Facultatif|
|/?|Imprimez des informations sur l’aide.|Facultatif|
|/help|Imprimez des informations sur l’aide.|Facultatif|

 **Exemples**

- ManifestDeResources /ressources:D:'Images /assembly:My.Assembly.Name /isNative

- ManifestFromResources /ressources: D:'Images’Image1.png;D:'Images’Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest

- ManifestFromResources /ressources:D:-Images-Image1.png;D:'Images’Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds

## <a name="notes"></a>Notes

- L’outil ne prend en charge les fichiers .png et .xaml. Tout autre type d’image ou de fichier sera ignoré. Un avertissement est généré pour tous les types non pris en soutien rencontrés lors de l’analyse des ressources. Si aucune image prise en charge n’est trouvée lorsque l’outil est fini d’analyser les ressources, une erreur sera générée

- En suivant le format suggéré pour les images .png, l’outil définira la valeur de taille/dimension pour le .png à la taille spécifiée par le format, même si elle diffère de la taille réelle de l’image.

- Le format largeur/hauteur peut être omis pour les images .png, mais l’outil lira la largeur réelle de l’image / hauteur et les utiliser pour la taille de l’image / valeur de dimension.

- Exécution de cet outil sur la même bande d’image plusieurs fois pour le même .imagemanifest se traduira par des entrées manifestes en double, parce que l’outil tente de diviser la bande d’image en images autonomes et d’ajouter ceux-ci au manifeste existant.

- La fusion (omettant/newGuids ou/newIds) ne doit être faite que pour les manifestes générés par des outils. Les manifestes qui ont été personnalisés ou générés par d’autres moyens peuvent ne pas être fusionnés correctement.

- Les manifestes générés pour les assemblées autochtones pourraient devoir être modifiés à la main après génération pour faire correspondre les symboles d’identification les identifiants de la ressource id du fichier .rc de l’assemblée indigène.

## <a name="sample-output"></a>Exemple de sortie
 **Manifeste d’image simple**

 Un manifeste d’image sera similaire à ce fichier .xml :

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

 **Manifeste d’image pour une bande d’image**

 Un manifeste d’image pour une bande d’image sera similaire à ce fichier .xml :

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

 **Manifeste d’image pour les ressources d’image d’assemblage indigène**

 Un manifeste d’image pour les images indigènes sera similaire à ce fichier .xml:

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
