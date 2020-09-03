---
title: Définir un élément de boîte à outils de modélisation personnalisé | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0a038150519ea7a40a52fb1be16ed93045c09eed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851517"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>Définir un élément de boîte à outils de modélisation personnalisé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour faciliter la création d'un élément ou d'un groupe d'éléments d'après un modèle que vous utilisez souvent, vous pouvez ajouter de nouveaux outils à la boîte à outils des diagrammes de modélisation dans Visual Studio. Vous pouvez distribuer ces éléments de boîte à outils à d'autres utilisateurs de Visual Studio.

 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Un outil personnalisé crée un ou plusieurs éléments dans un diagramme. Par exemple, vous pouvez créer un outil personnalisé pour créer des éléments tels que les suivants :

- un package lié au profil .NET et une classe avec le stéréotype .NET ;

- une paire de classes liées par une association pour représenter le modèle Observer.

> [!NOTE]
> Vous pouvez utiliser cette méthode pour créer des outils d'élément. Autrement dit, vous pouvez créer des outils que vous faites glisser de la boîte à outils vers un diagramme. Vous ne pouvez pas créer d'outils de connecteur.

## <a name="defining-a-custom-modeling-tool"></a><a name="DefineTool"></a> Définition d’un outil de modélisation personnalisé

#### <a name="to-define-a-custom-modeling-tool"></a>Pour définir un outil de modélisation personnalisé

1. Créez un diagramme UML qui contient un élément ou un groupe d'éléments.

    - Ces éléments peuvent avoir des relations entre eux et peuvent avoir des éléments auxiliaires tels que des ports, des attributs, des opérations ou des broches.

2. Enregistrez le diagramme en utilisant le nom que vous souhaitez donner au nouvel outil. Dans le menu **fichier** , cliquez sur **Enregistrer... Comme**.

3. À l'aide de l'Explorateur Windows, copiez les deux fichiers de diagrammes dans le dossier suivant ou dans n'importe quel sous-dossier :

     *YourDocuments* **\Visual Studio\Architecture Tools\Custom, éléments de boîte à outils**

    - Créez ce dossier s'il n'existe pas. Vous devrez peut-être créer les **Outils d’architecture** et les éléments de **boîte à outils personnalisés**.

    - Copiez les deux fichiers de diagramme, l’un avec un nom qui se termine par «... **diagramme**» et l’autre avec un nom qui se termine par «... **Diagram. Layout**»

    - Vous pouvez créer autant d'outils personnalisés que vous le souhaitez. Utilisez un diagramme pour chaque outil.

