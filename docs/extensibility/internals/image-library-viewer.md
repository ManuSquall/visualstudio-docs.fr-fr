---
title: Visualiseur de bibliothèque d’images (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7c5eda24c235cddec99cb5177c6ed315978bc6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707750"
---
# <a name="image-library-viewer"></a>Visionneuse de bibliothèque d’images
L’outil Visual Studio Image Library Viewer peut charger et rechercher des manifestes d’image, permettant à l’utilisateur de les manipuler de la même manière que Visual Studio. L’utilisateur peut modifier l’arrière-plan, les tailles, le DPI, le contraste élevé et d’autres paramètres. L’outil affiche également des informations de chargement pour chaque manifeste d’image et affiche des informations source pour chaque image dans le manifeste de l’image. Cet outil est utile pour :

1. Erreurs de diagnostic

2. S’assurer que les attributs sont définis correctement dans les manifestes d’image personnalisés

3. Recherche d’images dans le Visual Studio Image Catalog afin qu’une extension Visual Studio puisse utiliser des images qui correspondent au style de Visual Studio

   ![Visionneuse de bibliothèque d’images - Hero](../../extensibility/internals/media/image-library-viewer-hero.png "Visionneuse de bibliothèque d’images - Hero")

   **Surnom d’image**

   Un surnom d’image (ou surnom pour faire court) est une paire GUID:ID qui identifie de façon unique un actif d’image ou un actif de liste d’images dans la bibliothèque d’images.

   **Fichiers de manifeste d’image**

   Les fichiers de manifeste d’image (.imagemanifest) sont des fichiers XML qui définissent un ensemble d’actifs d’image, les surnoms qui représentent ces actifs, et l’image réelle ou les images qui représentent chaque actif. Les manifestes d’image peuvent définir des images autonomes ou des listes d’images pour le support d’interface utilisateur hérité. En outre, il existe des attributs qui peuvent être définis soit sur l’actif ou sur les images individuelles derrière chaque actif pour changer quand et comment ces actifs sont affichés.

   **Schéma manifeste d’image**

   Un manifeste d’image complet ressemble à ceci :

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Guid, ID, or String elements -->
      </Symbols>
      <!-- zero or one Images elements -->
      <Images>
        <!-- zero or more Image elements -->
      </Images>
      <!-- zero or one ImageLists elements -->
      <ImageLists>
        <!-- zero or more ImageList elements -->
      </ImageLists>
</ImageManifest>
```

 **Symboles**

 En tant qu’aide à la lisibilité et à l’entretien, le manifeste de l’image peut utiliser des symboles pour les valeurs d’attribut. Les symboles sont définis comme ceci :

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|||
|-|-|
|**Sous-élément**|**Définition**|
|Importer|Importe les symboles du fichier manifeste donné pour une utilisation dans le manifeste actuel.|
|Guid|Le symbole représente un GUID et doit correspondre au formatage GUID.|
|id|Le symbole représente une pièce d’identité et doit être un intégrateur non natif.|
|String|Le symbole représente une valeur de chaîne arbitraire.|

 Les symboles sont sensibles aux cas et référencés à l’aide d’une syntaxe de $(symbol-name) :

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Certains symboles sont prédéfinis pour tous les manifestes. Ceux-ci peuvent être utilisés dans \<l’attribut Uri de la Source> ou \<Import> élément de référence sur la machine locale.

|||
|-|-|
|**Symbole**|**Description**|
|CommonProgramFiles|La valeur de la variable de l’environnement %CommonProgramFiles%|
|LocalAppData (localAppData)|La valeur de la variable de l’environnement %LocalAppData%|
|ManifesteFolder|Le dossier contenant le fichier manifeste|
|MyDocuments (en)|Le chemin complet du dossier Mes Documents de l’utilisateur actuel|
|ProgramFiles|La valeur de la variable de l’environnement % ProgramFiles %|
|Système|Le dossier Windows-System32|
|WinDir (WinDir)|La valeur de la variable de l’environnement %WinDir%|

 **Image**

 L’élément \<Image> définit une image qui peut être référencée par un surnom. Le GUID et l’ID pris ensemble forment le surnom d’image. Le surnom de l’image doit être unique dans toute la bibliothèque d’images. Si plus d’une image a un surnom donné, la première rencontrée lors de la construction de la bibliothèque est celle qui est conservée.

 Il doit contenir au moins une source. Bien que les sources neutres en taille donneront les meilleurs résultats à travers un large éventail de tailles, elles ne sont pas nécessaires. Si le service est demandé pour une image \<d’une taille non définie dans l’élément Image> et qu’il n’y a pas de source neutre sur mesure, le service choisira la meilleure source spécifique à la taille et l’échelle à la taille demandée.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**Attribut**|**Définition**|
|Guid|[Requis] La partie GUID du surnom d’image|
|id|[Requis] La partie ID du surnom d’image|
|AutoriserColorInversion|[Optionnel, par défaut vrai] Indique si l’image peut avoir ses couleurs programmatiquement inversées lorsqu’elles sont utilisées sur un fond sombre.|

 **Source**

 L’élément \<Source> définit un actif unique de source d’image (XAML et PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**Attribut**|**Définition**|
|Uri|[Requis] Un URI qui définit d’où l’image peut être chargée. Les valeurs possibles sont les suivantes :<br /><br /> - Un [pack URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) utilisant l’autorité application:///<br /><br /> - Une référence absolue des ressources composant<br /><br /> - Un chemin vers un fichier contenant une ressource autochtone|
|Arrière-plan|[Facultatif] Indique ce que sur le type de fond de la source est destinée à être utilisé.<br /><br /> Les valeurs possibles sont les suivantes :<br /><br /> - *Lumière*: La source peut être utilisée sur un fond léger.<br /><br /> - *Dark*: La source peut être utilisée sur un fond sombre.<br /><br /> - *HighContrast*: La source peut être utilisée sur n’importe quel fond en mode High Contrast.<br /><br /> - *HighContrastLight*: La source peut être utilisée sur un fond lumineux en mode Contraste élevé.<br /><br /> -*HighContrastDark*: La source peut être utilisée sur un fond sombre en mode Contraste élevé.<br /><br /> Si **l’attribut d’arrière-plan** est omis, la source peut être utilisée sur n’importe quel fond.<br /><br /> Si **Background** is *Light*, *Dark*, *HighContrastLight*, ou *HighContrastDark*, les couleurs de la source ne sont jamais inversées. Si **Background** est omis ou réglé à *HighContrast*, l’inversion des couleurs de la source est contrôlée par l’attribut **AllowColorInversion** de l’image.|

 Un \<élément source> peut avoir exactement l’un des sous-ensembles optionnels suivants :

||||
|-|-|-|
|**Élément**|**Attributs (tous requis)**|**Définition**|
|\<Taille>|Valeur|La source sera utilisée pour des images de la taille donnée (dans les unités de périphérique). L’image sera carrée.|
|\<SizeRange>|MinSize, MaxSize|La source sera utilisée pour les images de MinSize à MaxSize (en unités d’appareils) inclusivement. L’image sera carrée.|
|\<Dimensions>|Width, Height|La source sera utilisée pour des images de la largeur et de la hauteur données (dans les unités de périphérique).|
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|La source sera utilisée pour les images de la largeur/hauteur minimale à la largeur/hauteur maximale (dans les unités de périphérique) inclusivement.|

 Un \<élément source> peut également \<avoir un sous-ensemble de> NativeResource en option, qui définit un \<> source qui est chargé à partir d’une assemblée autochtone plutôt qu’un assemblage géré.

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**Attribut**|**Définition**|
|Type|[Requis] Le type de ressource indigène, soit XAML ou PNG|
|id|[Requis] La partie ID integer de la ressource autochtone|

 **Imagelist**

 L’élément \<ImageList> définit une collection d’images qui peuvent être retournées en une seule bande. La bande est construite sur demande, au besoin.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**Attribut**|**Définition**|
|Guid|[Requis] La partie GUID du surnom d’image|
|id|[Requis] La partie ID du surnom d’image|
|Externe|[Optionnel, faux par défaut] Indique si le surnom d’image fait référence à une image dans le manifeste actuel.|

 Le surnom de l’image contenue n’a pas à référencer une image définie dans le manifeste actuel. Si l’image contenue ne peut pas être trouvée dans la bibliothèque d’images, une image blanche de placeholder sera utilisée à sa place.

## <a name="how-to-use-the-tool"></a>Comment utiliser l’outil
 **Validation d’un manifeste d’image personnalisé**

 Pour créer un manifeste personnalisé, nous vous recommandons d’utiliser l’outil ManifestFromResources pour autogénérer le manifeste. Pour valider le manifeste personnalisé, lancez le Visual de la Bibliothèque d’images et sélectionnez File > Set Paths... d’ouvrir le dialogue des répertoires de recherche. L’outil utilisera les répertoires de recherche pour charger les manifestes d’image, mais il les utilisera également pour trouver les fichiers .dll qui contiennent les images dans un manifeste, alors assurez-vous d’inclure à la fois les répertoires manifeste et DLL dans ce dialogue.

 ![Visionneuse de bibliothèque d’images - Rechercher](../../extensibility/internals/media/image-library-viewer-search.png "Visionneuse de bibliothèque d’images - Rechercher")

 Cliquez **sur Ajouter ...** pour sélectionner de nouveaux répertoires de recherche à la recherche de manifestes et de leurs DLL correspondants. L’outil se souviendra de ces répertoires de recherche, et ils peuvent être activés ou désactivés en cochant ou en décochant un répertoire.

 Par défaut, l’outil tentera de trouver le visual Studio installer répertoire et ajouter ces répertoires à la liste des répertoires de recherche. Vous pouvez ajouter manuellement des répertoires que l’outil ne trouve pas.

 Une fois que tous les manifestes sont chargés, l’outil peut être utilisé pour basculer les couleurs **de fond,** **DPI**, **contraste élevé**, ou la mise à **l’échelle grise** pour les images afin qu’un utilisateur puisse inspecter visuellement les ressources d’image pour vérifier qu’ils sont rendus correctement pour divers paramètres.

 ![Visionneuse de bibliothèque d’images - Arrière-plan](../../extensibility/internals/media/image-library-viewer-background.png "Visionneuse de bibliothèque d’images - Arrière-plan")

 La couleur de fond peut être réglée à la lumière, à l’obscurité ou à une valeur personnalisée. La sélection de "Custom Color" ouvrira un dialogue de sélection de couleurs et ajoutera cette couleur personnalisée au bas de la boîte combo de fond pour un rappel facile plus tard.

 ![Visionneuse de bibliothèque d’images - Couleur personnalisée](../../extensibility/internals/media/image-library-viewer-custom-color.png "Visionneuse de bibliothèque d’images - Couleur personnalisée")

 La sélection d’un surnom d’image affiche les informations pour chaque image réelle derrière ce surnom dans le volet Détails d’image sur la droite. Le volet permet également aux utilisateurs de copier un surnom par nom ou par la valeur GUID:ID brute.

 ![Visionneuse de bibliothèque d’images - Détails d’une image](../../extensibility/internals/media/image-library-viewer-image-details.png "Visionneuse de bibliothèque d’images - Détails d’une image")

 Les informations affichées pour chaque source d’image comprennent le type d’arrière-plan sur qui l’afficher, si elle peut être sur le thème ou prend en charge High Contrast, quelles tailles il est valable pour ou si elle est neutre sur mesure, et si l’image provient d’un assemblage natif.

 ![Visionneuse de bibliothèque d’images - Possibilité d’appliquer un thème](../../extensibility/internals/media/image-library-viewer-can-theme.png "Visionneuse de bibliothèque d’images - Possibilité d’appliquer un thème")

 Lors de la validation d’un manifeste d’image, nous vous recommandons de déployer le manifeste et l’image DLL dans leurs emplacements du monde réel. Cela permettra de vérifier que tous les chemins relatifs fonctionnent correctement et que la bibliothèque d’images peut trouver et charger le manifeste et l’image DLL.

 **Recherche de catalogue d’images KnownMonikers**

 Pour mieux correspondre au style Visual Studio, une extension Visual Studio peut utiliser des images dans le visual Studio Image Catalog plutôt que de créer et d’utiliser le sien. Cela a l’avantage de ne pas avoir à maintenir ces images, et garantit que l’image aura une image de support haute DPI de sorte qu’il devrait sembler correct dans tous les paramètres DPI que Visual Studio prend en charge.

 Le visualiseur de la bibliothèque d’images permet de rechercher un manifeste afin qu’un utilisateur puisse trouver le surnom qui représente un actif d’image et utiliser ce surnom dans le code. Pour rechercher des images, entrez le terme de recherche souhaité dans la boîte de recherche et appuyez sur Enter. La barre d’état en bas affichera le nombre de correspondances trouvées sur le nombre total d’images dans tous les manifestes.

 ![Visionneuse de bibliothèque d’images - Filtre](../../extensibility/internals/media/image-library-viewer-filter.png "Visionneuse de bibliothèque d’images - Filtre")

 Lors de la recherche de surnoms d’image dans les manifestes existants, nous vous recommandons de rechercher et d’utiliser uniquement les surnoms du Visual Studio Image Catalog, d’autres surnoms volontairement accessibles au public, ou vos propres surnoms personnalisés. Si vous utilisez des surnoms non publics, l’interface utilisateur personnalisée peut être cassée ou faire changer ses images de manière inattendue si ou quand ces surnoms et images non publics sont modifiés ou mis à jour.

 En outre, la recherche par GUID est possible. Ce type de recherche est utile pour filtrer la liste à un seul manifeste, ou sous-section unique d’un manifeste si ce manifeste contient plusieurs GUIDs.

 ![Visionneuse de bibliothèque d’images - GUID de filtre](../../extensibility/internals/media/image-library-viewer-filter-guid.png "Visionneuse de bibliothèque d’images - GUID de filtre")

 Enfin, la recherche par PIÈCE d’identité est possible ainsi.

 ![Visionneuse de bibliothèque d’images - ID de filtre](../../extensibility/internals/media/image-library-viewer-filter-id.png "Visionneuse de bibliothèque d’images - ID de filtre")

## <a name="notes"></a>Notes

- Par défaut, l’outil tirera dans plusieurs manifestes d’image présents dans le répertoire d’installation Visual Studio. Le seul qui a publiquement des surnoms consommables est le manifeste **Microsoft.VisualStudio.ImageCatalog.** GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (ne **remplacez pas** ce GUID dans un manifeste personnalisé) Type: KnownMonikers

- L’outil tente de lancer pour charger toutes les manifestations d’image qu’il trouve, de sorte qu’il pourrait prendre plusieurs secondes pour l’application à apparaître réellement. Il peut également être lent ou non réactif pendant le chargement des manifestes.

## <a name="sample-output"></a>Exemple de sortie
 Cet outil ne génère aucune sortie.
