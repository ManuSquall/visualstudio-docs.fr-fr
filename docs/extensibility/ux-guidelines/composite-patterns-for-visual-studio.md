---
title: Modèles composites pour Visual Studio | Microsoft Docs
description: En savoir plus sur les modèles composites importants pour la cohérence dans Visual Studio. Les modèles composites combinent les éléments d’interaction et de conception.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b8b84baa7be7449b8edb6241e415fc90c9acd594
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901420"
---
# <a name="composite-patterns-for-visual-studio"></a>Modèles composites pour Visual Studio
Les modèles composites combinent des éléments d’interaction et de conception dans des configurations distinctes. Voici quelques-uns des modèles composites les plus importants dans Visual Studio en ce qui concerne la cohérence :

- [Visualisation des données](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [Interface utilisateur et aperçu en un objet](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Modèles de sélection](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Persistance et enregistrement des paramètres](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Entrée tactile](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a> Visualisation des données

### <a name="overview"></a>Vue d’ensemble
 Les graphiques sont un moyen visuel d’agréger et de visualiser des données afin d’améliorer la prise de décision. Ils peuvent aider les utilisateurs à être confrontés à beaucoup de données, mais peu d’entre elles, voir ce qui mérite une attention et ce qui peut nécessiter une action.

 L’utilisateur bénéficie d’un graphique si l’une des conditions suivantes est vraie :

- Le graphique aide-t-il les utilisateurs à identifier les tâches sur lesquelles ils peuvent agir ?

- Le graphique permettra-il aux utilisateurs de prévoir les conséquences des modifications potentielles ?

- Le graphique aide-t-il les utilisateurs à découvrir les tendances et à identifier les modèles ?

- Le graphique permet-il aux utilisateurs de prendre de meilleures décisions ?

- Le graphique aide-t-il à répondre à une question spécifique que les utilisateurs peuvent avoir dans le contexte donné ?

#### <a name="general-rules-for-charts"></a>Règles générales pour les graphiques

- Étiquetez clairement les données. Les illustrations sans explication sont juste des images.

- Démarrer les axes à zéro pour éviter l’inclinaison des proportions. La longueur de ligne et la taille de la barre sont des indications visuelles importantes pour comprendre les relations entre les points de données.

- Créer des graphiques, et non infographies. Les infographies sont des représentations artistiques de données, et leur objectif principal est la narration visuelle. Les graphiques peuvent être visuellement attrayants, tout en permettant aux données de parler eux-mêmes.

- Évitez les skeumorphism, les graphiques à barres, les hashmarks de contraste et les autres touches infographie.

- N’utilisez pas d’effets 3D en tant qu’élément décoratif. Utilisez-les uniquement s’ils sont véritablement intégrables à la capacité de l’utilisateur à comprendre les informations.

- Évitez d’utiliser plusieurs lignes et remplissages, car plus de deux couleurs peuvent rendre ce type de graphique difficile à lire et interpréter correctement.

- N’utilisez pas un graphique (ou une illustration) comme seul moyen de comprendre un concept ou d’interagir avec des données. Cela présente des difficultés pour les utilisateurs ayant des handicaps.

- N’utilisez pas de graphiques en tant qu’éléments non décoratives ou décoratives sur une page. En d’autres termes, si un graphique n’ajoute pas de valeur ou aide les utilisateurs à résoudre un problème, ne l’utilisez pas.

### <a name="chart-types"></a>Types de graphiques
 Les types de graphiques utilisés dans Visual Studio incluent des graphiques à barres, des graphiques en courbes, un graphique à secteurs modifié connu sous le nom de graphique en anneau ou « graphique en anneau », des chronologies, des nuages de points (également appelés « diagrammes de cluster ») et des diagrammes de Gantt. Chaque type de graphique est utile pour la communication d’un type d’informations différent.

### <a name="other-charting-considerations"></a>Autres considérations relatives aux graphiques

#### <a name="color"></a>Couleur
 Une palette spécifique de couleurs de graphiques est définie pour être utilisée dans Visual Studio. La palette est accessible pour les principaux types de cécité des couleurs, et les couleurs peuvent être différenciées même si elles sont utilisées comme des secteurs de couleur très étroits. Vous pouvez utiliser ces couleurs dans n’importe quelle combinaison pour n’importe quel type de graphique ou graphique dans votre interface utilisateur. Vous n’avez pas besoin d’utiliser les sept couleurs si vous n’avez pas besoin de nombreuses couleurs distinctes. Ces couleurs n’ont pas été conçues pour être utilisées avec des éléments de premier plan, par conséquent, ne placez pas de texte ou de glyphes par-dessus ces couleurs. Ces teintes doivent être codées en dur et exposées à la personnalisation utilisateur sous **outils > options** (voir [exposition des couleurs pour les utilisateurs finaux](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).

|Echantillon|Hex|RGB|
|------------|---------|---------|
|![Échantillon 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113178, 82|
|![Échantillon BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191, 63, 0|
|![Échantillon FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252183, 20|
|![Échantillon 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144, 63139|
|![Échantillon 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17 122 209|
|![Échantillon 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121 215 242|
|![Échantillon B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181 181 181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a> Interface utilisateur et aperçu en un objet
 Cette section fournit un contexte de lecture, également appelé vue d’aperçu du code, un type d’interface utilisateur sur objet unique à Visual Studio.

### <a name="overview"></a>Vue d’ensemble

- L’interface utilisateur sur l’objet doit fournir à l’utilisateur des informations supplémentaires ou une interactivité sans dépasser de sa tâche principale.

- Le modèle principal de l’interface utilisateur sur l’objet dans Visual Studio est appelé « informations à l’attention ».

- L’interface utilisateur sur l’objet dans Visual Studio est soit en ligne, soit flottante, soit durable soit transitoire.

  - La vue aperçu du code, un type d’interface utilisateur sur l’objet dans Visual Studio, est inline et durable.

  - CodeLens, un type d’interface utilisateur on-Object dans Visual Studio, est flottant et temporaire

  La compréhension du fonctionnement d’un morceau de code, ou la recherche de détails sur ce code, requiert souvent un développeur pour changer de contexte et accéder à d’autres contenus ou à une autre fenêtre. Ces décalages de contexte peuvent être perturbés, car les utilisateurs peuvent perdre leur attention sur leur tâche d’origine s’ils laissent leur fenêtre principale. En outre, il peut être difficile de faire en sorte que le contexte d’origine soit difficile, en particulier si le changement de Windows a provoqué la masquage de son code d’origine par une autre interface utilisateur.

  L’interface utilisateur sur l’objet suit un modèle appelé « informations à l’attention ». Ces messages, fenêtres contextuelles et boîtes de dialogue fournissent aux utilisateurs des informations supplémentaires pertinentes qui ajoutent des éclaircissements ou une interactivité sans perdre leur attention à leur tâche principale. Les fenêtres contextuelles qui s’affichent lorsqu’un utilisateur place le pointeur sur une icône dans la zone de notification, le tilde rouge sous un mot mal orthographié et l’aperçu présenté dans Visual Studio 2013 sont des exemples d’interface utilisateur.

### <a name="decision-points"></a>Points de décision
 Dans Visual Studio, il existe plusieurs façons d’utiliser ce modèle d’informations à l’attention. Choisir le mécanisme approprié et l’implémenter de manière cohérente et prévisible est essentiel à l’expérience globale. Dans le cas contraire, les utilisateurs peuvent être confrontés à une expérience confuse ou incohérente qui détournent le focus du contenu lui-même.

#### <a name="relationships-between-master-and-detail-content"></a>Relations entre le contenu maître et le contenu de détail
 Les informations à l’attention sont utilisées pour afficher une relation entre le contenu sur lequel l’utilisateur se concentre (le contenu « maître ») et le contenu connexe supplémentaire (le contenu « détail »). Dans ce modèle, le contenu détaillé est clairement lié au contenu utilisé par l’utilisateur et peut être affiché à proximité du contenu maître. Informations supplémentaires ou informations qui ne peuvent pas être résumées sans trop d’informations le contenu maître doit suivre un autre modèle, tel qu’une fenêtre outil.

- Affiche **toujours** le contenu détaillé à proximité du contenu maître.

- Vérifiez **toujours** que le contenu détaillé permet toujours à un utilisateur de rester concentré sur le contenu maître. Souvent, la meilleure façon d’y parvenir consiste à afficher le contenu de détail aussi près que possible du contenu maître. Pour ce faire, vous pouvez restituer le contenu de détail dans une fenêtre indépendante en regard du contenu maître ou afficher le contenu de détail en ligne sous le contenu maître.

- **N’utilisez jamais** d’informations au point d’attention qui éloignent l’utilisateur du contenu maître. Si les utilisateurs ont besoin d’afficher le contenu des détails séparément, exposez une action explicite qui permet à l’utilisateur de le faire.

#### <a name="design-details"></a>Détails de la conception
 Une fois que vous avez déterminé que l’interface utilisateur de l’objet est le bon choix, il existe quatre considérations principales en matière de conception :

1. **Persistance :** le contenu est-il censé être durable ou transitoire ?
   Les utilisateurs devront-ils conserver les informations visibles pour y faire référence ou interagir ? Ou les utilisateurs voudront-ils rapidement en savoir plus sur les informations, puis continuer leurs tâches principales ?

2. **Type de contenu :** le contenu sera-t-il à titre informatif, exploitable ou de navigation ?
   L’utilisateur a-t-il besoin de détails supplémentaires sur le contenu maître ? L’utilisateur a-t-il besoin d’effectuer une tâche qui affecte le contenu maître ? Ou l’utilisateur doit-il être dirigé vers une autre ressource ?

3. **Type d’indicateur :** un indicateur ambiant a-t-il un sens ?
   Les informations peuvent-elles être résumées de façon utile et s’afficher sans trop le contenu maître ?

4. **Gestes :** quels gestes seront utilisés pour appeler et faire disparaître l’interface utilisateur ?
   Comment l’utilisateur affichera-t-il le contenu détaillé et l’enverra ? Y a-t-il une valeur pour ajouter un mouvement tel que l’épinglage pour basculer entre les États temporaires et durables ?

   Chacun de ces quatre points de décision aura un impact sur les principaux composants de l’interface utilisateur de l’objet.

### <a name="on-object-ui-components"></a>Composants de l’interface utilisateur sur l’objet

1. Type de conteneur (Content Presenter)

    - Virgule flottante

    - En ligne

2. Type de contenu

    - Information : données qui peuvent être statiques ou dynamiques

    - Actionable : commandes qui modifient le contenu maître

    - Navigation : liens qui permettent à l’utilisateur d’accéder à une autre fenêtre ou application, comme MSDN

3. Mouvements

    - Invocation

    - Ignorées

    - Épinglage

    - Autres interactions

4. Persistance et modèle de validation

    - Temporaire

    - Durable

    - Automatique

    - À la demande

5. Indicateurs ambiants (facultatif)

    - Souligné en tilde

    - Icône de balise active

    - Autres indicateurs ambiants

#### <a name="container-content-presenter-type"></a>Type de conteneur (Content Presenter)
 Deux options majeures sont disponibles pour présenter le contenu au point d’attention :

1. **Inline :** un présentateur Inline, tel que la vue d’aperçu introduite dans l’éditeur de code Visual Studio 2013, crée de l’espace pour le nouveau contenu en décalant le contenu existant.

    - **Préférez** les présentateurs Inline si vous vous attendez à ce que les utilisateurs souhaitent consacrer un temps considérable à la référence ou à l’interaction avec le contenu que vous présentez.

    - **Évitez** les présentateurs Inline si vous vous attendez à ce que les utilisateurs souhaitent en savoir plus sur les informations que vous présentez, puis poursuivez avec leurs tâches principales avec une interruption minimale.

2. **Flottant :** un présentateur flottant est positionné aussi près que possible du contenu sélectionné, mais ne modifie pas la disposition du contenu existant. Différentes stratégies peuvent être utilisées, telles que l’affichage d’un panneau de contenu flottant sur l’espace blanc le plus proche du symbole sélectionné.

    - **Préférer** les présentateurs flottants si vous vous attendez à ce que les utilisateurs souhaitent en savoir plus sur les informations que vous présentez, puis poursuivez avec leurs tâches principales avec une interruption minimale.

    - **Évitez** les présentateurs flottants si vous vous attendez à ce que les utilisateurs souhaitent consacrer un temps considérable à la référence ou à l’interaction avec le contenu que vous présentez.

#### <a name="content-type"></a>Type de contenu
 Il existe trois types de contenu principaux qui peuvent être affichés dans n’importe quel conteneur d’interface utilisateur. Vous pouvez afficher n’importe quelle combinaison de ces types d’informations. Les trois types sont :

1. **Informations :** la plupart des conteneurs d’interface utilisateur sur l’objet affichent un certain type de contenu d’information. Le contenu peut représenter des informations sur l’état actuel de l’environnement ou il peut représenter des informations sur un état futur potentiel de l’environnement. Par exemple, il peut être utilisé pour afficher l’effet d’une commande particulière, telle qu’une refactorisation, sur le code existant.

    - Utilisez **toujours** la représentation canonique des informations que vous affichez. Par exemple, le code doit ressembler à du code, à la mise en surbrillance de la syntaxe et doit respecter la police et les autres paramètres d’environnement définis par l’utilisateur.

    - Envisagez **toujours** de prendre en charge toutes les actions sur le contenu d’information qui serait possible si ces mêmes informations sont présentées sous forme de contenu maître. Par exemple, si vous présentez du code existant à l’intérieur d’un conteneur d’interface utilisateur, envisagez fortement de prendre en charge la possibilité de parcourir et de modifier ce code.

    - Envisagez **toujours** d’utiliser une autre couleur d’arrière-plan si vous présentez du contenu informatif qui représente un état futur potentiel.

2. Actionable : certains conteneurs d’interface utilisateur sur l’objet offrent la possibilité d’effectuer certaines actions sur le contenu maître, comme effectuer une opération de refactorisation.

    - Placez **toujours** les commandes actionnables séparément du contenu d’information.

    - Activez et désactivez **toujours** les actions, le cas échéant.

    - Reportez-vous **toujours** aux instructions standard pour représenter les commandes dans les boîtes de dialogue.

    - Conservez **toujours** le nombre d’actions exposées dans un conteneur d’interface utilisateur sur l’objet à un minimum absolu. L’interaction avec l’interface utilisateur sur un objet doit être une expérience légère et rapide. L’utilisateur n’a pas besoin d’utiliser de l’énergie pour gérer le conteneur d’interface utilisateur sur l’objet lui-même.

    - Déterminez **toujours** comment et quand un conteneur d’interface utilisateur est fermé ou ignoré. En guise de meilleure pratique, toute action qui conclut le dialogue entre le contenu maître et le contenu de détail doit également fermer le conteneur de l’interface utilisateur sur l’objet lorsque cette action est appelée.

3. **Navigation :** certains conteneurs d’interface utilisateur sur l’objet incluent des liens qui permettent à l’utilisateur d’accéder à une autre fenêtre ou application, par exemple en ouvrant un article MSDN dans le navigateur Web de l’utilisateur.

    - Ajoutez **toujours** un lien de navigation avec « Open » afin que les utilisateurs ne soient pas surpris par la navigation vers d’autres contenus.

    - Séparez **toujours** les liens de navigation des liens exploitables.

#### <a name="ambient-indicators-optional"></a>Indicateurs ambiants (facultatif)
 Les indicateurs ambiants peuvent être discrets, y compris le texte présenté dans une couleur contrastée du reste du code, ou bien évident, y compris les symboles tickler tels que les soulignements en tilde et les icônes de balise active. Les indicateurs ambiants communiquent la disponibilité d’informations supplémentaires pertinentes. Idéalement, elles fournissent des informations utiles même sans que l’utilisateur ne soit obligé d’interagir avec elles.

- Placez **toujours** un indicateur ambiant de manière à ce qu’il ne gêne pas ou ne surcharge pas l’utilisateur. S’il est impossible de positionner un indicateur ambiant d’une telle manière, envisagez une autre solution.

- Placez **toujours** l’indicateur ambiant aussi près que possible du contenu auquel il est lié.

- Essayez **toujours** de créer un indicateur qui synthétise les informations qu’il rend disponibles. Envisagez de fournir un décompte du nombre d’éléments de données disponibles (par exemple, « 3 références » au lieu de « références » simplement) ou d’une autre façon de synthétiser les données.

  - Dans les cas où les données d’un indicateur ne peuvent pas toujours être calculées et affichées, pensez immédiatement à fournir des commentaires progressifs à mesure que les valeurs sont calculées. Par exemple, envisagez d’animer les modifications qui reflètent les mises à jour des données disponibles, de la même façon que la vignette de messagerie dynamique sur Windows Phone est actualisée à mesure que le nombre d’e-mails non lus augmente.

- **N’ajoutez jamais** plus d’indicateurs qu’un utilisateur ne peut raisonnablement prendre dans le cas d’une partie de contenu donnée. Les indicateurs ambiants doivent être utiles sans nécessiter l’intervention de l’utilisateur. Les indicateurs perdent leur ambiance s’ils nécessitent un dépassement de capacité et d’autres contrôles de gestion pour les mettre en vue.

#### <a name="gestures"></a>Mouvements
 L’un des aspects clés de la possibilité pour l’utilisateur de conserver le focus sur le contenu maître est de prendre en charge les gestes appropriés pour ouvrir et ignorer le contenu de détail supplémentaire.

- Demandez **toujours** à l’utilisateur d’effectuer des mouvements explicites pour ouvrir le contenu supplémentaire. Les gestes ouverts courants sont les suivants :

  - **Pointage :** info-bulles ou contenu informatif non interactif

  - **Commande explicite :** présentateur Inline

  - **Double-cliquez sur l’indicateur ambiant :** Fenêtre contextuelle CodeLens

- Faites **toujours** disparaître le contenu des détails chaque fois que l’utilisateur appuie sur la touche ÉCHAP.

- Tenez **toujours** compte du contexte de l’interface utilisateur sur l’objet. Pour les présentateurs de contenu qui autorisent l’interaction au sein du conteneur, déterminez attentivement s’il faut afficher des informations supplémentaires sur le pointage, ce qui risque de perturber le flux de travail de l’utilisateur.

- **N'** Affichez jamais le contenu au pointage qui semble modifiable ou qui invite l’interaction de l’utilisateur. Ce comportement peut nuire aux utilisateurs s’ils essaient de déplacer le curseur sur le contenu de détail, car le comportement standard d’une info-bulle consiste à faire disparaître immédiatement lorsque le curseur ne se trouve plus sur le contenu maître qui l’a généré.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a> Modèles de sélection

### <a name="overview"></a>Vue d’ensemble
 Un modèle de sélection est le mécanisme utilisé pour indiquer et confirmer les opérations sur un ou plusieurs objets intéressants au sein de l’interface utilisateur. Cette rubrique décrit les modèles d’interaction de sélection dans les éditeurs de documents Visual Studio : les éditeurs de texte, les aires de conception et les surfaces de modélisation.

 Les utilisateurs doivent avoir un moyen d’indiquer à Visual Studio ce qu’ils travaillent, et Visual Studio doit répondre de façon prévisible aux commentaires des utilisateurs sur ce qu’il utilise. Des différences ou une communication incorrecte entre l’utilisateur et l’interface utilisateur peuvent empêcher l’utilisateur de remarquer une action, ce qui peut avoir des conséquences inattendues. Souvent, l’erreur est inaperçue jusqu’à ce que l’utilisateur constate qu’un problème est manquant ou a changé. Les modèles de sélection sont donc l’un des éléments les plus importants de la conception de l’interface utilisateur. Bien que les modèles de sélection dans Visual Studio soient cohérents avec Windows, il y a de légères variations.

 Dans Visual Studio, comme dans Windows, les modèles de sélection diffèrent selon le contexte dans lequel l’interaction se produit. Vous pouvez effectuer des sélections dans quatre types d’objets :

- Texte

- Objets graphiques

- Listes et arborescences

- Grilles

  Au sein de ces objets, il existe trois types de sélection :

- Contiguë

- Disjoint

- Région

#### <a name="scope"></a>Étendue
 Le composant le plus important de la sélection consiste à s’assurer que l’utilisateur sait dans quelle fenêtre il travaille (activation) et où se trouve le focus (sélection). Visual Studio étend les fonctionnalités de gestion des fenêtres dans Windows, mais le schéma d’activation est le même : l’interaction avec une fenêtre met le focus sur la fenêtre. Visual Studio a deux indicateurs d’activation : un pour les fenêtres de document et un pour les fenêtres outil.

 Pour les fenêtres de document, la fenêtre active est indiquée par un onglet de fenêtre de document à l’avant et en modifiant sa couleur d’arrière-plan :

 ![Sélection de l'onglet actif dans Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **Sélection de l’onglet actif**

 Pour les fenêtres outil, la fenêtre active est indiquée par une modification de la couleur de la zone de barre de titre de la fenêtre outil :

 ![Sélection de la fenêtre Outil active dans Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **Fenêtre outil active présentant la sélection principale d’un nœud**

 ![Sélection de la fenêtre Outil inactive dans Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Fenêtre outil inactive, présentant la sélection latente du nœud**

 Une fois qu’une fenêtre est active, son focus est indiqué en fonction des modèles de sélection décrits dans cette section des instructions.

#### <a name="context"></a>Contexte
 Visual Studio a été conçu pour conserver un concept solide de contexte, en gardant le suivi de l’emplacement de travail de l’utilisateur. Une seule fenêtre est active, qu’il s’agisse d’un outil ou d’une fenêtre de document. Toutefois, la fenêtre de document en haut conserve toujours une sélection latente. Même si le focus peut se trouver dans une fenêtre outil, la fenêtre de document qui était active affiche une sélection, même dans un état inactif. Cela permet de conserver le contexte de l’utilisateur dans le document qu’il a modifié, en les signalant que Visual Studio a conservé son état afin qu’il puisse retourner et basculer en toute transparence entre les fenêtres outil et les fenêtres de document.

### <a name="text-selection"></a>Sélection de texte
 Les éditeurs Visual Studio qui sont strictement textuels, tels que l’éditeur de texte intégré, utilisent le même modèle de sélection de texte et l’apparence décrits dans la page [souris et pointeurs](/windows/desktop/uxguide/inter-mouse) des instructions d’interaction avec l’expérience utilisateur Windows sur MSDN. Le focus d’entrée dans l’éditeur de texte est indiqué par une barre verticale appelée point d’insertion. Le point d’insertion est un pixel épais et coloré comme inverse de tout ce qui se trouve derrière lui. Il clignote en fonction de la vitesse définie par le paramètre **taux de clignotement du curseur** dans l’onglet **Vitesse** de l’applet clavier du panneau de **configuration** .

#### <a name="contiguous-and-disjoint-selection"></a>Sélection contiguë et disjointe
 La sélection dans l’éditeur de texte est contiguë uniquement. Les sélections de texte disjoint ne sont pas autorisées, mais elles doivent être traitées dans les éditeurs d’objets graphiques. Lorsque le pointeur de la souris de l’utilisateur se trouve sur une zone de texte, le curseur se transforme en I. Un clic simple place le point d’insertion dans l’éditeur de texte à l’emplacement de clic. Maintenez le bouton de la souris enfoncé pour démarrer une sélection et relâcher le bouton de la souris pour mettre la sélection en surbrillance.

#### <a name="region-selection-box-selection"></a>Sélection de la région (sélection de zone)
 Visual Studio prend en charge les sélections de régions dans l’éditeur de texte, et c’est ce que l’on appelle la sélection de zone. La sélection de zone permet à l’utilisateur de sélectionner une zone de texte qui ne suit pas le flux de texte normal. Comme pour la sélection de texte standard, la sélection doit être contiguë. La sélection de la zone est lancée en maintenant la touche Alt enfoncée tout en faisant glisser la souris. La sélection de zone peut également être lancée en maintenant les touches Alt et Maj enfoncées tout en utilisant les touches de direction pour indiquer la région de sélection. La sélection de zone utilise la sélection normale en surbrillance et affiche le curseur de point d’insertion clignotant à la fin de la zone de sélection.

 ![Boîte de &#40;régionale&#41; sélection dans Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Sélection d’une région (zone) dans Visual Studio**

#### <a name="text-selection-appearance"></a>Apparence de la sélection de texte
 Les couleurs utilisées pour la sélection active et inactive dans l’éditeur peuvent être personnalisées. Pour personnaliser l’apparence visuelle de l’éditeur, un utilisateur peut accéder à **outils > options**, puis sous **environnement > polices et couleurs > éditeur de texte**.

### <a name="graphical-selection"></a>Sélection graphique

#### <a name="interaction"></a>Interaction
 La sélection d’objets graphiques peut être complexe et dépend d’un certain nombre de facteurs :

- **Modèle de sélection principal de l’éditeur.** Les éditeurs qui contiennent des objets graphiques peuvent également être utilisés pour modifier du texte ou des grilles. Par exemple, l’éditeur peut être un éditeur textuel qui prend également en charge le placement d’objets graphiques, tels que le concepteur XAML Visual Studio. La prise en charge de plusieurs types d’objets peut affecter la façon dont l’utilisateur sélectionne des groupes composés de différents types d’objets.

- **Prise en charge des États de sélection primaire et secondaire.** Un éditeur peut fournir des États de sélection principaux et secondaires afin que les objets puissent être modifiés en interaction, alignés les uns avec les autres, redimensionnés ensemble, etc.

- **Prise en charge de la modification sur place.** Les éditeurs peuvent également permettre la modification du contenu de leurs objets graphiques. Par exemple, une forme de rectangle peut également contenir du texte à l’intérieur qui peut être modifié par l’utilisateur. En outre, ce texte peut être centré ou justifié. La modification sur place implique un niveau d’interaction utilisateur plus détaillé et requiert donc un ensemble approprié de signaux visuels pour la présentation des informations d’État à l’utilisateur.

#### <a name="mouse-interaction"></a>Interaction avec la souris

|Entrée|Résultats|
|-----------|------------|
|Cliquer sur un objet non sélectionné|Sélectionne l’objet et affiche une ligne en pointillés et des poignées de sélection, si l’objet est redimensionnable.|
|Cliquer sur un objet sélectionné|Active la modification sur place si l’objet la prend en charge. En cliquant en dehors de l’objet, vous désactivez le mode d’édition sur place.|
|Double-cliquez sur un objet.|Ouvre le code derrière l’objet pour modification et peut insérer un gestionnaire d’événements par défaut, le cas échéant.|
|Pointer vers un objet|Remplace le pointeur par le curseur de déplacement. L’apparence de l’objet, telle que sa luminosité ou sa couleur, peut changer.|
|Pointer sur une poignée de sélection|Remplace le pointeur par le curseur de redimensionnement. Pour les objets qui prennent en charge la rotation, certains handles de sélection peuvent remplacer le pointeur par un curseur de rotation, car le pointeur est positionné différemment (par exemple, déplacé plus loin) par rapport au handle de sélection.|
|Glissement|Même si l’objet n’est pas sélectionné précédemment, remplace le pointeur par le curseur déplacer et déplace l’objet.|
|L’éditeur perd le focus|Désactive le mode d’édition sur place, bien que l’objet conserve le contenu et l’apparence qu’il avait lors de sa dernière opération/état de sélection.|
|Sélection de l’objet|Indiqué par une bordure, une ligne en pointillés ou un autre traitement visuel distinct pour mettre en surbrillance la limite de l’objet.|
|Redimensionner un objet sélectionné|Indiqué par les poignées de sélection.<br /><br /> Un objet redimensionnable a huit handles, représentant chaque direction dans laquelle il peut être redimensionné. Moins de handles peuvent être utilisés si l’objet ne peut être redimensionné que dans certaines directions. Lorsque l’utilisateur redimensionne un objet jusqu’à ce que huit descripteurs ne soient pas interactifs, quatre descripteurs peuvent être utilisés. Les tailles des handles doivent être liées à la bordure de la fenêtre et aux métriques de l’arête avec la fonction d’API **GetSystemMetrics** pour une taille proportionnelle à la résolution d’affichage.<br /><br /> ![Poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|Faire pivoter un objet sélectionné|![Poignées de rotation](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Interaction du clavier

|Entrée|Résultats|
|-----------|------------|
|Onglet|Déplace l’indicateur de focus parmi l’ordre logique des objets dans l’éditeur. Il peut s’agir de gauche à droite ou de haut en bas en fonction de la valeur de propriété **TabIndex** (ou équivalente), de l’ordre de création de l’objet et de l’objectif global de l’éditeur. Maj + Tab inverse le sens de l’indicateur de focus.|
|Espace|Active le mode panoramique pendant que la frappe est maintenue. Une entrée de souris supplémentaire est nécessaire pour effectuer un panoramique de la position de la fenêtre d’affichage.|
|Ctrl+Barre d'espace|Active le mode de zoom lorsque la frappe est maintenue. Une entrée de souris supplémentaire est nécessaire pour augmenter et diminuer le facteur de zoom.|
|CTRL + ALT + signe moins|Réduit le facteur de zoom d’un niveau.|
|CTRL + ALT + signe plus|Augmente le facteur de zoom d’un niveau.|
|Maj ou Ctrl|Ajoute l’objet au groupe de sélection. La touche Ctrl vous permet également de supprimer des objets individuellement du groupe de sélection.|
|Entrez|Exécute la commande par défaut pour l’objet (généralement Open ou Edit).|
|F2|Active la modification sur place pour l’objet.|
|Touches de direction|Déplace le ou les objets sélectionnés dans le sens de la touche de direction appuyée, par petits incréments (par exemple, 1 pixel à la fois)|
|CTRL + touches de direction|Déplace le ou les objets sélectionnés dans le sens de la touche de direction appuyée, en incréments plus larges (par exemple, 10 pixels à la fois)|
|Maj + touches de direction|Redimensionne le ou les objets sélectionnés dans la direction correspondante, par petits incréments (par exemple, 1 pixel à la fois)|
|Ctrl + Maj + touches de direction|Redimensionne le ou les objets sélectionnés dans le sens respectif, en incréments plus larges (par exemple, 10 pixels à la fois)|

 Lorsque les utilisateurs modifient les contrôles en place, il peut être judicieux que les objets se redimensionnent automatiquement avec l’entrée d’utilisateur. Par exemple, si l’utilisateur modifie un contrôle Label, l’étiquette doit croître pour afficher le texte que l’utilisateur vient de taper. Si ce n’est pas le cas, l’utilisateur doit redimensionner le contrôle manuellement après la modification du texte. Si l’utilisateur possède un grand nombre de contrôles, cela devient une tâche tâches répétitives et unproduction.

#### <a name="graphical-containers"></a>Conteneurs graphiques
 Dans certains cas, les éditeurs graphiques fournissent des conteneurs pour d’autres objets graphiques, tels que le contrôle de panneau Windows Forms ou le contrôle de disposition de grille dans le Concepteur HTML. Si votre éditeur fournit des conteneurs pour d’autres objets graphiques, le modèle de sélection suivant doit être utilisé uniquement pour le conteneur (les objets du conteneur suivent le modèle standard, comme décrit ci-dessus) :

|Entrée|Résultats|
|-----------|------------|
|Un simple clic sur le conteneur|Sélectionne l’objet conteneur sans sélectionner directement les objets qu’il contient. Le conteneur peut être déplacé et/ou redimensionné avec une entrée de souris et de clavier standard (comme décrit ci-dessus). Les objets contenus sont déplacés par rapport au conteneur, mais les objets contenus ne sont pas redimensionnés, sauf s’ils sont également directement sélectionnés.|
|Pointez sur la région des limites du conteneur|Convertit la souris en curseur de déplacement, indiquant que le conteneur peut être déplacé.|
|Faites glisser la région limite du conteneur|Remplace la souris par le curseur de déplacement et déplace le conteneur (et les objets contenus dans). Le conteneur ne peut pas être déplacé sans avoir préalablement sélectionné un seul clic.|
|Un simple clic sur un objet dans le conteneur|Désélectionne le conteneur (s’il est sélectionné) et sélectionne uniquement l’objet sur lequel vous avez cliqué.|
|Maj + clic ou Ctrl + clic sur un objet et/ou un conteneur contenu|Ajoute l’objet cliqué à un groupe de sélection ou de sélection existant. Si l’objet cliqué est déjà membre du groupe de sélection, il est supprimé du groupe de sélection.|

 Les objets contenus doivent adhérer au modèle de sélection de base comme décrit dans la section précédente. Du test de l’utilisation de Windows Forms Designer, les utilisateurs attendaient un accès transparent aux objets contenus sans étapes intermédiaires (imposées par l’objet de relation contenant-contenu).

#### <a name="disjoint-and-region-selections"></a>Sélections disjointes et régionales
 Les éditeurs d’objets graphiques doivent prendre en charge les sélections disjointes. Notez que ce graphique n’affiche pas l’apparence du contrôle pour Visual Studio. Consultez [apparence de la sélection d’objets graphiques](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) pour obtenir des spécifications visuelles détaillées.

 ![Sélecteurs de régions et disjoints](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Sélection disjointe**

 Les éditeurs graphiques doivent également fournir des sélections de régions avec un indicateur de sélection de type texte défilant. Si l’éditeur graphique prend en charge d’autres types d’objets (tels que du texte), les sélections de régions peuvent ne pas être possibles en fonction des contraintes de ces autres types d’objets.

 ![Sélection de texte défilant](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **Sélection de texte défilant**

#### <a name="primary-and-secondary-selections"></a>Sélections principales et secondaires
 Certains éditeurs d’objets graphiques permettent à l’utilisateur de modifier ou d’aligner des objets dans des groupes. Dans ce cas, le concept de sélections principales et secondaires doit être introduit. La sélection principale est l’objet auquel tous les autres objets répondent pour les opérations de groupe. L’objet que l’utilisateur sélectionne en premier devient le contrôle principal et les sélections suivantes deviennent les sélections secondaires. La sélection principale a un traitement visuel distinct de la ou des sélections secondaires pour indiquer l’objet principal :

 ![Sélection principale et secondaire](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **Sélection principale avec deux sélections secondaires**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a> Apparence de la sélection d’objets graphiques
 Les poignées de sélection sont des carrés dessinés dans un motif rectangulaire autour du cadre englobant de l’objet. Le graphique ci-dessous montre des exemples des différents États qu’un objet graphique peut avoir avec la poignée, le dimensionnement et l’apparence de modification sur place. La taille des handles doit être liée à la bordure de fenêtre et aux métriques de bord à l’aide de l’API **GetSystemMetrics** .

| État | Apparence | Détails visuels |
|-------------------------|---------------| - |
| **Non sélectionné** | Default | ![État du bouton par défaut](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState") |
| **Sélection principale** | Redimensionnable | ![Sélection principale avec des poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize") |
| **Sélection principale** | Non redimensionnable | ![Sélection principale sans poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize") |
| **Sélection principale** | Verrouillé | ![Sélection principale verrouillée](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked") |
| **Sélection secondaire** | Redimensionnable | ![Sélection secondaire avec des poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize") |
| **Sélection secondaire** | Non redimensionnable | ![Sélection secondaire sans poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize") |
| **Sélection secondaire** | Verrouillé | ![Sélection secondaire verrouillée](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked") |
| **Interface utilisateur active** | Default | ![État actif de l'interface utilisateur](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive") |

### <a name="view-selection-models"></a>Afficher les modèles de sélection

#### <a name="tree-view"></a>Arborescence
 La sélection dans une arborescence s’affiche avec une simple mise en surbrillance. Si l’utilisateur clique sur un nom de nœud ou sur une icône de nœud, le nœud est sélectionné. Les glyphes triangulaires à gauche du nœud développent ou contractent le contrôle d’arborescence, mais n’affectent pas la sélection de l’utilisateur, à une exception près : lors de la réduction d’un nœud parent lorsque la sélection est sur un enfant de ce nœud, la sélection se déplace vers le parent.

 ![Arborescence classique dans Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Arborescence classique dans Visual Studio**

 Les arborescences peuvent prendre en charge des sélections contiguës et disjointes, même sur plusieurs niveaux de l’arborescence. Les sélections multiples contiguës ou disjointes doivent être effectuées sur les nœuds d’arbre visibles. Si un nœud est réduit, la sélection disjointe est perdue et le nœud qui a été réduit obtient la sélection. De cette façon, l’utilisateur peut voir les nœuds qui seront affectés par une opération. Lorsque les nœuds sont réduits, les nœuds susceptibles d’être affectés ne sont pas effacés.

 Lorsqu’un nœud parent est sélectionné, l’opération doit s’appliquer au parent, bien qu’il puisse y avoir des cas où il est logique qu’une opération s’applique au parent et à tous ses enfants. Dans ce cas, fournissez une interface utilisateur supplémentaire pendant l’opération, par exemple une case à cocher ou une boîte de dialogue de confirmation pour rendre l’option « appliquer à tous les enfants » explicite à l’utilisateur.

##### <a name="renaming"></a>Renommage
 Si les nœuds de l’arborescence prennent en charge le changement de nom, le changement de nom doit être effectué sur place. L’opération sur place doit être la norme pour tous les contrôles d’arborescence dans Visual Studio. Fournissez une commande Rename qui active immédiatement le mode d’édition sur place, avec la sélection de texte couvrant le nom entier du nœud, prêt à accepter l’entrée utilisateur. Si le nœud représente un fichier, le nom de fichier doit contenir l’extension. La surbrillance de sélection doit inclure uniquement le corps du nom de fichier et non l’extension.

|Entrée|Résultats|
|-----------|------------|
|Entrée (touche)|Valide l’opération de changement de nom|
|Touche Échap|Annule l’opération de changement de nom|
|Cliquer en dehors de la zone d’édition sur place|Valide l’opération de changement de nom|
|Annuler|Fournir une annulation facile pour annuler l’opération de changement de nom|

#### <a name="selection-within-lists-and-grid-controls"></a>Sélection dans des listes et des contrôles de grille
 Le concept clé dans la sélection de liste est qu’il est basé sur les lignes, ce qui signifie que lorsqu’une sélection est effectuée, la ligne entière est sélectionnée en tant qu’unité. En revanche, les grilles peuvent permettre la sélection de cellules spécifiques sans affecter les autres aspects de la ligne. Les grilles peuvent également contenir une hiérarchie de lignes imbriquées (par exemple, dans un contrôle TreeGrid) qui permettent de sélectionner et désélectionner des branches entières de la hiérarchie en interagissant avec les lignes parentes. La sélection dans les listes est indiquée par une simple couleur de surbrillance sur l’intégralité de la ligne de données. Le focus est représenté par une bordure en pointillés d’un pixel autour de la ligne ou de la cellule modifiable en cours (ligne si toutes les cellules sont en lecture seule).

> [!NOTE]
> **Le focus** et la **sélection** sont des concepts différents. *Le focus* est une indication de l’élément d’interface utilisateur ciblé pour recevoir l’entrée qui n’est pas explicitement dirigée vers un autre objet, tandis que la *sélection* fait référence à l’état de l’inclusion d’un objet dans un ensemble d’objets sur lesquels des opérations ultérieures peuvent avoir lieu.

 Les sélections dans les listes peuvent être contiguës, disjointes ou régionales. Lorsque plusieurs sélections sont autorisées, la sélection contiguë et disjointe doit toujours être prise en charge, tandis que la prise en charge des sélections de région (zone) est facultative. Les sélections de régions sont lancées en faisant glisser l’espace blanc du corps de la liste.

| Object | Sélection |
|--------|------------|
| List | Contiguë |
| List | Disjoint |
| List | Région |

 Cliquez une fois sur une liste pour sélectionner la ligne où le clic s’est produit. Si l’utilisateur clique dans une cellule de liste qui prend en charge la modification sur place, la cellule est également immédiatement activée pour la modification sur place. Dans le cas contraire, la ligne entière est immédiatement sélectionnée et montre une mise en surbrillance.

 Le glissement dans le corps de la liste effectue l’une des trois opérations suivantes :

- Lance une sélection de zone si la liste la prend en charge et que la souris est entourée d’un espace blanc

- Lance une opération de glisser-déplacer si la cellule ou la ligne de liste prend en charge une source de glissement

- Sélectionne la ligne actuelle

##### <a name="in-place-editing"></a>Modification sur place
 Lorsque la modification sur place est autorisée, il existe deux modèles de base : le contrôle d’édition simple et le sélecteur de propriétés. Avec un contrôle d’édition simple, le contenu est mis en surbrillance et prêt pour l’entrée d’utilisateur dès que la modification sur place est activée. Lorsqu’un sélecteur de propriétés est implémenté, le bouton qui appelle le sélecteur de propriétés s’affiche une fois que le mode d’édition sur place est activé et que la sélection actuelle n’est pas mise en surbrillance. Le bouton du sélecteur doit être justifié à droite dans la cellule. Pour obtenir des exemples d’édition sur place, consultez la **fenêtre Propriétés** et **liste des tâches** dans Visual Studio.

##### <a name="keyboard-support"></a>Prise en charge du clavier
 La prise en charge du clavier pour la sélection dans les listes et les grilles suit les conventions Windows standard :

- Les touches de direction parcourent la liste, en sélectionnant chaque ligne/cellule au fur et à mesure que le focus est déplacé.

- Maj + Flèche effectue une sélection contiguë dans le sens des touches de direction.

- Ctrl + flèche suivi d’une barre d’espace permet de basculer entre l’ajout et la suppression d’éléments de liste dans la sélection, ce qui crée une sélection disjointe.

- Pour les grilles qui contiennent des hiérarchies imbriquées, la touche de direction droite développe une ligne parente et la touche de direction gauche réduit une ligne.

- La touche Tab déplace le focus entre les cellules de la ligne actuelle si les cellules sont modifiables.

- La touche entrée exécute la commande par défaut sur l’élément dans la liste (souvent **ouverte**).

- La touche F2 active la modification sur place pour la cellule actuellement sélectionnée.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a> Persistance et enregistrement des paramètres

### <a name="overview"></a>Vue d’ensemble
 Bien que chaque composant logiciel dans Visual Studio soit généralement responsable de son propre État et de sa persistance, Visual Studio enregistre automatiquement les paramètres dans certains cas, par exemple avec les tailles et les positions des fenêtres. Le tableau ci-dessous est une combinaison de paramètres enregistrés automatiquement et des paramètres qui nécessitent un utilisateur explicite ou une action programmée à entreprendre.

|Object|Éléments à enregistrer|Quand enregistrer|Emplacement d’enregistrement|
|------------|------------------|------------------|-------------------|
|Objet sélectionnable (par exemple, une ligne de code)|Point d’arrêt sur une ligne de code<br /><br /> Raccourci utilisateur associé à la ligne de code|Lors de l’enregistrement du projet|Fichier d' **options utilisateur (. suo)** pour le projet|
|Boîte de dialogue|Emplacement de la boîte de dialogue, si elle a été déplacée<br /><br /> Affichage que l’utilisateur a utilisé en dernier dans la boîte de dialogue|Quand la boîte de dialogue se ferme<br /><br /> À la fin de la session Visual Studio|En mémoire<br /><br /> Registre dans **HKEY_CURRENT_USER**|
|Fenêtre|La taille et l’emplacement de la fenêtre|Quand la fenêtre se ferme<br /><br /> En cas de modification du mode Visual Studio<br /><br /> À la fin de la session Visual Studio|Fichier d' **options utilisateur (. suo)** pour le projet<br /><br /> Fichier d’options personnalisées pour les paramètres de fenêtre|
|Document|Sélection actuelle dans le document<br /><br /> Vue du document<br /><br /> Les derniers emplacements visités par l’utilisateur|Lors de l’enregistrement du document|Fichier d' **options utilisateur (. suo)** pour le projet|
|Project|Références aux fichiers<br /><br /> Références aux répertoires sur le disque<br /><br /> Références à d’autres logiciels<br /><br /> Composants<br /><br /> Informations d’État sur le projet lui-même|Lors de l’enregistrement du projet|Fichier projet|
|Solution|Références aux projets<br /><br /> Références aux fichiers|Lors de l’enregistrement du projet ou de la solution|Fichier **solution (. sln)**|
|Paramètres dans **outils > options**|Personnalisations du clavier<br /><br /> Personnalisations de la barre d’outils<br /><br /> Modèles de couleurs|Quand la boîte de dialogue **outils > options** se ferme<br /><br /> À la fin de la session Visual Studio|Registre dans **HKEY_CURRENT_USER**|

 Ce que fait l’utilisateur et quand il le fait, détermine si un paramètre est enregistré en mémoire (pendant la session), enregistré sur le disque (entre les sessions en tant que paramètre de registre), dans le cadre du fichier de projet ou de solution lui-même, dans le cadre du fichier des **options de solution (.** Le tableau ci-dessus montre plusieurs événements auxquels les paramètres peuvent être enregistrés. Toutefois, il existe d’autres cas dans lesquels vous pouvez souhaiter enregistrer l’État :

- Quand l’utilisateur change d’emplacement dans une boîte de dialogue ou une fenêtre

- Lorsque l’utilisateur transfère le focus vers une autre fenêtre

- Quand l’utilisateur passe du mode conception au mode débogage

- Quand l’utilisateur ferme son compte

- Lorsque l’ordinateur passe en veille prolongée ou s’arrête

- Lorsque l’ordinateur/disque dur va être reformaté et reconfiguré

### <a name="window-configurations"></a>Configurations de fenêtres
 La configuration d’une fenêtre est la présentation de base de l’environnement de développement. il s’agit d’un schéma qui se compose de la liste des fenêtres outil présentes et de la façon dont elles sont organisées. Pour Windows géré par l’IDE (Windows IDE), les informations de disposition sont conservées par utilisateur. par conséquent, quand un utilisateur lance l’IDE, la disposition de la fenêtre s’affiche de la même manière qu’à la dernière sortie de Visual Studio. L’État et la position des fenêtres de l’IDE sont conservées dans un fichier d’options personnalisé au format XML. Les fenêtres outil créées par des packages chargés dans l’IDE rendent leurs informations d’État persistantes dans le registre et peuvent ou non être par utilisateur.

#### <a name="profile-specific-layouts"></a>Dispositions spécifiques au profil
 Chaque profil comprend des dispositions de fenêtres outil, organisées de manière familière à des personnes de développeur spécifiques (Visual C++ les développeurs s’attendent à voir le **Explorateur de solutions** sur le côté gauche de l’IDE, tandis que les développeurs C# s’attendent à voir le **Explorateur de solutions** à droite). Les dispositions de fenêtres spécifiques au profil sont chargées une fois que l’utilisateur a choisi un profil au démarrage. Un auteur de package doit déterminer la disposition de fenêtre qui convient le mieux à l’expérience de son client, sachant que les modifications apportées par l’utilisateur à la configuration de la fenêtre seront conservées.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a> Entrée tactile
 Les utilisateurs utilisent de plus en plus des produits de développement Microsoft sur des appareils tactiles. Toutefois, il existe des barrières qui compliquent l’utilisation des outils de développement sur des appareils tactiles. Les utilisateurs s’attendent à ce que nos produits fournissent une expérience tactile fiable et précise. L’objectif de ces instructions est d’informer les décisions concernant les fonctionnalités tactiles à incorporer et d’encourager une expérience tactile cohérente sur Visual Studio et les produits associés.

### <a name="levels-of-experience"></a>Niveaux d’expérience
 Les niveaux d’expérience suivants sont destinés à servir de guide pour aider les équipes à déterminer les fonctionnalités tactiles à proposer en fonction de leur niveau d’intérêt d’investissement souhaité.

- L' **expérience de base** est destinée aux équipes qui souhaitent fournir des fonctionnalités tactiles afin qu’il n’y ait pas de fin mort tout au long de leur travail.

- L' **expérience optimisée** est destinée aux équipes qui souhaitent fournir les fonctionnalités tactiles les plus courantes (par exemple, celles généralement disponibles dans les applications de navigateur Internet).

- L' **expérience élevée** est destinée aux équipes qui souhaitent ajouter des fonctionnalités telles que les gestes ou d’autres fonctionnalités facultatives qui peuvent rendre leur application tactile pour la première fois.

||Expérience de base|Expérience optimisée|Expérience élevée|
|-|----------------------|--------------------------|-------------------------|
|**Permet aux utilisateurs de...**|Correction du code et de la solution/de la lecture au niveau du projet sans les fins mortes|Effectuer des tâches de maintenance, de refactorisation et de navigation|Travaillez dans une expérience cohérente, intuitive et fluide en toute confiance|
|**Éditeur**|Panoramique tactile et sélection<br /><br /> Touche de défilement pour sauter et appuyer sur + glisser|Zoom de pince<br /><br /> Défilement rapide<br /><br /> Sélection<br /><br /> Utilisation facile du menu contextuel||
|**Fenêtres d’outils principales**|Afficher le panorama<br /><br /> Sélection d’élément<br /><br /> Touche de défilement pour sauter et appuyer sur + glisser|Défilement et sélection faciles des éléments||
|**Fenêtrage**||Redimensionner la fenêtre<br /><br /> Accès rapide||
|**Barre d’outils document**||Navigation facile entre les fichiers ouverts||
|**Mouvements**||S’assurer que les gestes courants fonctionnent dans l’IDE|Actions basées sur des mouvements<br /><br /> Prise en charge du glisser-déplacer et des concepteurs|
|**Autres points à considérer**|||Clavier personnalisé à l’écran|

#### <a name="gestures"></a>Mouvements
 Les gestes fournissent aux utilisateurs un raccourci vers des commandes qui, sans cela, nécessitent une interaction plus complexe. Reportez-vous aux instructions Windows sur les [gestes tactiles courants pour les applications de bureau](/windows/desktop/wintouch/windows-touch-gestures-overview)et suivez ces instructions pour la plupart des gestes, y compris les gestes simples tels que le panoramique et le zoom.
