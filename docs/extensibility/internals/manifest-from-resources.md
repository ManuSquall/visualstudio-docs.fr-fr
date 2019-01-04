---
title: Manifeste à partir de ressources | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f1affa200527e770dc87c51c4bb6f7b8a088fcc0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959368"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
Le manifeste à partir de l’outil de ressources est une application console qui prend une liste de ressources d’images (fichiers .png ou .xaml) et génère un fichier .imagemanifest qui permet à ces images à utiliser avec le Service d’images Visual Studio. En outre, cet outil peut être utilisé pour ajouter des images à un .imagemanifest existant. Cet outil est utile pour ajouter la prise en charge de haute résolution et des thèmes pour les images à une extension Visual Studio. Le fichier .imagemanifest généré doit être inclus dans et déployé dans le cadre d’une extension de Visual Studio (.vsix).  
  
## <a name="how-to-use-the-tool"></a>Comment utiliser l’outil  
 **Syntaxe**  
  
 ManifestFromResources /ressources :\<Dir1 > ;\< Img1 >/assembly :\<AssemblyName > \<arguments facultatifs >  
  
 **Arguments**  
  
||||  
|-|-|-|  
|**Nom du commutateur**|**Notes**|**Obligatoire ou facultatif**|  
|/Resources|Une liste délimitée par des points-virgules des images ou des répertoires. Cette liste doit toujours contenir la liste complète des images qui figurent dans le manifeste. Si seule une liste partielle est fournie, les entrées non incluses seront perdues.<br /><br /> Si un fichier de ressources donné est une bande d’image, l’outil sera scindez-le en images distinctes avant d’ajouter chaque sous-image au manifeste.<br /><br /> Si l’image est un fichier .png, nous recommandons de que vous mettre en forme le nom comme suit afin que l’outil peut remplir les attributs appropriés pour l’image : \<Nom >. \<Largeur >. \<Hauteur > .png.|Obligatoire|  
|assembly|Le nom de l’assembly managé (sans compter l’extension) ou le chemin d’accès de l’exécution de l’assembly natif qui héberge les ressources (relatif à l’emplacement du runtime du manifeste).|Obligatoire|  
|/ manifeste|Nom à donner au fichier .imagemanifest généré. Cela peut également inclure un chemin d’accès absolu ou relatif pour créer le fichier dans un autre emplacement. Le nom par défaut correspond au nom de l’assembly.<br /><br /> Par défaut : \<Répertoire actif >\\< Assembly\>.imagemanifest|Facultatif|  
|/guidName|Le nom à donner au symbole GUID pour toutes les images dans le manifeste généré.<br /><br /> Par défaut : AssetsGuid|Facultatif|  
|/rootPath|Le chemin d’accès racine devant être supprimées avant de créer des URI de ressource managée. (Cet indicateur est d’aider avec les cas où l’outil Obtient le chemin d’accès URI relatif incorrect, à l’origine des ressources qui ne parviennent pas à charger.)<br /><br /> Par défaut : \<Répertoire actif >|Facultatif|  
|/ Recursive|Définition de cet indicateur indique à l’outil de manière récursive tous les répertoires de recherche dans l’argument /resources. L’omission de cet indicateur entraîne une recherche top-niveau uniquement des répertoires.|Facultatif|  
|/isNative|Définissez cet indicateur lorsque l’argument de l’assembly est un chemin d’accès pour un assembly natif. Omettre cet indicateur lorsque l’argument de l’assembly est le nom d’un assembly managé. (Voir la section Notes pour plus d’informations sur cet indicateur.)|Facultatif|  
|/newGuids|Cet indicateur indique à l’outil pour créer une nouvelle valeur pour le symbole GUID d’images au lieu de la fusion de celui à partir du manifeste existant.|Facultatif|  
|/newIds|Cet indicateur indique à l’outil pour créer de nouvelles valeurs de symbole d’ID pour chaque image au lieu de la fusion de valeurs à partir du manifeste existant.|Facultatif|  
|/noLogo|Définition de cet indicateur, les informations de copyright et de produit à partir de l’impression s’arrête.|Facultatif|  
|/?|Afficher les informations d’aide.|Facultatif|  
|/help|Afficher les informations d’aide.|Facultatif|  
  
 **Exemples**  
  
-   ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds  
  
## <a name="notes"></a>Notes  
  
-   L’outil prend uniquement en charge les fichiers .png et .xaml. D’autres types de fichier image ou seront ignorés. Un avertissement est généré pour tous les types non pris en charge rencontrés lors de l’analyse les ressources. Si non pris en charge les images sont trouvent lorsque l’outil a terminé l’analyse les ressources, une erreur sera générée  
  
-   En suivant le format recommandé pour les images .png, l’outil définir la valeur de la dimension de la taille de la .png à la taille du format spécifié, même si elle diffère de la taille réelle de l’image.  
  
-   Le format de la largeur/hauteur peut être omis pour les images .png, mais l’outil lit la largeur/hauteur réelle de l’image et les utiliser pour la valeur de dimension de la taille de l’image.  
  
-   Exécution de cet outil sur la même bande d’image plusieurs fois pour la même .imagemanifest entraîne manifestes des entrées en double, car l’outil tente de fractionner la bande d’images en images autonomes et ajoutez-les au manifeste existant.  
  
-   Fusion (en omettant /newGuids ou /newIds) doit être effectuée uniquement pour les manifestes générés par un outil. Manifestes qui ont été personnalisés ou générés par d’autres moyens ne peuvent pas être fusionnées correctement.  
  
-   Les manifestes sont générés pour les assemblys natifs devrez peut-être être modifié manuellement après génération pour rendre les symboles de l’ID correspond à la ressource ID à partir du fichier .rc de l’assembly natif.  
  
## <a name="sample-output"></a>Résultat de l'exemple  
 **Manifeste de l’image simple**  
  
 Un manifeste de l’image sera semblable à ce fichier .xml :  
  
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
  
 **Manifeste de l’image pour une bande d’image**  
  
 Un manifeste d’image pour une bande d’image sera semblable à ce fichier .xml :  
  
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
  
 **Manifeste de l’image pour les ressources d’image de l’assembly natif**  
  
 Un manifeste de l’image pour les images natives sera semblable à ce fichier .xml :  
  
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