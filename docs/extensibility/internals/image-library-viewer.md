---
title: Image visionneuse de bibliothèque | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ee0be99b307955017b896f70019dfc05481717c9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133784"
---
# <a name="image-library-viewer"></a>Visionneuse de bibliothèque d’images
L’outil Visionneuse bibliothèque d’images Visual Studio peut charger et rechercher des manifestes d’images, permettant à l’utilisateur pour les manipuler dans la même façon Visual Studio. L’utilisateur peut modifier en arrière-plan, tailles, PPP, contraste élevé et autres paramètres. Également, l’outil affiche des informations de chargement pour chaque manifeste de l’image et affiche des informations de source pour chaque image dans le manifeste de l’image. Cet outil est utile pour :  
  
1.  Diagnostic d’erreurs  
  
2.  S’assurer que les attributs sont correctement définies dans les manifestes de l’image personnalisée  
  
3.  Recherchez des images dans le catalogue d’images Visual Studio afin que d’une extension Visual Studio peut utiliser des images d’ajuster le style de Visual Studio  
  
 ![Héros de visionneuse de bibliothèque d’images](../../extensibility/internals/media/image-library-viewer-hero.png "héros de visionneuse de bibliothèque d’images")  
  
 **Moniker d’image**  
  
 Un moniker d’image (ou moniker pour la forme courte) est une paire GUID : ID qui identifie de façon unique un composant de l’image ou le composant de liste l’image dans la bibliothèque d’images.  
  
 **Fichiers manifestes d’image**  
  
 Les fichiers image manifeste (.imagemanifest) sont des fichiers XML qui définissent un ensemble de composants de l’image, les monikers qui représentent ces ressources et l’image réelle ou des images qui représentent chaque élément multimédia. Manifestes d’images peuvent définir des images autonomes ou les listes d’images pour la prise en charge héritée de l’interface utilisateur. En outre, il existe des attributs qui peuvent être définies sur l’élément multimédia ou sur des images individuelles derrière chaque élément multimédia pour modifier quand et comment ces éléments sont affichés.  
  
 **Schéma de manifeste d’image**  
  
 Un manifeste de l’image complète ressemble à ceci :  
  
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
  
 Faciliter la lisibilité et la maintenance, le manifeste de l’image permet les symboles pour les valeurs d’attribut. Symboles qui sont définis comme suit :  
  
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
|Import|Importe les symboles du fichier manifeste donné pour une utilisation dans le manifeste actuel.|  
|GUID|Le symbole représente un GUID et doit correspondre à la mise en forme de GUID.|  
|Id|Le symbole représente un ID et doit être un entier non négatif.|  
|Chaîne|Le symbole représente une valeur de chaîne arbitraire.|  
  
 Symboles respectent la casse et référencés à l’aide de la syntaxe de $(symbol-name) :  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 Certains symboles sont prédéfinis pour tous les manifestes. Ils peuvent être utilisés dans l’attribut Uri de la \<Source > ou \<importation > élément aux chemins d’accès de référence sur l’ordinateur local.  
  
|||  
|-|-|  
|**Symbole**|**Description**|  
|CommonProgramFiles|La valeur de la variable d’environnement % %CommonProgramFiles|  
|LocalAppData|La valeur de la variable d’environnement % LocalAppData|  
|ManifestFolder|Le dossier contenant le fichier manifest|  
|Mes documents|Le chemin d’accès complet du dossier Mes Documents de l’utilisateur actuel|  
|ProgramFiles|La valeur de la variable d’environnement % ProgramFiles|  
|Système|Le dossier Windows\System32|  
|WinDir|La valeur de la variable d’environnement % WinDir %|  
  
 **Image**  
  
 Le \<Image > élément définit une image qui peut être référencée par un moniker. Le GUID et l’ID d’ensemble forment le moniker d’image. Le moniker de l’image doit être unique dans la bibliothèque de l’intégralité de l’image. Si plusieurs images a un moniker donné, la première rencontré lors de la génération de la bibliothèque est celui qui est conservé.  
  
 Il doit contenir au moins une source. Bien qu’il est indépendant de la taille des sources donnera les meilleurs résultats sur un large éventail de tailles, ils ne sont plus nécessaires. Si le service est demandé pour une image d’une taille non définie dans le \<Image > élément et qu’aucune source indépendant de la taille, le service de choisir la meilleure source spécifique à la taille et mettre à l’échelle à la taille demandée.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**Attribut**|**Définition**|  
