---
title: Image visionneuse de bibliothèque | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 749441e960363fe208e3ad67288180c1935db35f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62860610"
---
# <a name="image-library-viewer"></a>Visionneuse de bibliothèque d’images
L’outil Visual Studio Image Library Viewer peut charger et rechercher des manifestes d’images, permettant à l’utilisateur pour les manipuler dans la même façon Visual Studio. L’utilisateur peut modifier en arrière-plan, tailles, PPP, contraste élevé et autres paramètres. L’outil affiche des informations de chargement pour chaque manifeste de l’image également et affiche des informations de source de chaque image dans le manifeste de l’image. Cet outil est utile pour :

1. Diagnostic des erreurs

2. S’assurer que les attributs sont correctement définies dans les manifestes de l’image personnalisée

3. Recherche d’images dans le catalogue d’images Visual Studio afin qu’une extension Visual Studio peut utiliser des images qui tiennent le style de Visual Studio

   ![Image de bannière de visionneuse de bibliothèque](../../extensibility/internals/media/image-library-viewer-hero.png "héros de visionneuse de bibliothèque d’images")

   **Moniker de l’image**

   Un moniker d’image (ou moniker en abrégé) est une paire GUID : ID qui identifie de façon unique un composant de l’image ou le composant de liste l’image dans la bibliothèque d’images.

   **Fichiers de manifeste d’image**

   Fichiers de manifeste (.imagemanifest) d’image sont des fichiers XML qui définissent un ensemble de ressources d’image, les monikers qui représentent ces actifs et l’image réelle ou des images qui représentent chaque élément multimédia. Manifestes d’images peuvent définir des images autonomes ou les listes d’images pour la prise en charge héritée de l’interface utilisateur. En outre, il existe des attributs qui peuvent être définies sur l’élément multimédia ou sur des images individuelles derrière chaque élément multimédia pour modifier quand et comment ces actifs sont affichés.

   **Schéma de manifeste d’image**

   Un manifeste de finalisation d’image se présente comme suit :

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

 Comme une meilleure lisibilité et la maintenance d’aide, le manifeste de l’image peut utiliser les symboles pour les valeurs d’attribut. Symboles qui sont définis comme suit :

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
|Import|Importe les symboles du fichier manifeste donné pour une utilisation dans le manifeste en cours.|
|GUID|Le symbole représente un GUID et doit correspondre à la mise en forme de GUID.|
|Id|Le symbole représente un ID et doit être un entier non négatif.|
|Chaîne|Le symbole représente une valeur de chaîne arbitraire.|

 Symboles respectent la casse et référencée à l’aide de la syntaxe de $(symbol-name) :

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Certains symboles sont prédéfinis pour tous les manifestes. Celles-ci peuvent être utilisées dans l’attribut Uri de la \<Source > ou \<importation > élément aux chemins d’accès de référence sur l’ordinateur local.

|||
|-|-|
|**Symbol**|**Description**|
|CommonProgramFiles|La valeur de la variable d’environnement % %CommonProgramFiles%|
|LocalAppData|La valeur de la variable d’environnement % LocalAppData|
|ManifestFolder|Le dossier contenant le fichier manifest|
|MyDocuments|Le chemin d’accès complet du dossier Mes Documents de l’utilisateur actuel|
|ProgramFiles|La valeur de la variable d’environnement % ProgramFiles %|
|Système|The Windows\System32 folder|
|WinDir|La valeur de la variable d’environnement % WinDir %|

 **Image**

 Le \<Image > élément définit une image qui peut être référencée par un moniker. Le GUID et l’ID d’ensemble forment le moniker d’image. Le moniker de l’image doit être unique dans la bibliothèque de l’intégralité de l’image. Si plusieurs images a un moniker donné, le premier a rencontré lors de la création de la bibliothèque est celui qui est conservé.

 Il doit contenir au moins une source. Bien qu’il est indépendant de la taille des sources donnera les meilleurs résultats sur un large éventail de tailles, ils ne sont plus nécessaires. Si le service est demandé pour une image d’une taille non définie dans le \<Image > élément et qu’aucune source indépendant de la taille, le service de choisir la meilleure source spécifiques à la taille et l’échelle à la taille demandée.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**Attribut**|**Définition**|
