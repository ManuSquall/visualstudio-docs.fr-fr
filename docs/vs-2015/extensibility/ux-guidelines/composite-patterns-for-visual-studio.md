---
title: Modèles composites
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 196fc4bddba0cfa6addb786148cd3876e1ec8260
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430006"
---
# <a name="composite-patterns-for-visual-studio"></a>Modèles composites pour Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Modèles composites combinent des éléments de conception et d’interaction dans des configurations distinctes. Les modèles composites plus importantes dans Visual Studio en matière de cohérence sont les suivantes :

- [Visualisation des données](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [L’interface utilisateur sur l’objet et la lecture](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Modèles de sélection](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Persistance et l’enregistrement des paramètres](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Entrée tactile](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="BKMK_DataVisualization"></a> Visualisation des données

### <a name="overview"></a>Vue d'ensemble
 Les graphiques sont un moyen visuel pour agréger et de visualiser des données pour améliorer la prise de décision. Ils peuvent aider les utilisateurs confrontés à un grand nombre de données, mais ce qui signifie peu de voir ce qui mérite une attention et ce qui est peut-être une action.

 L’utilisateur bénéficieront d’un graphique si une des conditions suivantes est vraie :

- Le graphique aidera les utilisateurs identifier les tâches qu’ils peuvent agir sur ?

- Le graphique permettent aux utilisateurs afin de prévoir les conséquences des modifications potentielles ?

- Est le graphique aider les utilisateurs à découvrir des tendances et identifier des modèles ?

- Le graphique permettra aux utilisateurs de prendre de meilleures décisions ?

- Le graphique aidera à répondre à une question spécifique que les utilisateurs devront peut-être dans le contexte donné ?

#### <a name="general-rules-for-charts"></a>Règles générales pour les graphiques

- Clairement les données d’étiquette. Illustrations sans aucune explication servent simplement de belles images.

- Démarrer les axes à zéro pour éviter les proportions d’inclinaison. Taille de ligne de longueur et de la barre de sont des signaux visuels importants pour comprendre les relations entre les points de données.

- Créer des graphiques, infographies pas. Infographies sont artistiques représentations des données, et leur objectif principal est de leur interprétation visual. Graphiques peuvent (et doivent) être visuellement attrayante, mais laisser les données parler d’elles-mêmes.

- Évitez skeumorphism, graphiques à barres illustrées, signes dièse contraste et autres fonctions tactiles infographie.

- N’utilisez pas d’effets 3D en tant qu’élément décoratif. Utilisez-les uniquement si elles véritablement partie intégrante de la capacité de l’utilisateur à comprendre les informations.

- Évitez d’utiliser plusieurs lignes et des remplissages, comme de plus de deux couleurs peuvent rendre ce type de graphique difficile à lire et interpréter correctement.

- N’utilisez pas d’un graphique (ou n’importe quel illustration) sont les seuls moyens de comprendre un concept ou l’interaction avec les données. Cela pose des difficultés pour les utilisateurs ayant des troubles visuels.

- N’utilisez pas les graphiques en tant qu’éléments superflues ou décoratifs sur une page. En d’autres termes, si un graphique n’ajoute pas que tous les utilisateurs valeur ou aide résoudre un problème, n’utilisez pas cela.

### <a name="chart-types"></a>Types de graphiques
 Types de graphiques utilisées dans Visual Studio incluent des graphiques à barres, graphiques en courbes, un graphique à secteurs modifié appelé graphique en anneau ou « graphique en anneau, « chronologies, à nuages de points tracés (également appelés « graphiques du cluster ») et des diagrammes de Gantt. Chaque type de graphique est utile pour la communication d’un autre type d’informations.

### <a name="other-charting-considerations"></a>Autres considérations relatives à la création de graphiques

#### <a name="color"></a>Color
 Il existe une palette spécifique de la création de graphiques couleurs sont définies pour une utilisation dans Visual Studio. La palette est accessible pour les principaux types de daltonisme, et les couleurs peuvent être différenciés même lorsque utilisés comme des secteurs très étroits de couleur. Vous pouvez utiliser ces couleurs dans n’importe quelle combinaison de tout type de graphique dans votre interface utilisateur. Vous n’avez pas besoin d’utiliser toutes les couleurs de sept si vous n’avez pas besoin que de nombreuses couleurs distinctes. Ces couleurs n’ont pas été conçues pour être utilisé avec des éléments de premier plan, donc vous ne placez ne pas de texte ou des glyphes sur ces couleurs. Ces teintes doivent être codé en dur et exposés à la personnalisation de l’utilisateur sous **Outils > Options** (consultez [exposant des couleurs pour les utilisateurs finaux](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).

|Échantillon|hex|RVB|
|------------|---------|---------|
|![Swatch 71B252](../../extensibility/ux-guidelines/media/0711-71b252.png "0711_71B252")|#71B252|113,178,82|
|![Échantillon BF3F00](../../extensibility/ux-guidelines/media/0711-bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|
|![Échantillon FCB714](../../extensibility/ux-guidelines/media/0711-fcb714.png "0711_FCB714")|#FCB714|252,183,20|
|![Swatch 903F8B](../../extensibility/ux-guidelines/media/0711-903f8b.png "0711_903F8B")|#903F8B|144,63,139|
|![Échantillon 117AD1](../../extensibility/ux-guidelines/media/0711-117ad1.png "0711_117AD1")|#117AD1|17,122,209|
|![Swatch 79D7F2](../../extensibility/ux-guidelines/media/0711-79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|
|![Swatch B5B5B5](../../extensibility/ux-guidelines/media/0711-b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|

## <a name="BKMK_OnObjectUI"></a> L’interface utilisateur sur l’objet et la lecture
 Cette section donne le contexte pour la lecture, également appelé code aperçu, un type de l’interface utilisateur de sur les objets unique à Visual Studio.

### <a name="overview"></a>Vue d'ensemble

- L’interface utilisateur sur l’objet doit donner à l’utilisateur plus d’informations ou l’interactivité sans se départir de leur tâche principale.

- Le modèle principal pour l’interface utilisateur sur les objets dans Visual Studio est appelé « information au moment de l’attention ».

- L’interface utilisateur sur l’objet dans Visual Studio est soit inline ou flottante et durable ou temporaire.

  - Aperçu de code, un type d’interface utilisateur sur les objets dans Visual Studio, est inline et durable.

  - CodeLens, un type d’interface utilisateur sur les objets dans Visual Studio, est temporaire et flottants

  Comprendre le fonctionne d’un morceau de code, ou rechercher des informations sur ce code, nécessite souvent un développeur changer de contexte et d’accéder à tout autre contenu ou d’une autre fenêtre. Ces équipes de contexte peuvent être gênante, car les utilisateurs peuvent perdre le focus sur leurs tâches d’origine, s’ils quittent leur fenêtre principale. En outre, bien que back de contexte d’origine peut être difficile, surtout si le basculement de windows a provoqué leur code d’origine pour être masquée par toute autre interface utilisateur.

  L’interface utilisateur sur l’objet suit un modèle appelé « information au moment de l’attention ». Ces messages, les fenêtres publicitaires et les boîtes de dialogue donnent aux utilisateurs des informations supplémentaires pertinentes qui ajoute une clarification ou l’interactivité sans perdre le focus sur leur tâche principale. Exemples de l’interface utilisateur sur les objets incluent les fenêtres publicitaires qui s’affichent lorsqu’un utilisateur pointe le pointeur sur une icône dans la zone de notification, la ligne ondulée rouge sous un mot mal orthographié et la vue Aperçu introduite dans Visual Studio 2013.

### <a name="decision-points"></a>Points de décision
 Dans Visual Studio, il existe plusieurs façons d’utiliser ce modèle d’informations au moment de l’attention. En choisissant le mécanisme de droite et de mettre en œuvre de manière cohérente et prévisible sont essentielle pour l’expérience globale. Sinon, les utilisateurs peuvent s’afficher une expérience à confusion ou incohérente qui porte atteinte le focus à partir du contenu lui-même.

#### <a name="relationships-between-master-and-detail-content"></a>Relations entre un maître et détail contenu
 Pour plus d’informations au moment de l’attention sont utilisés pour afficher une relation entre le contenu que l’utilisateur ayant le focus sur (le contenu « maître ») et d’autres concerne le contenu (le contenu de « détail »). Dans ce modèle, le contenu de détail est indéniablement lié au contenu de l’utilisateur travaille avec et peut être affichée près du contenu principal. Obtenir des informations supplémentaires ou des informations qui ne peut pas être synthétisées sans pour autant submerger le contenu principal doivent suivre un autre modèle, telle qu’une fenêtre outil.

- **Toujours** afficher le contenu de détail à proximité du contenu principal.

- **Toujours** Assurez-vous que le contenu de détail permet toujours d’un utilisateur de rester concentré sur le contenu principal. Souvent, la meilleure façon d’y parvenir consiste à afficher le contenu de détail comme proche le contenu principal que possible. Cela est possible par le rendu du contenu en détail dans une fenêtre contextuelle en regard du contenu principal, ou en rendant le contenu de détail inclus sous le contenu principal.

- **Jamais** utiliser des informations au moment de l’attention qui dirige l’utilisateur en dehors du contenu principal. Si les utilisateurs doivent afficher le contenu de détail séparément, exposer une action explicite qui permet à l’utilisateur pour ce faire.

#### <a name="design-details"></a>Détails de la conception
 Une fois que vous avez déterminé que l’interface utilisateur sur l’objet est le bon choix, il existe quatre considérations de conception principale :

1. **Persistance :** le contenu doit être durable ou temporaire ?
   Les utilisateurs souhaiteront conserver les informations visibles pour faire référence à ou interagir avec ? Ou les utilisateurs souhaiteront aperçu rapidement les informations et poursuivez leur tâche principale ?

2. **Type de contenu :** le contenu sera d’information, exploitables ou navigation ?
   L’utilisateur a-t-il besoin des détails supplémentaires sur le contenu principal ? L’utilisateur n’a besoin pour effectuer une tâche qui affecte le contenu principal ? Ou l’utilisateur doit-il être dirigé vers une autre ressource ?

3. **Type d’indicateur :** n’a un indicateur ambiant sens ?
   Les informations résumées de manière utile et l’affichage se sans pour autant submerger le contenu principal ?

4. **Mouvements :** les mouvements sera utilisé pour appeler et ignorer l’interface utilisateur ?
   Comment l’utilisateur affiche le contenu de détail et envoyez-la par la suite ? Existe-t-il des valeur lors de l’ajout d’un mouvement telles que l’épinglage pour basculer entre les états temporaires et durables ?

   Chacun de ces points de quatre décision aura un impact sur les principaux composants de l’interface utilisateur sur les objets.

### <a name="on-object-ui-components"></a>Composants d’interface utilisateur sur l’objet

1. Type de conteneur (présentateur de contenu)

    - Virgule flottante

    - Inline

2. Type de contenu

    - Information : données qui peuvent être statique ou dynamique

    - Exploitables : commandes qui modifient le contenu principal

    - Navigation : des liens qui dirige l’utilisateur vers une autre fenêtre ou une application, telles que MSDN

3. Mouvements

    - Invocation

    - Licenciement

    - L’épinglage

    - Autres interactions

4. Modèle de persistance et de validation

    - Transient

    - Durable

    - Automatique

    - À la demande

5. Indicateurs ambiantes (facultatifs)

    - Soulignement de trait de soulignement ondulé

    - Icône de balise active

    - Autres indicateurs ambiantes

#### <a name="container-content-presenter-type"></a>Type de conteneur (présentateur de contenu)
 Il existe deux principales options sont disponibles pour présenter le contenu au moment de l’attention :

1. **Inline :** un présentateur inline, telles que la vue Aperçu qui a été introduit dans l’éditeur de Code Visual Studio 2013, rend l’espace pour le nouveau contenu par le passage du contenu existant.

    - **Préférez** présentateurs inline si vous pensez que les utilisateurs souhaitent passent beaucoup de temps faisant référence à ou interagir avec le contenu que vous présentez.

    - **Éviter** présentateurs inline si vous prévoyez que les utilisateurs souhaiteront coup les informations vous présenterez, puis poursuivez sa tâche principale avec une interruption minimale.

2. **Flottant :** présentateur flottante est positionné plus près le contenu sélectionné que possible, mais ne modifie pas la disposition du contenu existant. Différentes stratégies peuvent être employées, telles que l’affichage d’un panneau flottant contenu sur le plus proche de l’espace blanc disponible au symbole sélectionné.

    - **Préférez** flottante présentateurs si vous prévoyez que les utilisateurs souhaiteront coup les informations vous présenterez, puis poursuivez sa tâche principale avec une interruption minimale.

    - **Éviter** flottante présentateurs si vous prévoyez que les utilisateurs souhaiteront passent beaucoup de temps faisant référence à ou interagir avec le contenu vous présente.

#### <a name="content-type"></a>Type de contenu
 Il existe trois principaux types de contenu qui peut être affiché à l’intérieur de n’importe quel conteneur de l’interface utilisateur sur l’objet. N’importe quelle combinaison de ces types d’informations peut être affichée. Les trois types sont :

1. **Information :** la plupart des objets conteneurs de l’interface utilisateur affiche un type de contenu d’information. Le contenu peut représenter des informations sur l’état actuel de l’environnement, ou il peut représenter des informations sur un état futur potentiel de l’environnement. Par exemple, il peut être utilisé pour montrer l’effet d’une commande particulière, par exemple une refactorisation sur le code existant.

    - **Toujours** utiliser la représentation canonique des informations que vous affichez. Par exemple, le code doit se présenter comme le code, avec la coloration syntaxique et doit respecter des polices et autres paramètres de que l’utilisateur a défini l’environnement.

    - **Toujours** prendre en compte la prise en charge de toutes les actions sur le contenu d’information qui serait possible si ces mêmes informations sont présentées en tant que contenu principal. Par exemple, si présentant le code existant à l’intérieur d’un conteneur de l’interface utilisateur sur l’objet, étudiez la possibilité de parcourir et modifier ce code de prise en charge.

    - **Toujours** envisager d’utiliser une couleur d’arrière-plan différente si la présentation du contenu d’information qui représente un état futur potentiel.

2. Exploitables : certains conteneurs de l’interface utilisateur sur l’objet fournit la possibilité d’effectuer une action sur le contenu principal, tels que l’exécution d’une opération de refactorisation.

    - **Toujours** positionner actionnables commandes séparément à partir du contenu d’information.

    - **Toujours** activer et désactiver les actions lorsque cela est approprié.

    - **Toujours** reportez-vous aux instructions standards pour représenter des commandes à l’intérieur des boîtes de dialogue.

    - **Toujours** conserver le nombre d’actions qui sont exposées dans un conteneur de l’interface utilisateur sur l’objet au strict minimum. Interaction avec l’interface utilisateur l’objet doit être une expérience léger et rapide. L’utilisateur ne doit pas avoir à étendre l’énergie sur la gestion du conteneur de l’interface utilisateur sur l’objet lui-même.

    - **Toujours** envisager comment et quand un conteneur de l’interface utilisateur sur l’objet sera fermé ou fermé. Comme meilleure pratique, toute action qui s’achève la boîte de dialogue entre maître et détail contenu doit également fermer le conteneur de l’interface utilisateur sur l’objet lorsque cette action est appelée.

3. **Navigation :** certains sur les objets conteneurs de l’interface utilisateur incluent des liens qui dirige l’utilisateur vers une autre fenêtre ou une application, telles que l’ouverture d’un article MSDN dans le navigateur web de l’utilisateur.

    - **Toujours** ajouter n’importe quel lien de navigation avec « Ouvrir » afin que les utilisateurs ne seront pas surpris de voir à certains autres contenu cible de navigation.

    - **Toujours** séparer des liens de navigation à partir des liens exploitables.

#### <a name="ambient-indicators-optional"></a>Indicateurs ambiantes (facultatifs)
 Indicateurs ambiantes peuvent être subtiles, y compris le texte présenté dans une couleur de contraste du reste du code, ou évident, y compris les symboles installer tels que des traits de soulignement ondulée et icônes de balise active. Indicateurs ambiantes communiquent la disponibilité des informations complémentaires utiles. Dans l’idéal, ils fournissent des informations utiles même sans que l’utilisateur d’interagir avec elles.

- **Toujours** positionner un indicateur ambiant afin qu’il ne vous détournera pas ni ne submerger l’utilisateur. S’il est impossible positionner un indicateur ambiant de manière, envisagez une autre solution.

- **Toujours** positionner l’indicateur ambiante aussi proche que possible pour le contenu qui lui sont associés.

- **Toujours** essaie de créer un indicateur qui résume les informations disponible. Si possible, donnez un décompte du nombre d’éléments de données disponibles (par exemple, « 3 références » au lieu de simplement « références ») ou considérer une autre façon pour synthétiser les données.

    - Dans les cas où les données d’un indicateur ne peut pas toujours être calculées et affichées, immédiatement si possible, donnez des commentaires progressif comme les valeurs sont calculées. Par exemple, considérez animer des modifications qui reflètent les mises à jour les données disponibles, similaires à la façon dont la vignette dynamique de la messagerie sur Windows Phone actualise en tant que le nombre d’e-mails non lus augmente.

- **Jamais** ajouter des indicateurs de plus qu’un utilisateur peut raisonnablement pour un élément de contenu donné. Indicateurs ambiants doivent être utiles sans nécessiter d’intervention de l’utilisateur. Les indicateurs de perdent leur ambiance s’ils ont besoin de dépassement de capacité et d’autres contrôles de gestion pour les afficher dans la vue.

#### <a name="gestures"></a>Mouvements
 Un aspect clé de l’autorisation de l’utilisateur conserver le focus sur le contenu principal est en prenant en charge les mouvements de droite pour ouvrir et fermer le contenu des détails supplémentaires.

- **Toujours** oblige l’utilisateur à effectuer des mouvements explicite pour ouvrir le contenu supplémentaire. Mouvements open courantes sont les suivantes :

    - **Pointage :** info-bulles ou le contenu d’information non interactif

    - **Commande explicite :** inline présentateur

    - **Double-cliquez sur l’indicateur ambiante :** Fenêtre contextuelle CodeLens

- **Toujours** ignorer le contenu en détail chaque fois que l’utilisateur appuie sur la touche ÉCHAP.

- **Toujours** prendre en compte le contexte de l’interface utilisateur sur l’objet. Pour les présentateurs de contenu qui permettent l’interaction dans le conteneur, étudiez attentivement le s’il faut afficher des informations supplémentaires quand vous placez, qui est susceptible de perturber la lecture de flux de travail de l’utilisateur.

- **Jamais** affiche le contenu sur pointage qui semble être modifiable ou invite l’intervention de l’utilisateur. Ce comportement peut frustrer les utilisateurs s’ils essaient déplacer le curseur sur le contenu de détail, comme le comportement standard pour une info-bulle doit immédiatement faire disparaître lorsque le curseur n’est plus sur le contrôleur de contenu qui l’a produit.

## <a name="BKMK_SelectionModels"></a> Modèles de sélection

### <a name="overview"></a>Vue d'ensemble
 Un modèle de sélection est le mécanisme utilisé pour indiquer et confirmer les opérations sur un ou plusieurs objets d’intérêt dans l’interface utilisateur. Cette rubrique traite des modèles d’interaction de sélection dans les éditeurs de document de Visual Studio : éditeurs de texte, les aires de conception et les surfaces de modélisation.

 Les utilisateurs doivent disposer d’un moyen d’indiquer à Visual Studio qu’ils travaillent, et Visual Studio doit répondre de manière prévisible avec des commentaires aux utilisateurs concernant les qu’elle s’exécute sur. Différences ou un problèmes de communication entre l’utilisateur et l’interface utilisateur peut entraîner l’utilisateur ne pas remarquer une action, ce qui peut avoir des conséquences inattendues. Souvent, l’erreur passe inaperçue jusqu'à ce que l’utilisateur voit que quelque chose est manquante ou a changé. Modèles de sélection sont par conséquent un des éléments les plus critiques de la conception de l’interface utilisateur. Bien que les modèles de sélection dans Visual Studio sont cohérents avec Windows, il existe de légères variations.

 Dans Visual Studio, comme dans Windows, les modèles de sélection diffèrent en fonction du contexte dans lequel l’interaction se produit. Sélections peuvent se produire dans les quatre types d’objets :

- Texte

- Objets graphiques

- Listes et les arbres

- Grilles

  Au sein de ces objets, il existe trois types de sélections :

- Contigus

- Disjoint

- Région

#### <a name="scope"></a>Portée
 Le composant le plus important de sélection est de s’assurer que l’utilisateur sait fenêtre dans laquelle ils travaillent (activation) et où le focus est située (sélection). Visual Studio étend les fonctionnalités de gestion de fenêtre dans Windows, mais le schéma d’activation est la même : interaction avec une fenêtre place le focus dans la fenêtre. Visual Studio a deux indicateurs pour l’activation : un pour les fenêtres de document et un pour les fenêtres Outil.

 Pour les fenêtres de document, la fenêtre active est indiquée par un onglet de fenêtre de document sera disponible au premier plan et en modifiant sa couleur d’arrière-plan :

 ![Sélection de l’onglet actif dans Visual Studio](../../extensibility/ux-guidelines/media/0713-01-activetab.png "0713-01_ActiveTab")

 **Sélection de l’onglet actif**

 Pour les fenêtres Outil, la fenêtre active est indiquée par une modification de la couleur de la zone de barre de titre de la fenêtre d’outil :

 ![Sélection de la fenêtre Outil active dans Visual Studio](../../extensibility/ux-guidelines/media/0713-02-activetoolwindow.png "0713-02_ActiveToolWindow")

 **Affiche la sélection principale d’un nœud de la fenêtre outil Active**

 ![Sélection de la fenêtre outil inactive dans Visual Studio](../../extensibility/ux-guidelines/media/0713-03-inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Fenêtre outil inactive, montrant latente sélection du nœud**

 Une fois qu’une fenêtre est active, son focus est indiqué en fonction des modèles de sélection décrites dans cette section des instructions.

#### <a name="context"></a>Contexte
 Visual Studio a été conçu pour conserver un fort concept de contexte, le suivi du où l’utilisateur travaille. Qu’une seule fenêtre est active, qu’il s’agisse d’une fenêtre outil ou le document. Toutefois, la fenêtre de document au premier plan conserve toujours une sélection latente. Bien que le focus dans une fenêtre outil, la fenêtre de document qui était actif affiche une sélection, même dans un état inactif. Cela vise à conserver le contexte de l’utilisateur dans le document, qu'ils ont été modifiant, en leur montrant que Visual Studio a conservé son état afin qu’ils peuvent retourner et déplacer en toute transparence entre les fenêtres Outil et fenêtres de document.

### <a name="text-selection"></a>Sélection de texte
 Les éditeurs de Visual Studio qui sont strictement textuelles, tels que l’éditeur de texte intégré, utilisent le même modèle de sélection de texte et l’apparence décrit dans le [la souris et des pointeurs](https://msdn.microsoft.com/library/dn742466.aspx) page de Windows User Experience Interaction Guidelines sur MSDN. Le focus d’entrée dans l’éditeur de texte est indiqué par une barre verticale, appelée le point d’insertion. Le point d’insertion est un pixel unique épais et coloré en tant que l’inverse de l’élément qui apparaît derrière lui. Fait clignoter en fonction de la fréquence définie par le **clignotement du curseur** définition dans le **vitesse** onglet de la **clavier** applet dans le panneau de configuration.

#### <a name="contiguous-and-disjoint-selection"></a>Sélection contiguë et disjoint
 Sélection dans l’éditeur de texte est contigue uniquement. De texte disjointes sélections ne sont pas autorisées, mais doivent être traitées dans les éditeurs de l’objet graphique. Lorsque le pointeur de la souris se trouve sur une zone de texte, le curseur se transforme en un pointeur en i. Un seul clic place le point d’insertion dans l’éditeur de texte à l’emplacement du clic. Le bouton de la souris enfoncé démarre une mise en surbrillance de sélection et relâchez le bouton de la souris termine la surbrillance de sélection.

#### <a name="region-selection-box-selection"></a>Sélection de la région (sélection de zone)
 Visual Studio prend en charge les sélections de la région dans l’éditeur de texte, et il s’agit de sélection de zone. Sélection de zone permet à l’utilisateur à sélectionner une zone de texte qui ne respecte pas le flux de texte standard. Comme avec la sélection de texte standard, la sélection doit être contiguë. Sélection de zone est lancée en maintenant enfoncée la touche Alt tout en faisant glisser avec la souris. Sélection de zone peut également être lancée en appuyant sur les touches Alt et MAJ tout en utilisant les touches de direction pour indiquer la région de sélection. Sélection de zone utilise la mise en surbrillance de sélection normale et affiche le curseur de point d’insertion clignote à la fin de la zone de sélection.

 ![Régional &#40;boîte&#41; sélection dans Visual Studio](../../extensibility/ux-guidelines/media/0713-04-boxselection.png "0713-04_BoxSelection")

 **Sélection de zone (zone) dans Visual Studio**

#### <a name="text-selection-appearance"></a>Apparence de sélection de texte
 Les couleurs utilisées pour la sélection active et inactive dans l’éditeur peuvent être personnalisés. Pour personnaliser l’apparence visuelle de l’éditeur, un utilisateur peut atteindre **Outils > Options**, puis regardez sous **environnement > polices et couleurs > Éditeur de texte**.

### <a name="graphical-selection"></a>Sélection de graphique

#### <a name="interaction"></a>Interaction
 Sélection d’un objet graphique peut être complexe et dépend de plusieurs facteurs :

- **Modèle de sélection principale de l’éditeur.** Les éditeurs qui contiennent des objets graphiques peuvent également servir à modifier du texte ou des grilles. Par exemple, l’éditeur peut être un éditeur de texte qui prend également en charge le positionnement des objets graphiques, tels que le concepteur Visual Studio XAML. Prenant en charge plusieurs types d’objets peut affecter la façon dont l’utilisateur sélectionne les groupes constitués de différents types d’objets.

- **Prise en charge des États de sélection principaux et secondaires.** Un éditeur peut fournir de sélection principale et secondaire, États de sorte que les objets peuvent être modifiés de concert, alignés avec d’autres, redimensionné entre eux, et ainsi de suite.

- **Prise en charge Édition sur place.** Éditeurs permettent également le contenu de leurs objets de graphiques à modifier. Par exemple, une forme rectangle peut contenir également de texte à l’intérieur qui peut être modifiée par l’utilisateur. En outre, ce texte peut être centré ou justifié. Modification sur place implique un niveau plus détaillé d’interaction utilisateur et par conséquent requiert un ensemble approprié de signaux visuels pour présenter des informations d’état à l’utilisateur.

#### <a name="mouse-interaction"></a>Interaction souris

|Entrée|Résultat|
|-----------|------------|
|Cliquez sur un objet non sélectionné|Sélectionne l’objet et affiche une ligne en pointillés et les handles de sélection, si l’objet est redimensionnable.|
|Cliquez sur un objet sélectionné|Active la modification sur place si l’objet prend en charge. Cliquez en dehors de l’objet désactive le mode d’édition sur place.|
|Double-cliquez sur un objet|Ouvre le code-behind de l’objet pour le modifier et peut insérer un gestionnaire d’événements par défaut, le cas échéant.|
|Pointe vers un objet|Remplace le pointeur par le curseur de déplacement. Apparence de l’objet, telles que sa couleur, ou la luminosité peut changer.|
|Pointez sur une poignée de sélection|Remplace le pointeur par le curseur de redimensionnement. Pour les objets qui prennent en charge de la rotation, certains d'entre eux de sélection peut changer le pointeur d’un curseur de rotation que le pointeur est positionné différemment (par exemple, déplacé éloignés) en ce qui concerne la poignée de sélection.|
|Faites glisser|Même si l’objet n’est pas déjà sélectionné, remplace le pointeur par le curseur de déplacement et déplace l’objet.|
|Éditeur perd le focus|Désactive le mode d’édition sur place, bien que l’objet conserve le contenu et l’apparence qu’il avait lors de son dernier état de sélection d’opération.|
|Sélection d’objets|Indiqué par une bordure, ligne en pointillés ou tout autre traitement visuellement distincte pour mettre en surbrillance de la limite de l’objet.|
|Redimensionner un objet sélectionné|Indiqué par les poignées de sélection.<br /><br /> Un objet redimensionnable doté de huit poignées, représentant chaque direction dans laquelle elle peut être redimensionnée. Handles moins peuvent être utilisés si l’objet peut uniquement être redimensionné dans certaines directions. Lorsque l’utilisateur redimensionne un objet jusqu’où huit poignées ne serait pas interactives, quatre poignées peuvent ensuite être utilisées. Handle de tailles doivent être liées aux métriques de bordure et le bord de fenêtre avec le **GetSystemMetrics** fonction d’API à la taille par rapport à la résolution d’affichage.<br /><br /> ![Poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-05-resizehandles.png "0713-05_ResizeHandles")|
|Faire pivoter un objet sélectionné|![Poignées de rotation](../../extensibility/ux-guidelines/media/0713-06-rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Interaction du clavier

|Entrée|Résultat|
|-----------|------------|
|Onglet|Déplace l’indicateur de focus entre l’ordre logique des objets dans l’éditeur. Cela peut être de gauche à droite ou haut-bas en fonction **TabIndex** (ou équivalent) valeur de propriété, ordre de création d’objet et l’usage général de l’éditeur. Maj + Tab inverse le sens de l’indicateur de focus.|
|Barre d’espace|Active le mode panoramique tandis que la séquence de touches est conservée. Entrée de souris supplémentaire est nécessaire pour effectuer un panoramique de la position de la fenêtre d’affichage.|
|Ctrl+Barre d'espace|Active le mode de zoom tandis que la séquence de touches est conservée. Entrée de souris supplémentaire est nécessaire pour augmenter et diminuer le facteur de zoom.|
|Ctrl + Alt + signe moins|Diminue le facteur de zoom d’un niveau.|
|Ctrl+Alt+Plus Sign|Augmente le facteur de zoom d’un niveau.|
|MAJ ou Ctrl|Ajoute l’objet au groupe de sélection. CTRL vous permet également à supprimer les objets individuellement à partir du groupe de sélection.|
|Entrée|Exécute la commande par défaut pour l’objet (généralement ouvrir ou modifier).|
|F2|Active la modification sur place pour l’objet.|
|Touches de direction|Déplace les objets sélectionnés dans la direction de la touche enfoncée, par petits incréments (par exemple, 1 pixel à la fois)|
|CTRL + touches de direction|Déplace les objets sélectionnés dans la direction de la touche enfoncée, dans les incréments de grande taille (par exemple, 10 pixels à la fois)|
|Maj + flèche clés|Redimensionne les objets sélectionnés dans la direction respectif, par petits incréments (par exemple, 1 pixel à la fois)|
|CTRL + MAJ + touches de direction|Redimensionne les objets sélectionnés dans la direction respectif, en incréments de grande taille (par exemple, 10 pixels à la fois)|

 Lorsque les utilisateurs modifier des contrôles en place, il peut être judicieux pour les objets redimensionner automatiquement des entrées utilisateur. Par exemple, si l’utilisateur modifie un contrôle d’étiquette, l’étiquette doit augmenter pour afficher le texte saisi par l’utilisateur uniquement. Si cela n’est pas fait, l’utilisateur doit redimensionner le contrôle manuellement après avoir modifié le texte. Si l’utilisateur a un grand nombre de contrôles, cela devient un tâches répétitives et les tâches non productives.

#### <a name="graphical-containers"></a>Conteneurs graphiques
 Dans certains cas, éditeurs graphiques fournissent des conteneurs pour d’autres objets graphiques, tels que le contrôle du contrôle Panel Windows Forms ou le contrôle de disposition en grille dans le Concepteur HTML. Si votre éditeur fournit des conteneurs pour d’autres objets de graphiques, le modèle de sélection suivante doit être utilisé pour le conteneur uniquement (objets dans le suivi de conteneur que le modèle standard comme décrit ci-dessus) :

|Entrée|Résultat|
|-----------|------------|
|Cliquez sur le conteneur|Sélectionne l’objet conteneur sans directement en sélectionnant les objets de relation contenant-contenu. Le conteneur peut-être être déplacé et/ou redimensionné avec standard de la souris et clavier d’entrée (comme décrit ci-dessus). Objets de relation contenant-contenus sont déplacés par rapport au conteneur, mais les objets de relation contenant-contenus ne sont pas redimensionnées, sauf si elles sont également directement sélectionnées.|
|Placez le curseur sur la région des limites du conteneur|Active la souris dans le curseur de déplacement, indiquant que le conteneur peut être déplacé.|
|Faites glisser la région des limites du conteneur|Modifie la souris pour le curseur de déplacement et déplace le conteneur (et les objets contenus dans). Le conteneur ne peut pas être déplacé sans d’abord sélectionné avec un seul clic.|
|Clic sur un objet au sein du conteneur|Désélectionne le conteneur (si sélectionné), sélectionne uniquement l’objet utilisateur a cliqué dessu.|
|MAJ + cliquez sur OR Ctrl + cliquez sur un objet de relation contenant-contenu et/ou d’un conteneur|Ajoute l’objet utilisateur a cliqué dessu à une sélection ou d’un groupe de sélection. Si l’objet sélectionné est déjà membre du groupe de sélection, il est supprimé du groupe de sélection.|

 Les objets de relation contenant-contenus doivent respecter le modèle de sélection de base comme décrit dans la section précédente. À partir de la facilité d’utilisation de test du Concepteur Windows Forms, les utilisateurs prévu, un accès transparent aux objets de relation contenant-contenus sans étapes intermédiaires (imposées par l’objet de relation contenant-contenu).

#### <a name="disjoint-and-region-selections"></a>Disjointes et sélections de région
 Éditeurs de l’objet graphique doivent prendre en charge les sélections disjointes. Veuillez noter que ce graphique n’affiche pas l’apparence du contrôle pour Visual Studio. Consultez [apparence de sélection d’objet graphique](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) des spécifications visual détaillées.

 ![Disjointes sélecteurs de régions et](../../extensibility/ux-guidelines/media/0713-07-disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Sélection disjointe**

 Éditeurs graphiques doivent également fournir des sélections de région avec un indicateur de sélection de type texte défilant. Si l’éditeur graphique prend en charge les autres types d’objets (par exemple, texte), les sélections de région ne peuvent pas être possibles selon les contraintes de ces autres types d’objets.

 ![Sélection de texte défilant](../../extensibility/ux-guidelines/media/0713-08-marqueeselection.png "0713-08_MarqueeSelection")

 **Sélection de texte défilant**

#### <a name="primary-and-secondary-selections"></a>Sélections principale et secondaire
 Certains éditeurs de l’objet graphique autoriser l’utilisateur à modifier ou d’aligner les objets dans des groupes. Dans ce cas, le concept de sélections principale et secondaire doit être introduite. La sélection principale est l’objet auquel tous les autres objets répondent pour les opérations de groupe. L’objet que l’utilisateur sélectionne tout d’abord devienne le contrôle principal et les sélections suivantes deviennent les sélections secondaire. La sélection principale a un traitement visual distinct à partir de l’ou les sélections secondaire pour indiquer quel objet est principal :

 ![Sélection principale et secondaire](../../extensibility/ux-guidelines/media/0713-09-primarysecondary.png "0713-09_PrimarySecondary")

 **Sélection principale avec deux sélections secondaire**

#### <a name="BKMK_GraphicalObjectSelectionAppearance"></a> Apparence de sélection de graphique d’objet
 Les poignées sont des carrés dessinés dans un rectangle autour de la zone englobante de l’objet. Le tableau ci-dessous montre des exemples des différents États qu’un objet graphique peut avoir avec la poignée de dimensionnement et apparence Édition sur place. La taille des poignées doit être liée à la bordure de fenêtre et edge à l’aide de mesures la **GetSystemMetrics** API.

|          État          |  Apparence   |                                                                  Détails des visuels                                                                  |
|-------------------------|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
|     **Non sélectionné**      |    Par défaut    |                 ![État du bouton par défaut](../../extensibility/ux-guidelines/media/0713-10-defaultstate.png "0713-10_DefaultState")                 |
|  **Sélection principale**  |   Redimensionnable   |       ![Sélection principale avec des poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-11-primaryresize.png "0713-11_PrimaryResize")        |
|  **Sélection principale**  | Pas redimensionnables |    ![Sélection principale sans poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-13-primarynoresize.png "0713-13_PrimaryNoResize")    |
|  **Sélection principale**  |    Verrouillé     |              ![Sélection principale verrouillée](../../extensibility/ux-guidelines/media/0713-15-primarylocked.png "0713-15_PrimaryLocked")              |
| **Sélection secondaire** |   Redimensionnable   |    ![Sélection secondaire avec des poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-17-secondaryresize.png "0713-17_SecondaryResize")     |
| **Sélection secondaire** | Pas redimensionnables | ![Sélection secondaire sans poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-19-secondarynoresize.png "0713-19_SecondaryNoResize") |
| **Sélection secondaire** |    Verrouillé     |           ![Sélection secondaire verrouillée](../../extensibility/ux-guidelines/media/0713-21-secondarylocked.png "0713-21_SecondaryLocked")           |
|      **Interface utilisateur active**      |    Par défaut    |                       ![État actif de l’interface utilisateur](../../extensibility/ux-guidelines/media/0713-23-uiactive.png "0713-23_UIActive")                        |

### <a name="view-selection-models"></a>Afficher les modèles de sélection

#### <a name="tree-view"></a>Arborescence
 Sélection dans une arborescence est affichée avec une simple mise en surbrillance. Si l’utilisateur clique sur un nom de nœud ou une icône de nœud, le nœud est sélectionné. Les glyphes triangulaires à gauche du nœud développer ou le contrôle d’arborescence de contrat, mais n’affectent pas la sélection de l’utilisateur, à une exception près : lors de la réduction d’un nœud parent lorsque la sélection est sur un enfant de ce nœud, la sélection se déplace vers le parent.

 ![Arborescence classique dans Visual Studio](../../extensibility/ux-guidelines/media/0713-25-treeview.png "0713-25_TreeView")

 **Arborescence classique dans Visual Studio**

 Vues de l’arborescence peuvent prendre en charge les sélections contigues et disjointes, même sur plusieurs niveaux dans l’arborescence. Contigu ou disjoint sélections multiples doivent être effectuées sur les nœuds d’arbre visible. Si un nœud est réduit, la sélection disjointe est perdue et le nœud qui a été réduit Obtient la sélection. De cette façon, l’utilisateur peut voir les nœuds qui seront affectés par une opération. Lorsque les nœuds sont réduits, il devient difficile de savoir quels nœuds susceptibles d’être affectés.

 Lorsqu’un nœud parent est sélectionné, l’opération doit s’appliquer à la page parente, s’il peut exister des cas où il est préférable pour une opération à appliquer au disque parent et tous ses enfants. Dans ce cas, fournissent une interface utilisateur supplémentaire pendant l’opération, tel qu’une case à cocher ou de la boîte de dialogue de confirmation pour rendre l’option « appliquer à tous les enfants » explicite à l’utilisateur.

##### <a name="renaming"></a>Renommage
 Si les nœuds dans l’arborescence de prendre en charge le changement de nom, le changement de nom doit être effectuée en place. L’opération de déplacement doit être la norme dans tous les contrôles d’arborescence dans Visual Studio. Fournir une commande de changement de nom Active immédiatement le mode d’édition sur place, avec la sélection de texte couvrant l’intégralité du nom du nœud, prêt à accepter l’entrée d’utilisateur. Si le nœud représente un fichier, le nom de fichier doit contenir l’extension. La surbrillance de sélection doit inclure uniquement le corps du nom de fichier et pas l’extension.

|Entrée|Résultat|
|-----------|------------|
|Entrée (touche)|Valide l’opération de changement de nom|
|Touche ÉCHAP|Annule l’opération de changement de nom|
|Cliquez en dehors de la zone d’édition|Valide l’opération de changement de nom|
|Annuler|Fournir facilement Annuler pour annuler l’opération de changement de nom|

#### <a name="selection-within-lists-and-grid-controls"></a>Sélection dans les listes et les contrôles de grille
 Le concept clé dans la sélection de liste est qu’il est basé sur une ligne, ce qui signifie que lorsqu’une sélection est effectuée à la ligne entière est sélectionné en tant qu’unité. En revanche, grilles peuvent autoriser des cellules spécifiques à sélectionner sans affecter tous les autres aspects de la ligne. Grilles peuvent également contenir une hiérarchie de lignes imbriquées (comme dans un contrôle TreeGrid) qui permettent de branches entières de la hiérarchie sélectionnée et désélectionnée en interagissant avec les lignes parentes. Sélection dans les listes est indiquée par une couleur de surbrillance simple sur toute la ligne de données. Le focus est indiqué par une bordure en pointillés pixels autour de la ligne modifiable actuelle ou d’une cellule (ligne si toutes les cellules sont en lecture seule).

> [!NOTE]
> **Le focus** et **sélection** sont des concepts différents. *Le focus* indique de quelle interface utilisateur de l’élément cible pour recevoir une entrée ne sont pas explicitement dirigée vers un autre objet, tandis que *sélection* fait référence à l’état d’inclusion d’un objet dans un ensemble d’objets sur lesquels suivantes opérations peuvent avoir lieu.

 Les sélections dans les listes peuvent être contiguës, disjoint, ou une région. Lorsque les sélections multiples sont autorisées, contiguës et disjointe sélection doit toujours être prise en charge, lors de la prise en charge des sélections de région (zone) sont facultatif. Sélections de région sont initiées en faisant glisser dans l’espace blanc du corps de la liste.

| Object | Sélection  |
|--------|------------|
|  Liste  | Contigus |
|  Liste  |  Disjoint  |
|  Liste  |   Région   |

 En cliquant sur une seule fois sur une liste pour sélectionner la ligne où le clic s’est produit. Si l’utilisateur à cliquer dans une cellule de liste qui prend en charge la modification sur place, la cellule est également immédiatement activée pour modification sur place. Sinon, la ligne entière est immédiatement sélectionnée et affiche une mise en surbrillance.

 Faire glisser dans le corps de la liste effectue une des trois choses :

- Lance une sélection de région, si la liste prend en charge et le bas de la souris est dans un espace blanc

- Initie une opération de glisser-déplacer si la cellule de la liste ou la ligne prend en charge en cours d’une source de glissement

- Sélectionne la ligne actuelle

##### <a name="in-place-editing"></a>Modification sur place
 Lors de la modification sur place est autorisée, il existe deux modèles de base : sélecteur de contrôle et la propriété de modification simple. Avec un contrôle d’édition simple, le contenu est mis en surbrillance et prêt pour l’utilisateur d’entrée dès que la modification sur place est activé. Où un sélecteur de propriété est implémenté, le bouton qui appelle le sélecteur de propriétés s’affichent une fois le mode d’édition sur place est activé, et la sélection actuelle n’est pas mis en surbrillance. Le bouton de sélecteur doit être aligné à droite dans la cellule. Pour des exemples de modifications sur place, consultez le **fenêtre Propriétés** et **liste des tâches** dans Visual Studio.

##### <a name="keyboard-support"></a>Prise en charge du clavier
 Prise en charge du clavier pour la sélection dans les listes et des grilles suit les conventions standards de Windows :

- Touches de direction permettent la liste, en sélectionnant chaque cellule/ligne que le focus est déplacé.

- Maj + flèche effectue une sélection contiguë dans la direction des touches de direction.

- Ctrl + flèche suivie bascules de la barre d’espace entre l’ajout et suppression d’éléments de la sélection, la création d’une sélection disjointe.

- Pour les grilles qui contiennent des hiérarchies imbriquées, la touche flèche droite développe une ligne parente, et la touche de direction gauche réduit un.

- La touche Tab déplace le focus entre les cellules de la ligne actuelle si les cellules sont modifiables.

- La touche entrée exécute la commande par défaut sur l’élément dans la liste (souvent **Open**).

- La touche F2 Active la modification sur place pour la cellule actuellement sélectionnée.

## <a name="BKMK_PersistenceAndSavingSettings"></a> Persistance et l’enregistrement des paramètres

### <a name="overview"></a>Vue d'ensemble
 Bien que chaque composant de logiciel dans Visual Studio est généralement responsable pour son propre état et la persistance, Visual Studio enregistre automatiquement les paramètres dans certains cas, comme avec les positions et les tailles de fenêtre. Le tableau ci-dessous est une combinaison de paramètres enregistrés automatiquement et qui requièrent un utilisateur explicit ou programmé action à entreprendre.

|Object|Les éléments à enregistrer|Quand l’enregistrer|Emplacement d’enregistrement|
|------------|------------------|------------------|-------------------|
|Objet sélectionnable (par exemple, une ligne de code)|Un point d’arrêt sur une ligne de code<br /><br /> Un raccourci de l’utilisateur associé à la ligne de code|Lorsque le projet est enregistré.|Le **options utilisateur (.suo)** fichier pour le projet|
|Boîte de dialogue|L’emplacement de la boîte de dialogue, s’il avait été déplacé<br /><br /> La vue que l’utilisateur utilisée en dernier dans la boîte de dialogue|Lorsque la boîte de dialogue se ferme<br /><br /> Lorsque la session de Visual Studio se termine|Dans la mémoire<br /><br /> Registre dans **HKEY_Current_User**|
|Fenêtre|La taille et l’emplacement de la fenêtre|Lorsque la fenêtre se ferme<br /><br /> Lorsque le mode de Visual Studio est modifié<br /><br /> Lorsque la session de Visual Studio se termine|Le **options utilisateur (.suo)** fichier pour le projet<br /><br /> Fichier d’options personnalisées pour les paramètres de la fenêtre|
|Document|La sélection actuelle dans le document<br /><br /> La vue du document<br /><br /> Les dernière plusieurs endroits que l’utilisateur a visité|Lorsque le document est enregistré|Le **options utilisateur (.suo)** fichier pour le projet|
|Projet|Références aux fichiers<br /><br /> Références à des répertoires sur le disque<br /><br /> Références à d’autres logiciels<br /><br /> Composants<br /><br /> Informations d’état sur le projet lui-même|Lorsque le projet est enregistré.|Le fichier projet|
|Solution|Références aux projets<br /><br /> Références aux fichiers|Lorsque le projet ou la solution est enregistrée|Le **solution (.sln)** fichier|
|Paramètres dans **Outils > Options**|Personnalisations de clavier<br /><br /> Personnalisations de la barre d’outils<br /><br /> Jeux de couleurs|Lorsque le **Outils > Options** boîte de dialogue fermée<br /><br /> Lorsque la session de Visual Studio se termine|Registre dans **HKEY_Current_User**|

 Ce que fait l’utilisateur et lorsqu’ils font, détermine si un paramètre est enregistré dans la mémoire (pendant la session), enregistrée sur le disque (entre les sessions en tant qu’un paramètre de Registre), dans le cadre du projet ou solution fichier lui-même, dans le cadre de la **solution Options (.suo)** de fichiers, ou que des paramètres personnalisés de fichiers que seul ce composant logiciel connaît. Le tableau ci-dessus présente plusieurs événements à laquelle les paramètres peuvent être enregistrés. Toutefois, il existe d’autres cas dans lesquels vous souhaiterez enregistrer l’état :

- Lorsque l’utilisateur modifie l’emplacement au sein d’une fenêtre ou boîte de dialogue

- Lorsque l’utilisateur transfère le focus vers une autre fenêtre

- Lorsque l’utilisateur bascule de la conception au mode de débogage

- Lorsque l’utilisateur se déconnecte son compte

- Lorsque l’ordinateur en veille prolongée ou s’arrête

- Lorsque le disque dur / l’ordinateur est sur le point d’être reformaté et configurer à nouveau

### <a name="window-configurations"></a>Configurations de fenêtres
 Une configuration de fenêtres est la présentation de base de l’environnement de développement : il s’agit d’un schéma comprenant la liste des fenêtres d’outils présents et la façon dans lequel ils sont organisés. Pour windows gérés par l’IDE (IDE windows), les informations de mise en page sont conservées par utilisateur, donc lorsqu’un utilisateur lance l’IDE, la disposition de fenêtre s’affiche le même que lors de la dernière sortie Visual Studio. L’état et la position de windows de l’IDE est conservé dans un fichier d’options personnalisées au format XML. Fenêtres Outil créées par les packages chargés dans l’IDE conserver leurs informations d’état dans le Registre et ne peuvent pas forcément par utilisateur.

#### <a name="profile-specific-layouts"></a>Dispositions spécifiques au profil
 Chaque profil inclut des dispositions de fenêtres Outil, organisées de manière familière aux personnes avec spécifiques pour les développeurs (les développeurs Visual C++ vous attendre à voir les **l’Explorateur de solutions** sur le côté gauche de l’IDE, tandis que les développeurs c# vous attendre à voir le  **L’Explorateur de solutions** sur la droite). Dispositions de fenêtres de profil spécifiques sont chargées une fois que l’utilisateur choisit un profil de démarrage. Auteur d’un package doit déterminer la disposition de fenêtre plus adaptée à leur expérience client, en sachant que les modifications apportées par l’utilisateur à la configuration de la fenêtre sont ensuite rendues persistantes.

## <a name="BKMK_TouchInput"></a> Entrée tactile
 Les utilisateurs ont recours à des produits de développement de Microsoft sur les appareils tactiles. Toutefois, il existe des barrières qui rendent difficile à utiliser les outils de développement sur les appareils tactiles. Les utilisateurs s’attendent à nos produits pour fournir une expérience tactile fiables et précises. L’objectif de ces recommandations consiste à indiquer des décisions sur les fonctions tactiles d’incorporer et à encourager une expérience tactile cohérent entre Visual Studio et les produits connexes.

### <a name="levels-of-experience"></a>Niveaux d’expérience
 Les niveaux d’expérience suivants sont destinés à servir de guide pour aider les équipes à déterminer les fonctions tactiles pour offrir selon leur niveau d’intérêt d’investissement en contact souhaité.

- Le **une expérience Basique** est pour les équipes qui souhaitent fournir des fonctionnalités tactiles et n’est donc pas d’ends mortes tout au long de leur travail.

- Le **optimisé expérience** s’adresse aux équipes qui souhaitent fournir le meilleur parti des fonctionnalités tactiles courantes (par exemple, ceux généralement disponibles dans les applications de navigateur internet).

- Le **élevés expérience** est pour les équipes qui souhaitent ajouter des fonctionnalités telles que mouvements ou autres fonctionnalités facultatives qui peuvent rendre leurs applications tactiles d’abord convivial.

||Expérience de base|Expérience optimisée|Expérience avec élévation de privilèges|
|-|----------------------|--------------------------|-------------------------|
|Permet aux utilisateurs de...|Corriger le code et solution/projet au niveau lecture sans les extrémités de lettres mortes|Effectuer des tâches de maintenance, de refactorisations et de navigation|Fonctionner en une expérience cohérente, intuitive et fluide en toute confiance|
|Éditeur|Défilement tactile et la sélection<br /><br /> Tactile de barre de défilement pour accéder et appuyez sur + faire glisser|Zoom de pincement<br /><br /> Défilement rapide<br /><br /> Sélection<br /><br /> Faciliter l’utilisation du menu contextuel||
|Fenêtres Outil principales|Panoramique de la liste<br /><br /> Sélection d’éléments<br /><br /> Tactile de barre de défilement pour accéder et appuyez sur + faire glisser|Élément facile le défilement et la sélection||
|Fenêtrage||Redimensionner la fenêtre<br /><br /> Accès rapide||
|Document bien||Facilite la navigation entre les fichiers ouverts||
|Mouvements||S’assurer que les mouvements courants fonctionnent dans l’IDE|Actions basées sur les mouvements<br /><br /> Prend en charge du glisser-déplacer et les concepteurs|
|Autres considérations|||Clavier visuel personnalisé|

#### <a name="gestures"></a>Mouvements
 Mouvements de fournissent aux utilisateurs un raccourci vers les commandes qui pourraient nécessiter une interaction plus complexe. Reportez-vous aux instructions de Windows sur [des entrées tactiles courantes pour les Applications de bureau](http://msdn.microsoft.com/library/windows/desktop/dd940543\(v=vs.85\).aspx)et suivez ces instructions pour la plupart des gestes, y compris des gestes simples telles que l’affichage panoramique et zoom.