|GUID|[Obligatoire] Le GUID du moniker d’image|  
|Id|[Obligatoire] La partie de l’ID du moniker d’image|  
|AllowColorInversion|[Facultatif, par défaut la valeur true] Indique si l’image peut avoir ses couleurs inversées par programmation les lorsqu’il est utilisé sur un arrière-plan sombre.|  
  
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
|URI|[Obligatoire] URI qui définit où l’image peut être chargée à partir de. Il peut avoir l'une des valeurs suivantes :<br /><br /> -A [URI à en-tête Pack](http://msdn.microsoft.com/en-US/library/aa970069\(v=vs.100\).aspx) à l’aide de l’application : / / / autorité<br /><br /> -Une référence de ressource du composant absolu<br /><br /> : Un chemin d’accès à un fichier contenant une ressource native|  
|Présentation|[Facultatif] Indique quel type d’arrière-plan de que la source est destinée à être utilisée.<br /><br /> Il peut avoir l'une des valeurs suivantes :<br /><br /> - *Lumière*: la source peut être utilisée sur un arrière-plan clair.<br /><br /> - *Sombre*: la source peut être utilisée sur un arrière-plan sombre.<br /><br /> - *Contraste élevé*: la source peut être utilisée sur n’importe quel arrière-plan en mode contraste élevé.<br /><br /> - *HighContrastLight*: la source peut être utilisée sur un arrière-plan clair en mode de contraste élevé.<br /><br /> -*HighContrastDark*: la source peut être utilisée sur un arrière-plan sombre dans le mode de contraste élevé.<br /><br /> Si le **arrière-plan** attribut est omis, la source peut être utilisée sur n’importe quel arrière-plan.<br /><br /> Si **arrière-plan** est *Light*, *foncé*, *HighContrastLight*, ou *HighContrastDark*, couleurs de la source ne sont jamais inversés. Si **arrière-plan** est omis ou défini comme *contraste élevé*, l’inversion des couleurs de la source est contrôlée par l’image **AllowColorInversion** attribut.|  
  
 A \<Source > élément peut avoir un seul des sous-éléments facultatives suivantes :  
  
||||  
|-|-|-|  
|**Élément**|**Attributs (tous requis)**|**Définition**|  
|\<Taille >|Value|La source est utilisée pour les images de la taille donnée (en unités de l’appareil). L’image sera carrée.|  
|\<SizeRange >|MinSize, MaxSize|La source servira pour les images à partir de MinSize à MaxSize (en unités de périphérique) (inclus). L’image sera carrée.|  
|\<Dimensions >|Largeur, hauteur|La source est utilisée pour les images de donnée de largeur et hauteur (en unités de l’appareil).|  
|\<DimensionRange >|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|La source servira pour les images à partir de la largeur/hauteur minimale de la largeur/hauteur maximale (en unités de périphérique) (inclus).|  
  
 A \<Source > élément peut également avoir facultatif \<NativeResource > sous-élément qui définit un \<Source > qui est chargé à partir d’un assembly natif plutôt qu’un assembly managé.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**Attribut**|**Définition**|  
|Type|[Obligatoire] Le type de la ressource native, XAML ou PNG|  
|Id|[Obligatoire] La partie ID entier de la ressource native|  
  
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
|GUID|[Obligatoire] Le GUID du moniker d’image|  
|Id|[Obligatoire] La partie de l’ID du moniker d’image|  
|Ressource externe|[Facultatif, false de valeur par défaut] Indique si le moniker d’image fait référence à une image dans le manifeste actuel.|  
  
 Le moniker de l’image de relation contenant-contenu n’a pas à faire référence à une image définie dans le manifeste en cours. Si l’image de relation contenant-contenu est introuvable dans la bibliothèque d’images, une image d’espace réservé vide sera utilisée à la place.  
  