|GUID|[Obligatoire] La partie GUID du moniker d’image|
|Id|[Obligatoire] La partie de l’ID du moniker d’image|
|AllowColorInversion|[Facultatif, par défaut la valeur true] Indique si l’image peut avoir ses couleurs inversées par programme lorsqu’il est utilisé sur un arrière-plan sombre.|

 **Source**

 Le \<Source > élément définit une seule source ressource (XAML et PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**Attribut**|**Définition**|
|URI|[Obligatoire] URI qui définit où l’image peut être chargé à partir de. Il peut avoir l'une des valeurs suivantes :<br /><br /> -A [URI à en-tête Pack](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) à l’aide de l’application : / / / autorité<br /><br /> -Une référence de ressource du composant absolu<br /><br /> -Un chemin d’accès à un fichier contenant une ressource native|
|Présentation|[Facultatif] Indique quel type d’arrière-plan de que la source est destinée à être utilisée.<br /><br /> Il peut avoir l'une des valeurs suivantes :<br /><br /> - *Lumière*: La source peut être utilisée sur un arrière-plan clair.<br /><br /> - *Foncé*: La source peut être utilisée sur un arrière-plan sombre.<br /><br /> - *Contraste élevé*: La source peut être utilisée sur n’importe quel arrière-plan en mode contraste élevé.<br /><br /> - *HighContrastLight*: La source peut être utilisée sur un arrière-plan clair en mode de contraste élevé.<br /><br /> -*HighContrastDark*: La source peut être utilisée sur un arrière-plan sombre en mode de contraste élevé.<br /><br /> Si le **arrière-plan** attribut est omis, la source peut être utilisée sur n’importe quel arrière-plan.<br /><br /> Si **arrière-plan** est *Light*, *foncé*, *HighContrastLight*, ou *HighContrastDark*, le les couleurs de la source ne sont jamais inversées. Si **arrière-plan** est omis ou défini sur *contraste élevé*, l’inversion des couleurs de la source est contrôlée par l’image **AllowColorInversion** attribut.|

 Un \<Source > élément peut avoir un seul des sous-éléments facultatives suivantes :

||||
|-|-|-|
|**Élément**|**Attributs (tous requis)**|**Définition**|
|\<Taille >|Value|La source sera utilisée pour les images de la taille spécifiée (en unités de périphérique). L’image sera carré.|
|\<SizeRange>|MinSize, MaxSize|La source servira pour les images à partir de MinSize vers taille maximale (en unités de périphérique) (inclus). L’image sera carré.|
|\<Dimensions>|Largeur, hauteur|La source sera utilisée pour les images de la donnée de la largeur et la hauteur (en unités de périphérique).|
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|La source servira pour les images à partir de la largeur/hauteur minimale de la largeur/hauteur maximale (en unités de périphérique) (inclus).|

 Un \<Source > élément peut également avoir un facultatif \<NativeResource > sous-élément qui définit un \<Source > qui est chargé à partir d’un assembly natif plutôt qu’un assembly managé.

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**Attribut**|**Définition**|
|Type|[Obligatoire] Le type de la ressource native, XAML ou PNG|
|Id|[Obligatoire] La partie ID d’entier de la ressource native|

 **ImageList**

 Le \<ImageList > élément définit une collection d’images qui peuvent être retournées dans une bande unique. La bande est basée sur la demande, en fonction des besoins.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**Attribut**|**Définition**|
|GUID|[Obligatoire] La partie GUID du moniker d’image|
|Id|[Obligatoire] La partie de l’ID du moniker d’image|
|Ressource externe|[False par défaut facultative] Indique si le moniker d’image fait référence à une image dans le manifeste en cours.|

 Le moniker de l’image de relation contenant-contenu n’a pas référencer une image définie dans le manifeste en cours. Si l’image de relation contenant-contenu est introuvable dans la bibliothèque d’images, une image d’espace réservé vide sera utilisée à la place.

## <a name="how-to-use-the-tool"></a>Comment utiliser l’outil
 **Validation d’un manifeste de l’image personnalisée**

 Pour créer un manifeste personnalisé, nous vous recommandons d’utiliser l’outil ManifestFromResources pour générer automatiquement le manifeste. Pour valider le manifeste personnalisé, lancez l’Afficheur de bibliothèque d’images et sélectionnez Fichier > définir les chemins... pour ouvrir la boîte de dialogue répertoires de recherche. L’outil utilisera les répertoires de recherche pour charger les manifestes d’images, mais il sera également l’utiliser à trouver les fichiers .dll qui contiennent les images dans un manifeste, par conséquent, veillez à inclure le manifeste et les répertoires de la DLL dans cette boîte de dialogue.

 ![Recherche de visionneuse de bibliothèque d’images](../../extensibility/internals/media/image-library-viewer-search.png "recherche de visionneuse de bibliothèque d’images")

 Cliquez sur **ajouter...**  pour sélectionner les nouveaux répertoires de recherche pour rechercher des manifestes et leurs DLL correspondante. L’outil enregistre ces répertoires de recherche, et ils peuvent être activées ou désactivée en cochant ou non un répertoire.

 Par défaut, l’outil tente de trouver le répertoire d’installation de Visual Studio et ajoutez ces répertoires à la liste de répertoires de recherche. Vous pouvez ajouter manuellement l’outil ne trouve pas de répertoires.

 Une fois que tous les manifestes sont chargés, l’outil peut être utilisé pour activer/désactiver **arrière-plan** couleurs, **PPP**, **contraste élevé**, ou **grayscaling** pour les images afin qu’un utilisateur peut inspecter visuellement les ressources d’image pour vérifier qu’ils sont restituées correctement pour différents paramètres.

 ![Image d’arrière-plan de visionneuse de bibliothèque](../../extensibility/internals/media/image-library-viewer-background.png "de l’Image d’arrière-plan de visionneuse de bibliothèque")

 La couleur d’arrière-plan peut être la valeur est clair, sombre ou une valeur personnalisée. En sélectionnant « Couleur personnalisée » pour ouvrir une boîte de dialogue de sélection de couleur et ajouter une couleur personnalisée vers le bas de la zone de liste déroulante d’arrière-plan pour vous en souvenir facilement plus tard.

 ![Couleur personnalisée de visionneuse de bibliothèque d’images](../../extensibility/internals/media/image-library-viewer-custom-color.png "couleur personnalisée de visionneuse de bibliothèque d’images")

 Sélection d’un moniker de l’image affiche les informations pour chaque image réelle derrière ce moniker dans le volet de détails de l’Image sur la droite. Le volet permet également aux utilisateurs de copier un moniker par nom ou par la valeur de la paire GUID : ID brutes.

 ![Image des détails de l’Image visionneuse bibliothèque](../../extensibility/internals/media/image-library-viewer-image-details.png "détails de l’Image visionneuse bibliothèque d’images")

 Les informations affichées pour chaque source de l’image inclut le type d’arrière-plan pour l’afficher, si elle peut être à thème ou prend en charge de contraste élevé, les tailles est valide pour ou s’il est indépendant de la taille, et indique si l’image provient d’un assembly natif.

 ![Visionneuse de bibliothèque d’images peut thème](../../extensibility/internals/media/image-library-viewer-can-theme.png "visionneuse de bibliothèque d’images peut thème")

 Lors de la validation d’un manifeste d’image, nous vous recommandons de déployer le manifeste et l’image DLL dans leurs emplacements du monde réel. Cela permettra de vérifier que les chemins d’accès relatifs sont fonctionne correctement et que la bibliothèque d’images peut rechercher et charger le manifeste et l’image DLL.

 **Recherche de catalogue de l’image KnownMonikers**

 Pour mieux faire correspondre les styles de Visual Studio, une extension Visual Studio peut utiliser des images dans le catalogue des images de Visual Studio, plutôt que la création et l’utilisation de son propre. Cela présente l’avantage de ne pas avoir à maintenir ces images et garantit que l’image aura une image haute résolution sauvegarde afin qu’il doit se présenter correct dans tous les paramètres PPP qui prend en charge de Visual Studio.

 L’Afficheur de bibliothèque d’images permet un manifeste à rechercher afin qu’un utilisateur peut rechercher le moniker qui représente un composant de l’image et utiliser ce moniker dans le code. Pour rechercher des images, entrez le terme de recherche souhaitée dans la zone de recherche et appuyez sur ENTRÉE. La barre d’état en bas affichera le nombre de correspondances ont été trouvé en dehors du nombre total d’images dans tous les manifestes.

 ![Filtre de visionneuse de bibliothèque d’images](../../extensibility/internals/media/image-library-viewer-filter.png "filtre de visionneuse de bibliothèque d’images")

 Lors de la recherche pour les monikers d’image dans les manifestes existants, nous vous recommandons de rechercher et d’utiliser uniquement des monikers le Visual Studio Image du catalogue, autres monikers intentionnellement accessibles au public ou votre propre monikers personnalisés. Si vous utilisez des monikers non publics, interface utilisateur personnalisée est peut-être rompu ou ont ses images changé de façon inattendue si ou lorsque ces monikers non publics et les images sont modifiés ou mis à jour.

 En outre, il est possible de la recherche par GUID. Ce type de recherche est utile pour filtrer la liste à un seul manifeste, ou une sous-section unique d’un manifeste si ce manifeste contient plusieurs GUID.

 ![Filtre de visionneuse de bibliothèque GUID de l’image](../../extensibility/internals/media/image-library-viewer-filter-guid.png "filtre de visionneuse de bibliothèque GUID de l’Image")

 Enfin, la recherche par ID est possible également.

 ![ID de filtre de visionneuse de bibliothèque de l’image](../../extensibility/internals/media/image-library-viewer-filter-id.png "ID de filtre de visionneuse de bibliothèque de l’Image")

## <a name="notes"></a>Notes

- Par défaut, l’outil permet d’extraire plusieurs manifestes d’images présents dans le répertoire d’installation de Visual Studio. Est le seul qui a des monikers publiquement consommables le **Microsoft.VisualStudio.ImageCatalog** manifeste. GUID : ae27a6b0-e345-4288-96df-5eaf394ee369 (faire **pas** remplacer ce GUID dans un manifeste personnalisé) Type : KnownMonikers

- L’outil tente de lancement pour charger tous les manifestes d’image qu’il trouve, donc il peut prendre plusieurs secondes pour l’application s’affiche réellement. Il peut également être lente ou ne répondent pas lors du chargement des manifestes.

## <a name="sample-output"></a>Résultat de l'exemple
 Cet outil ne génère pas de sortie.