4. Facultatif Créez un fichier **. fichier tbxinfo** comme décrit dans [comment définir les propriétés des outils personnalisés](#tbxinfo), puis ajoutez-le au même répertoire. Cela vous permet de définir une icône de boîte à outils, une info-bulle, et ainsi de suite.

    - Un seul fichier **. fichier tbxinfo** peut être utilisé pour définir plusieurs outils. Il peut faire référence à des fichiers de diagrammes situés dans des sous-dossiers.

5. Démarrez Visual Studio. L'outil supplémentaire apparaît dans la boîte à outils du type de diagramme approprié.

### <a name="what-the-custom-tool-will-replicate"></a>Que réplique l'outil personnalisé ?
 Un outil personnalisé réplique la plupart des fonctionnalités du diagramme source :

- Noms. Quand un élément est créé à partir de la boîte à outils, un numéro est ajouté à la fin du nom si nécessaire pour éviter les noms en double dans le même espace de noms.

- Couleurs, tailles et formes.

- Stéréotypes et profils de packages.

- Valeurs de propriétés comme Is Abstract.

- Éléments de travail liés.

- Multiplicités et autres propriétés de relations.

- Positions relatives des formes.

  Les fonctionnalités suivantes ne sont pas conservées dans un outil personnalisé :

- Formes simples. Il s'agit des formes qui ne sont liées à aucun élément de modèle, que vous pouvez dessiner dans certains genres de diagrammes.

- Routage de connecteur. Si vous routez des connecteurs manuellement, le routage n'est pas préservé quand votre outil est utilisé. Les positions de certaines formes imbriquées, telles que les Ports, ne sont pas conservées par rapport à leurs propriétaires.

## <a name="how-to-define-the-properties-of-custom-tools"></a><a name="tbxinfo"></a> Comment définir les propriétés des outils personnalisés
 Un fichier d’informations de boîte à outils (**. fichier tbxinfo**) vous permet de spécifier un nom de boîte à outils, une icône, une info-bulle, une tabulation et un mot clé d’aide pour un ou plusieurs outils personnalisés. Donnez-lui un nom, tel que **mytools. fichier tbxinfo**.

 Ce fichier ressemble à ce qui suit :

```
<?xml version="1.0" encoding="utf-8" ?>
<customToolboxItems xmlns="http://schemas.microsoft.com/visualstudio/[version]/ArchitectureTools/CustomToolboxItems">
  <customToolboxItem fileName="MyObserverTool.classdiagram">
    <displayName>
       <value>Observer Pattern</value>
    </displayName>
    <tabName>
       <value>UML Class Diagram</value>
    </tabName>
    <image><bmp fileName="ObserverPatternIcon.bmp"/></image>
    <f1Keyword>
      <value>ObserverPatternHelp</value>
    </f1Keyword>
    <tooltip>
       <value>Create a pair of classes</value>
    </tooltip>
  </customToolboxItem>
</customToolboxItems>
```

 La valeur de chaque élément peut être :

- Comme indiqué dans l'exemple, `<bmp fileName="…"/>` pour l'icône de boîte à outils et `<value>string</value>` pour les autres éléments.

  \- ou -

- `<resource fileName="Resources.dll"`

   `baseName="Observer.resources" id="Observer.tabname" />`

   Dans ce cas, vous fournissez un assembly compilé dans lequel les valeurs de chaîne ont été compilées en tant que ressources.

  Ajoutez un nœud `<customToolboxItem>` pour chaque élément de boîte à outils que vous souhaitez définir.

  Les nœuds du fichier **. fichier tbxinfo** sont les suivants. Il existe une valeur par défaut pour chaque nœud.

|Nom du nœud|Définit|
|---------------|-------------|
|displayName|Le nom de l'élément de boîte à outils.|
|tabName|L'onglet de boîte à outils sous lequel l'élément doit apparaître. Vous pouvez spécifier le nom de l'onglet normal pour ce type de diagramme ou un nom distinct.|
|image|Emplacement du fichier bitmap (**. bmp**), qui doit avoir une hauteur et une largeur de 16, et une profondeur de couleur de 24 bits.|
|f1Keyword|Le mot clé qui localise une rubrique d'aide.|
|tooltip|Une info-bulle pour cet outil.|

 Vous pouvez modifier le fichier bitmap dans Visual Studio et affecter la valeur 16 à sa hauteur et sa largeur dans la fenêtre Propriétés.

> [!NOTE]
> Si vous commencez à utiliser un fichier .tbxinfo après avoir utilisé des fichiers de diagrammes seuls, vous constaterez peut-être que la boîte à outils contient à la fois les anciennes et les nouvelles versions d'un élément de boîte à outils. Cela peut également se produire si le nom du fichier de diagramme a été tapé incorrectement dans le fichier .tbxinfo. Si cela se produit, dans le menu contextuel de la boîte à outils, choisissez **Réinitialiser la boîte à outils**. Les éléments de boîte à outils personnalisés disparaîtront. Redémarrez Visual Studio et les éléments personnalisés corrects apparaîtront.

## <a name="how-to-distribute-toolbox-items-in-a-visual-studio-extension"></a><a name="Extension"></a> Comment distribuer des éléments de boîte à outils dans une extension Visual Studio
 Vous pouvez distribuer des éléments de boîte à outils à d’autres [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] utilisateurs en les empaquetant dans une extension Visual Studio (VSIX). Vous pouvez empaqueter des commandes, des profils et d'autres extensions dans le même fichier VSIX. Pour plus d’informations, consultez [déploiement d’extensions Visual Studio](https://msdn.microsoft.com/library/dd393694(VS.100).aspx).

 L'approche habituelle pour créer une extension Visual Studio consiste à utiliser le modèle de projet VSIX. Pour ce faire, vous devez avoir installé [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].

#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>Pour ajouter un élément de boîte à outils à une extension Visual Studio

1. [Créez et testez un ou plusieurs outils personnalisés](#DefineTool).

2. [Créez un fichier. fichier tbxinfo](#tbxinfo) qui référence les outils.

3. Ouvrez un projet d'extension Visual Studio existant.

     \- ou -

     Définissez un nouveau projet d'extension Visual Studio.

    1. Dans le menu **Fichier**, sélectionnez **Nouveau**, **Projet**.

    2. Dans la boîte de dialogue **nouveau projet** , sous **modèles installés**, choisissez **Visual C#**, **extensibilité**, **projet VSIX**.

4. Ajoutez vos définitions de boîte à outils au projet. Incluez le fichier **. fichier tbxinfo** , les fichiers de diagramme, les fichiers bitmap et les fichiers de ressources, et assurez-vous qu’ils sont inclus dans le VSIX.

    - Dans Explorateur de solutions, dans le menu contextuel du projet VSIX, choisissez **Ajouter**, **élément existant**. Dans la boîte de dialogue, définissez **les objets de type : tous les fichiers**. Recherchez les fichiers, sélectionnez-les tous, puis choisissez **Ajouter**.

        > [!NOTE]
        > Dans ce projet, vous ne pouvez pas ouvrir les fichiers de diagrammes dans l'éditeur de modèle.

5. Définissez les propriétés suivantes de tous les fichiers que vous venez d'ajouter. Vous pouvez définir leurs propriétés en même temps en les sélectionnant dans l'Explorateur de solutions. Veillez à ne pas modifier les propriétés des autres fichiers dans le projet.

     **Copier dans le répertoire**  =  de sortie **Toujours copier**

     **Action de génération** = **Contenu**

     **Inclure dans VSIX**  =  **true**

6. Ouvrez **source.extension.vsixmanifest**. Le fichier s'ouvre dans l'éditeur de manifeste d'extension.

7. Sous **métadonnées**, ajoutez une description pour les outils personnalisés.

     Sous **ressources**, choisissez **nouveau** , puis définissez les champs dans la boîte de dialogue comme suit :

    - **Type**  =  **Type d’extension personnalisé**

    - Type = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`

        > [!NOTE]
        > Cette option ne figure pas dans la liste déroulante. Vous devez l'entrer à l'aide du clavier.

    - **Source**  =  **Fichier sur FileSystem**.

    - **Path** = votre fichier **. fichier tbxinfo** , par exemple **mytools. fichier tbxinfo**

8. Créez le projet.

9. **Pour vérifier que l’extension fonctionne**, appuyez sur F5. L'instance expérimentale de Visual Studio démarre.

     Dans l'instance expérimentale, créez ou ouvrez un diagramme UML du type approprié. Vérifiez que votre nouvel outil apparaît dans la boîte à outils et qu'il crée les éléments correctement.

10. Pour **obtenir un fichier VSIX en vue du déploiement :** Dans l’Explorateur Windows, ouvrez le dossier **.\bin\debug** ou **.\bin\release** pour rechercher le fichier **. vsix** . Il s'agit d'un fichier d'Extension [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Vous pouvez l'installer sur votre ordinateur et l'envoyer à d'autres utilisateurs de Visual Studio.

#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>Pour installer des outils personnalisés à partir d'une Extension Visual Studio

1. Ouvrez le fichier `.vsix` dans l'Explorateur Windows ou dans Visual Studio.

2. Choisissez **installer** dans la boîte de dialogue qui s’affiche.

3. Pour désinstaller ou désactiver temporairement l’extension, ouvrez **extensions et mises à jour** dans le menu **Outils** .

## <a name="localization"></a>Localisation
 Vous pouvez créer une extension qui, une fois installée sur un autre ordinateur, affiche les noms d'outils et les info-bulles dans la langue de l'ordinateur cible.

#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>Pour fournir des versions de l'outil dans plusieurs langues

1. Créez un projet d'Extension Visual Studio qui contient un ou plusieurs outils personnalisés.

    Dans le fichier **. fichier tbxinfo** , utilisez la méthode de fichier de ressources pour définir les `displayName` Outils, la boîte à outils `tabName` et l’info-bulle. Créez un fichier de ressources dans lequel ces chaînes sont définies, compilez-le dans un assembly et faites-y référence à partir du fichier tbxinfo.

2. Créez des assemblys supplémentaires qui contiennent des fichiers de ressources avec des chaînes dans d'autres langues.

3. Placez chaque assembly supplémentaire dans un dossier dont le nom est le code de culture de la langue. Par exemple, placez une version française de l’assembly dans un dossier nommé **fr**.

4. Vous devez utiliser un code de culture neutre, en général deux lettres, et non une culture spécifique telle que `fr-CA`. Pour plus d’informations sur les codes de culture, consultez [CultureInfo. GetCultures, méthode](https://msdn.microsoft.com/library/system.globalization.cultureinfo.getcultures(VS.100).aspx), qui fournit une liste complète des codes de culture.

5. Générez l'Extension Visual Studio et distribuez-la.

6. Une fois l'extension installée sur un autre ordinateur, la version du fichier de ressources pour la culture locale de l'utilisateur sera chargée automatiquement. Si vous n'avez pas fourni de version pour la culture de l'utilisateur, les ressources par défaut sont utilisées.

   Vous ne pouvez pas appliquer cette méthode pour installer différentes versions du diagramme de prototype. Les noms des éléments et des connecteurs seront identiques dans chaque installation.

## <a name="other-toolbox-operations"></a>Autres opérations de boîte à outils
 En règle générale, dans [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] vous pouvez personnaliser la boîte à outils en renommant les outils, en les déplaçant vers différents onglets de la boîte à outils et en les supprimant. Toutefois, ces modifications ne sont pas conservées pour les outils de modélisation personnalisés créés avec les procédures décrites dans cette rubrique. Quand vous redémarrez [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], les outils personnalisés réapparaissent avec leurs noms et leurs emplacements dans la boîte à outils définis.

 En outre, vos outils personnalisés disparaissent si vous exécutez la commande **Réinitialiser la boîte à outils** . Cependant, ils réapparaissent quand vous redémarrez [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

## <a name="see-also"></a>Voir aussi
 [Étendre des modèles et des diagrammes UML](../modeling/extend-uml-models-and-diagrams.md) [définir un profil pour étendre UML](../modeling/define-a-profile-to-extend-uml.md) [définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [définir des contraintes de validation pour les modèles UML](../modeling/define-validation-constraints-for-uml-models.md)