## <a name="how-to-use-the-tool"></a>Comment utiliser l’outil  
 **Validation d’un manifeste d’image personnalisée**  
  
 Pour créer un manifeste personnalisé, nous vous recommandons d’utiliser l’outil ManifestFromResources pour générer automatiquement le manifeste. Pour valider le manifeste personnalisé, lancer la visionneuse de bibliothèque d’images, puis sélectionnez Fichier > définir les chemins... pour ouvrir la boîte de dialogue répertoires de recherche. L’outil utilise les répertoires de recherche pour charger des manifestes d’images, mais il sera également l’utiliser pour rechercher les fichiers .dll qui contiennent les images dans un manifeste, veillez à inclure le manifeste et les répertoires de la DLL dans cette boîte de dialogue.  
  
 ![Recherche de visionneuse de bibliothèque d’images](../../extensibility/internals/media/image-library-viewer-search.png "recherche de visionneuse de bibliothèque d’images")  
  
 Cliquez sur **ajouter...**  pour sélectionner les nouveaux répertoires de recherche pour rechercher des manifestes et leurs DLL correspondant. L’outil enregistre ces répertoires de recherche, et ils peuvent être activés ou désactivés en cochant ou non un répertoire.  
  
 Par défaut, l’outil tente de trouver le répertoire d’installation de Visual Studio et ajoutez ces répertoires à la liste de répertoires de recherche. Vous pouvez ajouter manuellement les répertoires que ne trouve pas l’outil.  
  
 Une fois que tous les manifestes sont chargées, l’outil peut être utilisé pour activer/désactiver **arrière-plan** couleurs, **PPP**, **contraste élevé**, ou **grayscaling** pour les images afin qu’un utilisateur peut inspecter visuellement les ressources d’image pour vérifier qu’ils sont restituées correctement pour les différents paramètres.  
  
 ![Image d’arrière-plan de visionneuse de bibliothèque](../../extensibility/internals/media/image-library-viewer-background.png "de l’Image d’arrière-plan de visionneuse de bibliothèque")  
  
 La couleur d’arrière-plan peut être définie à une valeur personnalisée, sombre ou clair. En sélectionnant « Couleur personnalisée » pour ouvrir une boîte de dialogue de sélection de couleur et ajouter cette couleur personnalisée vers le bas de la zone de liste déroulante en arrière-plan pour réutiliser facilement ultérieurement.  
  
 ![Couleur personnalisée de visionneuse de bibliothèque d’images](../../extensibility/internals/media/image-library-viewer-custom-color.png "couleur personnalisée de visionneuse de bibliothèque d’images")  
  
 Moniker d’image affiche les informations pour chaque image réelle derrière ce moniker dans le volet de détails de l’Image de droite. Le volet permet également aux utilisateurs de copier un moniker par nom ou par la valeur de la paire GUID : ID brute.  
  
 ![Détails de l’Image Viewer bibliothèque d’images](../../extensibility/internals/media/image-library-viewer-image-details.png "détails de l’Image Viewer bibliothèque d’images")  
  
 Les informations affichées pour chaque source d’image inclut le type d’arrière-plan pour l’afficher, si elle peut être à thème ou prend en charge du contraste élevé, quelles sont les tailles valide ou s’il est indépendant de la taille et si l’image provient d’un assembly natif.  
  
 ![Visionneuse de bibliothèque d’images peut thème](../../extensibility/internals/media/image-library-viewer-can-theme.png "thème du cylindre visionneuse de bibliothèque d’images")  
  
 Lors de la validation d’un manifeste de l’image, nous vous recommandons de déployer le manifeste et l’image DLL dans leurs emplacements du monde réel. Cette commande vérifie que les chemins d’accès relatifs sont fonctionne correctement et que la bibliothèque d’images peut rechercher et charger le manifeste et l’image de DLL.  
  
 **Recherche de catalogue d’images KnownMonikers**  
  
 Pour mieux faire correspondre le style de Visual Studio, une extension Visual Studio peut utiliser des images dans le catalogue d’images Visual Studio, plutôt que la création et l’utilisation de son propre. Cela présente l’avantage de ne pas disposer de conserver ces images et garantit que l’image est une image de sauvegarde de la haute résolution afin qu’il doit se présenter correct dans tous les paramètres PPP qui prend en charge de Visual Studio.  
  
 La visionneuse de bibliothèque d’images permet un manifeste à rechercher afin qu’un utilisateur peut rechercher le moniker représentant un composant de l’image, utilisez ce nom dans le code. Pour rechercher des images, entrez le terme de recherche dans la zone de recherche et appuyez sur ENTRÉE. La barre d’état en bas affiche le nombre de correspondances ont été trouvé hors les images totales dans tous les manifestes.  
  
 ![Filtre de visionneuse de bibliothèque d’images](../../extensibility/internals/media/image-library-viewer-filter.png "filtre de visionneuse de bibliothèque d’images")  
  
 Lorsque vous recherchez des monikers d’image dans les manifestes existants, nous recommandons que vous recherchez et utilisez uniquement les monikers le Visual Studio Image du catalogue, autres monikers intentionnellement publiquement accessibles ou votre propre monikers personnalisés. Si vous utilisez des monikers non publics, interface utilisateur personnalisée est peut-être rompu ou ont ses images modifiées de façon inattendue si ou lorsque les monikers non publics et les images sont modifiés ou mis à jour.  
  
 En outre, il est possible de recherche par GUID. Ce type de recherche est utile pour filtrer la liste à un seul manifeste ou sous-section unique d’un manifeste si ce manifeste contient plusieurs GUID.  
  
 ![Filtre de visionneuse de bibliothèque GUID de l’image](../../extensibility/internals/media/image-library-viewer-filter-guid.png "filtre de visionneuse de bibliothèque GUID de l’Image")  
  
 Enfin, la recherche par ID est possible ainsi.  
  
 ![ID de filtre de visionneuse de bibliothèque de l’image](../../extensibility/internals/media/image-library-viewer-filter-id.png "ID de filtre de visionneuse de bibliothèque de l’Image")  
  
## <a name="notes"></a>Notes  
  
-   Par défaut, l’outil extraira dans plusieurs manifestes d’images présentes dans le répertoire d’installation de Visual Studio. La seule ayant des monikers publiquement consommables est la **Microsoft.VisualStudio.ImageCatalog** de manifeste. GUID : ae27a6b0-e345-4288-96df-5eaf394ee369 (faire **pas** remplacer ce GUID dans un manifeste personnalisé) Type : KnownMonikers  
  
-   L’outil tente de lancement pour charger tous les manifestes d’images qu’il trouve, il peut prendre plusieurs secondes pour l’application s’affiche réellement. Il peut également être lente ou ne répondent pas lors du chargement des manifestes.  
  
## <a name="sample-output"></a>Résultat de l'exemple  
 Cet outil ne génère pas de sortie.