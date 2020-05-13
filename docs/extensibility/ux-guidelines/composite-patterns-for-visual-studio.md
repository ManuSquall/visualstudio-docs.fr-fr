---
title: Modèles composites pour Studio Visuel (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 500ea8ffe7c33c1d747590ea074bff43fa1a3ab3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698617"
---
# <a name="composite-patterns-for-visual-studio"></a>Modèles composites pour Visual Studio
Les modèles composites combinent des éléments d’interaction et de conception dans des configurations distinctes. Voici quelques-uns des modèles composites les plus importants de Visual Studio en ce qui concerne la cohérence :

- [Visualisation des données](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [L’interface utilisateur sur l’objet et le regard](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Modèles de sélection](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Paramètres de persistance et d’enregistrement](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Entrée tactile](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a>Visualisation des données

### <a name="overview"></a>Vue d'ensemble
 Les graphiques sont un moyen visuel d’agréger et de visualiser les données afin d’améliorer la prise de décision. Ils peuvent aider les utilisateurs confrontés à beaucoup de données, mais peu de sens voir ce qui mérite l’attention et ce qui pourrait avoir besoin d’une action.

 L’utilisateur bénéficiera d’un graphique si l’une des conditions suivantes est vraie :

- Le graphique aidera-t-il les utilisateurs à identifier les tâches sur laquelle ils peuvent agir ?

- Le graphique permettra-t-il aux utilisateurs de prévoir les conséquences des changements potentiels ?

- Le graphique aidera-t-il les utilisateurs à découvrir les tendances et à identifier les modèles ?

- Le graphique permettra-t-il aux utilisateurs de prendre de meilleures décisions ?

- Le graphique aidera-t-il à répondre à une question spécifique que les utilisateurs peuvent avoir dans le contexte donné ?

#### <a name="general-rules-for-charts"></a>Règles générales pour les graphiques

- Étiquetez clairement les données. Illustrations sans explication sont juste de jolies images.

- Démarrer les haches à zéro pour éviter de biaiser les proportions. La longueur de la ligne et la taille de la barre sont des repères visuels importants pour comprendre les relations entre les points de données.

- Créez des graphiques, pas des infographies. Les infographies sont des représentations artistiques des données, et leur objectif principal est la narration visuelle. Les graphiques peuvent (et doivent) être visuellement attrayants, mais laissez les données parler d’elles-mêmes.

- Évitez le skeumorphisme, les graphiques à barres picturales, les hashmarks de contraste et d’autres touches infographic.

- N’utilisez pas les effets 3D comme élément décoratif. Utilisez-les uniquement s’ils font vraiment partie intégrante de la capacité de l’utilisateur à comprendre l’information.

- Évitez d’utiliser plusieurs lignes et remplissages, car plus de deux couleurs peuvent rendre ce type de graphique difficile à lire et à interpréter correctement.

- N’utilisez pas un graphique (ou une illustration) comme seul moyen de comprendre un concept ou d’interagir avec les données. Cela présente des difficultés pour les utilisateurs ayant une déficience visuelle.

- N’utilisez pas de graphiques comme éléments gratuits ou décoratifs sur une page. En d’autres termes, si un graphique n’ajoute aucune valeur ou n’aide pas les utilisateurs à résoudre un problème, ne l’utilisez pas.

### <a name="chart-types"></a>Types de graphiques
 Les types de graphiques utilisés dans Visual Studio comprennent les graphiques à barres, les graphiques en ligne, un graphique à secteurs modifié connu sous le nom de graphique à anneaux ou « carte de beignet », les chronologies, les parcelles de dispersion (également appelées « graphiques à grappes ») et les graphiques Gantt. Chaque type de graphique est utile pour communiquer un type d’information différent.

### <a name="other-charting-considerations"></a>Autres considérations de cartographie

#### <a name="color"></a>Couleur
 Il existe une palette spécifique de couleurs de cartographie définies pour une utilisation dans Visual Studio. La palette est accessible pour les principaux types de daltonisme, et les couleurs peuvent être différenciées même lorsqu’elles sont utilisées comme tranches de couleur très étroites. Vous pouvez utiliser ces couleurs dans n’importe quelle combinaison pour n’importe quel type de graphique ou graphique dans votre interface utilisateur. Vous n’avez pas besoin d’utiliser les sept couleurs si vous n’avez pas besoin que de nombreuses couleurs distinctes. Ces couleurs n’ont pas été conçues pour être utilisées avec des éléments de premier plan, donc ne placez pas de texte ou de glyphes sur le dessus de ces couleurs. Ces teintes doivent être codées et exposées à la personnalisation de l’utilisateur sous **Tools > Options** (voir couleurs [exposantes pour les utilisateurs finaux](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).

|Swatch|Hex|RGB|
|------------|---------|---------|
|![Échantillon 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|
|![Échantillon BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|
|![Échantillon FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|
|![Échantillon 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|
|![Échantillon 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|
|![Échantillon 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|
|![Échantillon B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a>L’interface utilisateur sur l’objet et le regard
 Cette section donne un contexte à l’aperçu, également connu sous le nom de vue d’aperçu du code, un type d’interface utilisateur sur l’objet unique à Visual Studio.

### <a name="overview"></a>Vue d'ensemble

- L’interface utilisateur sur l’objet devrait donner à l’utilisateur plus d’informations ou d’interactivité sans nuire à sa tâche principale.

- Le modèle principal pour l’interface utilisateur sur l’objet dans Visual Studio est connu comme "information au point d’attention."

- L’interface utilisateur sur objet dans Visual Studio est soit en ligne, soit flottante et durable ou transitoire.

  - La vue d’aperçu du code, un type d’interface utilisateur sur objet dans Visual Studio, est en ligne et durable.

  - CodeLens, un type d’interface utilisateur sur objet dans Visual Studio, flotte et transitoire

  Comprendre comment fonctionne un morceau de code, ou trouver des détails sur ce code, nécessite souvent un développeur de changer de contexte et d’aller à d’autres contenus ou une autre fenêtre. Ces changements de contexte peuvent être perturbateurs, car les utilisateurs peuvent perdre l’accent sur leur tâche initiale s’ils quittent leur fenêtre principale. En outre, obtenir ce contexte d’origine de retour peut être difficile, surtout si la commutation des fenêtres a causé leur code d’origine d’être obscurci par d’autres interfaces utilisateur.

  L’interface utilisateur sur objet suit un modèle appelé « information au point d’attention ». Ces messages, fenêtres contexturées et boîtes de dialogue donnent aux utilisateurs des informations supplémentaires et pertinentes qui ajoutent des éclaircissements ou de l’interactivité sans perdre l’accent sur leur tâche principale. Des exemples d’interface utilisateur sur objet incluent des fenêtres pop-up qui apparaissent lorsqu’un utilisateur plane sur un pointeur sur une icône dans la zone de notification, le mouvement rouge sous un mot mal orthographié, et la vue d’oeil introduite dans Visual Studio 2013.

### <a name="decision-points"></a>Points de décision
 Au sein de Visual Studio, il existe plusieurs façons d’utiliser ce modèle d’information au point d’attention. Le choix du bon mécanisme et sa mise en œuvre d’une manière cohérente et prévisible sont essentiels à l’expérience globale. Dans le cas contraire, les utilisateurs pourraient être présentés avec une expérience déroutante ou incohérente qui nuit à se concentrer sur le contenu lui-même.

#### <a name="relationships-between-master-and-detail-content"></a>Relations entre le contenu maître et le contenu détaillé
 Les informations au point d’attention sont utilisées pour afficher une relation entre le contenu sur lequel l’utilisateur se concentre (le contenu « maître ») et le contenu connexe supplémentaire (le contenu « détaillé »). Dans ce modèle, le contenu détaillé est clairement lié au contenu avec lequel l’utilisateur travaille et peut être affiché à proximité du contenu principal. Les informations supplémentaires ou les informations qui ne peuvent pas être résumées sans accabler le contenu principal doivent suivre un autre modèle, comme une fenêtre d’outil.

- **Affichez toujours** le contenu détaillé à proximité du contenu principal.

- **Assurez-vous toujours** que le contenu détaillé permet toujours à un utilisateur de rester concentré sur le contenu principal. Souvent, la meilleure façon d’y parvenir est de rendre le contenu détaillé aussi proche que possible du contenu principal. Cela peut être fait en rendant le contenu détaillé dans une fenêtre pop-up à côté du contenu maître, ou en rendant le contenu détaillé en ligne sous le contenu principal.

- **N’utilisez jamais** d’informations au point d’attention qui éloigne l’utilisateur du contenu principal. Si les utilisateurs ont besoin de visualiser le contenu détaillé séparément, exposez une action explicite qui permet à l’utilisateur de le faire.

#### <a name="design-details"></a>Détails de conception
 Une fois que vous avez déterminé que l’interface utilisateur sur l’objet est le bon choix, il ya quatre considérations de conception principales:

1. **Persistance :** le contenu devrait-il être durable ou transitoire ?
   Les utilisateurs voudront-ils garder les informations visibles pour se référer ou interagir avec? Ou les utilisateurs voudront-ils rapidement jeter un coup d’œil à l’information et ensuite continuer avec leur tâche principale?

2. **Type de contenu :** le contenu sera-t-il informationnel, exploitable ou navigationnel ?
   L’utilisateur a-t-il besoin de détails supplémentaires sur le contenu du maître ? L’utilisateur doit-il accomplir une tâche qui affecte le contenu principal ? Ou l’utilisateur doit-il être dirigé vers une autre ressource ?

3. **Type d’indicateur :** un indicateur ambiant a-t-il un sens ?
   L’information peut-elle être résumée de manière utile et affichée sans accabler le contenu principal ?

4. **Gestes :** quels gestes seront utilisés pour invoquer et rejeter l’interface utilisateur ?
   Comment l’utilisateur va-t-il mettre en place le contenu des détails et l’envoyer ? Est-il utile d’ajouter un geste comme l’épinglage pour passer d’un état transitoire à un état durable?

   Chacun de ces quatre points de décision aura un impact sur les principales composantes de l’interface utilisateur sur l’objet.

### <a name="on-object-ui-components"></a>Composants d’interface utilisateur sur objet

1. Type de conteneur (présentateur de contenu)

    - Virgule flottante

    - En ligne

2. Type de contenu

    - Informationnel : données qui peuvent être statiques ou dynamiques

    - Actionnable : commandes qui modifient le contenu principal

    - Navigation : liens qui adviment l’utilisateur vers une autre fenêtre ou une autre application, comme MSDN

3. Mouvements

    - Invocation

    - Licenciement

    - Épinglage

    - Autres interactions

4. Modèle de persistance et d’engagement

    - Temporaire

    - Durable

    - Automatique

    - À la demande

5. Indicateurs ambiants (facultatif)

    - Squiggle souligner

    - Icône intelligente de tag

    - Autres indicateurs ambiants

#### <a name="container-content-presenter-type"></a>Type de conteneur (présentateur de contenu)
 Il existe deux options majeures disponibles pour présenter le contenu au point d’attention :

1. **Inline:** un présentateur en ligne, comme la vue d’oeil qui a été introduit dans le Visual Studio 2013 Code Editor, fait de l’espace pour de nouveaux contenus en déplaçant le contenu existant.

    - **Préférez les** présentateurs en ligne si vous vous attendez à ce que les utilisateurs veuillent passer beaucoup de temps à se référer ou à interagir avec le contenu que vous présentez.

    - **Évitez les** présentateurs en ligne si vous vous attendez à ce que les utilisateurs voudront jeter un coup d’œil à l’information que vous présentez, puis continuer avec leur tâche principale avec un minimum de perturbation.

2. **Flottant :** un présentateur flottant est positionné le plus près possible du contenu sélectionné, mais ne modifie pas la mise en page du contenu existant. Diverses stratégies peuvent être utilisées, telles que l’affichage d’un panneau de contenu flottant sur l’espace blanc disponible le plus proche du symbole sélectionné.

    - **Préférez les** présentateurs flottants si vous vous attendez à ce que les utilisateurs voudront jeter un coup d’œil à l’information que vous présentez, puis continuer avec leur tâche principale avec un minimum de perturbation.

    - **Évitez les** présentateurs flottants si vous vous attendez à ce que les utilisateurs veuillent passer beaucoup de temps à se référer ou à interagir avec le contenu que vous présentez.

#### <a name="content-type"></a>Type de contenu
 Il existe trois principaux types de contenu qui peuvent être affichés à l’intérieur de n’importe quel conteneur d’interface utilisateur sur l’objet. Toute combinaison de ces types d’informations peut être montrée. Les trois types sont les :

1. **Informations :** la plupart des conteneurs d’interface utilisateur sur l’objet afficheront une sorte de contenu d’information. Le contenu peut représenter des informations sur l’état actuel de l’environnement ou il peut représenter des informations sur un état futur potentiel de l’environnement. Par exemple, il pourrait être utilisé pour montrer l’effet d’une commande particulière, comme une refactoration, sur le code existant.

    - **Utilisez toujours** la représentation canonique des informations que vous affichez. Par exemple, le code doit ressembler à du code, avec mise en évidence de la syntaxe, et doit respecter les paramètres de police et d’autres paramètres de l’environnement que l’utilisateur a définis.

    - **Envisagez toujours** de prendre en charge toute action sur le contenu d’information qui serait possible si ces mêmes informations sont présentées comme du contenu maître. Par exemple, si vous présentez du code existant à l’intérieur d’un conteneur d’interface utilisateur sur objet, envisagez fortement de prendre en charge la possibilité de naviguer et de modifier ce code.

    - **Envisagez toujours** d’utiliser une couleur de fond différente si vous présentez du contenu d’information qui représente un état futur potentiel.

2. Actionnable : certains conteneurs d’interface utilisateur sur l’objet permettront d’effectuer une action sur le contenu principal, comme l’exécution d’une opération de refactoration.

    - **Positionnez toujours** les commandes exploitables séparément du contenu d’information.

    - **Activez** et désactivez toujours les actions le cas échéant.

    - **Consultez toujours** les lignes directrices standard pour représenter les commandes à l’intérieur des boîtes de dialogue.

    - **Maintenez toujours** le nombre d’actions exposées dans un conteneur d’interface utilisateur sur l’objet à un minimum absolu. Interagir avec l’interface utilisateur sur l’objet devrait être une expérience légère et rapide. L’utilisateur ne devrait pas avoir à dépenser de l’énergie sur la gestion du conteneur d’interface utilisateur sur l’objet lui-même.

    - **Considérez toujours** comment et quand un conteneur d’assurance-chômage sur l’objet sera fermé ou rejeté. Comme meilleure pratique, toute action qui conclut le dialogue entre le maître et le contenu détaillé devrait également fermer le conteneur d’interface utilisateur sur l’objet lorsque cette action est invoquée.

3. **Navigation :** certains conteneurs d’interface utilisateur sur l’objet incluent des liens qui auent l’utilisateur vers une autre fenêtre ou une autre application, comme l’ouverture d’un article MSDN dans le navigateur Web de l’utilisateur.

    - **Toujours** prépendez n’importe quel lien de navigation avec "Open" de sorte que les utilisateurs ne seront pas surpris d’être navigué vers un autre contenu.

    - **Séparez toujours** les liens de navigation des liens exploitables.

#### <a name="ambient-indicators-optional"></a>Indicateurs ambiants (facultatif)
 Les indicateurs ambiants peuvent être subtils, y compris le texte présenté dans une couleur contrastante du reste du code, ou évident, y compris les symboles chatouilleux tels que les souligne de gribouillis et les icônes intelligentes de tag. Les indicateurs ambiants communiquent la disponibilité d’informations supplémentaires et pertinentes. Idéalement, ils fournissent des informations utiles, même sans exiger de l’utilisateur d’interagir avec eux.

- **Toujours** positionner un indicateur ambiant de sorte qu’il ne distrait pas ou ne submerge pas l’utilisateur. S’il est impossible de positionner un indicateur ambiant de cette manière, envisager une autre solution.

- **Toujours** positionner l’indicateur ambiant aussi proche que possible du contenu qu’il est lié à.

- **Essayez toujours** de créer un indicateur qui résume l’information qu’il met à disposition. Envisagez de fournir un compte-compte du nombre d’éléments de données disponibles (par exemple, « 3 références » au lieu de simplement « Références ») ou pensez à une autre façon de résumer les données.

  - Dans les cas où les données d’un indicateur ne peuvent pas toujours être calculées et affichées, envisagez immédiatement de fournir une rétroaction progressive au fur et à mesure que les valeurs sont calculées. Par exemple, envisagez d’animer les modifications qui reflètent les mises à jour des données disponibles, semblables à la façon dont la tuile en direct sur Windows Phone se rafraîchit à mesure que le nombre d’e-mails non lus augmente.

- **N’ajoutez jamais** plus d’indicateurs qu’un utilisateur ne peut raisonnablement prendre pour un morceau donné de contenu. Les indicateurs ambiants doivent être utiles sans nécessiter d’interaction de la part de l’utilisateur. Les indicateurs perdent leur ambiance s’ils ont besoin de débordement et d’autres contrôles de gestion pour les mettre en vue.

#### <a name="gestures"></a>Mouvements
 Un aspect clé de permettre à l’utilisateur de maintenir l’accent sur le contenu principal est en soutenant les bons gestes pour ouvrir et rejeter le contenu détaillé supplémentaire.

- **Exigez toujours** que l’utilisateur effectue un geste explicite pour ouvrir le contenu supplémentaire. Les gestes ouverts courants comprennent :

  - **Hover :** outils ou contenu d’information non interactif

  - **Commande explicite :** présentateur en ligne

  - **Double clic de l’indicateur ambiant :** Fenêtre pop-up CodeLens

- **Rejetez toujours** le contenu du détail chaque fois que l’utilisateur appuie sur la touche Esc.

- **Tenez toujours** compte du contexte de l’interface utilisateur sur l’objet. Pour les présentateurs de contenu qui permettent l’interaction à l’intérieur du conteneur, examinez attentivement s’il faut afficher des informations supplémentaires sur le vol stationnaire, ce qui est susceptible d’être perturbateur pour le flux de travail de l’utilisateur.

- **N’affichez jamais de** contenu sur le plan plan stationnaire qui semble être modifiable ou invite à l’interaction utilisateur. Ce comportement peut frustrer les utilisateurs s’ils essaient de déplacer le curseur sur le contenu de détail, comme le comportement standard pour un tooltip est de rejeter immédiatement lorsque le curseur n’est plus sur le contenu maître qui l’a produit.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a>Modèles de sélection

### <a name="overview"></a>Vue d'ensemble
 Un modèle de sélection est le mécanisme utilisé pour indiquer et confirmer les opérations sur un ou plusieurs objets d’intérêt au sein de l’interface utilisateur. Ce sujet traite des modèles d’interaction de sélection au sein des éditeurs de documents Visual Studio : éditeurs de texte, surfaces de conception et surfaces de modélisation.

 Les utilisateurs doivent avoir un moyen d’indiquer à Visual Studio ce sur quoi ils travaillent, et Visual Studio doit répondre de façon prévisible avec des commentaires aux utilisateurs sur ce qu’il fonctionne sur. Les différences ou une mauvaise communication entre l’utilisateur et l’interface utilisateur peuvent faire en sorte que l’utilisateur ne s’en amarie pas à une action, ce qui peut avoir des conséquences imprévues. Souvent, l’erreur passe inaperçue jusqu’à ce que l’utilisateur voit que quelque chose manque ou a changé. Les modèles de sélection sont donc l’une des pièces les plus critiques de la conception de l’interface utilisateur. Bien que les modèles de sélection dans Visual Studio sont compatibles avec Windows, il ya de légères variations.

 Dans Visual Studio, comme dans Windows, les modèles de sélection diffèrent selon le contexte dans lequel l’interaction se produit. Les sélections peuvent se faire dans quatre types d’objets :

- Texte

- Objets graphiques

- Listes et arbres

- Grilles

  Dans ces objets, il existe trois types de sélections :

- Contiguë

- Disjoint

- Région

#### <a name="scope"></a>Étendue
 L’élément le plus important de la sélection est de s’assurer que l’utilisateur sait dans quelle fenêtre il travaille (activation) et où l’accent est situé (sélection). Visual Studio étend la fonctionnalité de gestion des fenêtres dans Windows, mais le schéma d’activation est le même: interagir avec une fenêtre apporte la mise au point à la fenêtre. Visual Studio dispose de deux indicateurs d’activation : l’un pour les fenêtres de documents et l’autre pour les fenêtres d’outils.

 Pour les fenêtres de document, la fenêtre active est indiquée par un onglet de fenêtre de document venant à l’avant et changeant sa couleur de fond :

 ![Sélection de l'onglet actif dans Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **Sélection active de l’onglet**

 Pour les fenêtres d’outils, la fenêtre active est indiquée par un changement de couleur de la zone de barre de titre de la fenêtre d’outil :

 ![Sélection de la fenêtre Outil active dans Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **Fenêtre d’outil active affichant la sélection primaire d’un nœud**

 ![Sélection de la fenêtre Outil inactive dans Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Fenêtre d’outil inactive, montrant la sélection latente du nœud**

 Une fois qu’une fenêtre est active, son objectif est indiqué selon les modèles de sélection décrits dans cette section des lignes directrices.

#### <a name="context"></a>Context
 Visual Studio a été conçu pour conserver un concept de contexte solide, en gardant une trace de l’endroit où l’utilisateur travaille. Une seule fenêtre est active, qu’il s’agisse d’un outil ou d’une fenêtre de document. Cependant, la fenêtre de document la plus haute conserve toujours une sélection latente. Bien que l’accent puisse être mis sur une fenêtre d’outil, la fenêtre de document qui a été la dernière active affiche une sélection, même dans un état inactif. Ceci est fait pour conserver le contexte de l’utilisateur dans le document qu’ils éditaient, ce qui montre que Visual Studio a conservé son état afin qu’il puisse revenir et passer de manière transparente entre les fenêtres d’outils et les fenêtres de documents.

### <a name="text-selection"></a>Sélection de texte
 Les éditeurs de Visual Studio qui sont strictement textuels, tels que l’éditeur de texte intégré, utilisent le même modèle de sélection de texte et l’apparence décrite dans la page [Mouse and Pointers](/windows/desktop/uxguide/inter-mouse) des lignes directrices d’interaction de l’expérience utilisateur de Windows sur MSDN. L’accent sur l’entrée dans l’éditeur de texte est indiqué par une barre verticale appelée le point d’insertion. Le point d’insertion est un pixel unique d’épaisseur et coloré comme l’inverse de tout ce qui apparaît derrière elle. Il clignote en fonction du taux fixé par le réglage du **taux de clignotement Cursor** dans l’onglet **Vitesse** de la pomme **de clavier** dans le panneau de contrôle.

#### <a name="contiguous-and-disjoint-selection"></a>Sélection contigue et décousue
 La sélection au sein de l’éditeur de texte est contigu seulement. Les sélections de textes disjoints ne sont pas autorisées, mais doivent être abordées dans les éditeurs d’objets graphiques. Lorsque le pointeur de souris de l’utilisateur est au-dessus d’une zone de texte, le curseur change à un I-faisceau. Un seul clic place le point d’insertion dans l’éditeur de texte à l’emplacement du clic. Tenir le bouton de la souris vers le bas commence un point culminant de sélection et la libération du bouton de la souris termine le point culminant de sélection.

#### <a name="region-selection-box-selection"></a>Sélection de la région (sélection de la boîte)
 Visual Studio prend en charge les sélections de régions dans l’éditeur de texte, et c’est ce qu’on appelle la sélection de la boîte. La sélection de la boîte permet à l’utilisateur de sélectionner une région de texte qui ne suit pas le flux texte régulier. Comme pour la sélection de texte standard, la sélection doit être contigu. La sélection de la boîte est initiée en maintenant la clé Alt tout en traînant avec la souris. La sélection des boîtes peut également être initiée en maintenant les touches Alt et Shift tout en utilisant les touches fléchées pour indiquer la région de sélection. La sélection de la boîte utilise le point culminant de sélection normal et montre le curseur de point d’insertion clignotant à la fin de la zone de sélection.

 ![Sélection régionale&#41; boîte &#40;dans Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Sélection de la région (boîte) en Visual Studio**

#### <a name="text-selection-appearance"></a>Apparence de sélection de texte
 Les couleurs utilisées pour la sélection active et inactive dans l’éditeur peuvent être personnalisées. Pour personnaliser l’apparence visuelle de l’éditeur, un utilisateur peut aller à **Tools > Options**, puis regarder sous Environnement > **Fonts et Couleurs > Éditeur de texte**.

### <a name="graphical-selection"></a>Sélection graphique

#### <a name="interaction"></a>Interaction
 La sélection d’objets graphiques peut être complexe et dépend d’un certain nombre de facteurs :

- **Le modèle de sélection principal de l’éditeur.** Les éditeurs qui contiennent des objets graphiques peuvent également être utilisés pour modifier du texte ou des grilles. Par exemple, l’éditeur peut être un éditeur basé sur le texte qui prend également en charge le placement d’objets graphiques, tels que le concepteur Visual Studio XAML. Prendre en charge plusieurs types d’objets peut affecter la façon dont l’utilisateur sélectionne des groupes constitués de différents types d’objets.

- **Soutien aux états de sélection primaire et secondaire.** Un éditeur peut fournir des états de sélection primaire et secondaire afin que les objets puissent être édités à l’unisson, alignés les uns avec les autres, resized ensemble, et ainsi de suite.

- **Support d’édition sur place.** Les éditeurs peuvent également permettre l’édition du contenu de leurs objets graphiques. Par exemple, une forme de rectangle peut également contenir du texte à l’intérieur qui peut être modifié par l’utilisateur. En outre, ce texte pourrait être centré ou justifié. L’édition place implique un niveau plus détaillé d’interaction utilisateur et nécessite donc un ensemble approprié d’indices visuels pour présenter des informations d’état à l’utilisateur.

#### <a name="mouse-interaction"></a>Interaction de souris

|Entrée|Résultats|
|-----------|------------|
|Cliquez sur un objet non sélectionné|Sélectionne l’objet et affiche une ligne pointillée et des poignées de sélection, si l’objet est resizable.|
|Cliquez sur un objet sélectionné|Active l’édition place si l’objet le prend en charge. Cliquer à l’extérieur de l’objet désactive le mode d’édition place.|
|Double-clic d’un objet|Ouvre le code derrière l’objet pour l’édition, et peut insérer un gestionnaire d’événement par défaut, le cas échéant.|
|Pointez vers un objet|Change le pointeur au curseur de mouvement. L’apparence de l’objet, comme sa luminosité ou sa couleur, peut changer.|
|Pointez vers une poignée de sélection|Change le pointeur au curseur de resize. Pour les objets qui prennent en charge la rotation, certaines poignées de sélection peuvent changer le pointeur en curseur de rotation au fur et à mesure que le pointeur est positionné différemment (par exemple, déplacé plus loin) en ce qui concerne la poignée de sélection.|
|Glissement|Même si l’objet n’est pas préalablement sélectionné, change le pointeur vers le curseur de mouvement et déplace l’objet.|
|L’éditeur perd son attention|Désactiver le mode d’édition en place, bien que l’objet conserve le contenu et l’apparence qu’il avait lors de son dernier état d’opération/sélection.|
|Sélection d’objets|Indiqué par une bordure, une ligne pointillée, ou tout autre traitement visuellement distinct pour mettre en évidence la limite de l’objet.|
|Resize un objet sélectionné|Indiqué par les poignées de sélection.<br /><br /> Un objet resizable a huit poignées, représentant chaque direction dans laquelle il peut être resized. Moins de poignées peuvent être utilisées si l’objet ne peut être resized que dans certaines directions. Lorsque l’utilisateur taille un objet jusqu’à l’endroit où huit poignées ne seraient pas interactives, alors quatre poignées peuvent être utilisées. La taille de la poignée doit être liée à la bordure de fenêtre et aux mesures de bord avec la fonction **aPI GetSystemMetrics** à la taille proportionnelle à la résolution d’affichage.<br /><br /> ![Poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|Faire pivoter un objet sélectionné|![Poignées de rotation](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Interaction clavier

|Entrée|Résultats|
|-----------|------------|
|Onglet|Déplace l’indicateur de mise au point parmi l’ordre logique des objets dans l’éditeur. Cela peut être de gauche à droite ou de haut en bas en fonction de la valeur de propriété **TabIndex** (ou équivalent), de l’ordre de création d’objets et de l’objectif global de l’éditeur. Shift-Tab inverse la direction de l’indicateur de mise au point.|
|Espace|Active le mode panoramique pendant que la frappe est maintenue. Une entrée supplémentaire de la souris est nécessaire pour panoramiquer la position du port de vue.|
|Ctrl+Barre d'espace|Active le mode zoom pendant que la frappe est maintenue. Une entrée supplémentaire de la souris est nécessaire pour augmenter et diminuer le facteur de zoom.|
|Signe Ctrl-Alt-Minus|Diminue le facteur zoom d’un niveau.|
|Signe de Ctrl-Alt-Plus|Augmente le facteur zoom d’un niveau.|
|Shift OU Ctrl|Ajoute l’objet au groupe de sélection. Ctrl vous permet également de supprimer les objets individuellement du groupe de sélection.|
|Entrez|Exécute la commande par défaut pour l’objet (généralement ouvert ou modifier).|
|F2|Active l’édition place de l’objet.|
|Touches de direction|Déplace l’objet sélectionné dans la direction de la clé de flèche pressée, par petites incréments (par exemple, 1 pixel à la fois)|
|Touches Ctrl-flèche|Déplace l’objet sélectionné dans la direction de la clé de flèche pressée, par tranches plus grandes (par exemple, 10 pixels à la fois)|
|Touches de shift-arrow|Resizes l’objet sélectionné dans la direction respective, par petites incréments (par exemple, 1 pixel à la fois)|
|Touches de flècheS Ctrl-Shift|Resizes l’objet sélectionné dans la direction respective, par tranches plus grandes (par exemple, 10 pixels à la fois)|

 Lorsque les utilisateurs modifient les contrôles en place, il peut être logique que les objets se resizent automatiquement avec l’entrée de l’utilisateur. Par exemple, si l’utilisateur modifie un contrôle d’étiquette, alors l’étiquette doit se développer pour afficher le texte que l’utilisateur vient d’taper. Si cela n’est pas fait, l’utilisateur doit resize le contrôle manuellement après l’édition du texte. Si l’utilisateur a beaucoup de contrôles, cela devient une tâche rote et improductive.

#### <a name="graphical-containers"></a>Conteneurs graphiques
 Dans certains cas, les éditeurs graphiques fournissent des conteneurs pour d’autres objets graphiques, tels que le contrôle du panneau de formulaires Windows ou le contrôle de mise en page de grille dans le concepteur HTML. Si votre éditeur fournit des conteneurs pour d’autres objets graphiques, alors le modèle de sélection suivant ne doit être utilisé que pour le conteneur (les objets dans le conteneur suivent le modèle standard tel que décrit ci-dessus) :

|Entrée|Résultats|
|-----------|------------|
|En un seul clic sur le conteneur|Sélectionne l’objet de conteneur sans sélectionner directement aucun des objets contenus. Le conteneur peut être déplacé et/ou resized avec l’entrée standard de la souris et du clavier (comme décrit ci-dessus). Les objets contenus sont déplacés par rapport au conteneur, mais les objets contenus ne sont pas resized à moins qu’ils ne soient également sélectionnés directement.|
|Planer au-dessus de la région limite du conteneur|Transforme la souris en curseur de mouvement, indiquant que le récipient peut être déplacé.|
|Faites glisser la région limite du conteneur|Change la souris vers le curseur de déplacement et déplace le récipient (et les objets contenus à l’intérieur). Le conteneur ne peut pas être déplacé sans d’abord être sélectionné en un seul clic.|
|En un seul clic sur un objet à l’intérieur du conteneur|Désélections le conteneur (s’il est sélectionné) et ne sélectionne que l’objet cliqué.|
|Shift-click OU Ctrl-cliquez sur un objet et/ou un conteneur contenu|Ajoute l’objet cliqué à un groupe de sélection ou de sélection existant. Si l’objet cliqué est déjà membre du groupe de sélection, il est retiré du groupe de sélection.|

 Les objets contenus doivent adhérer au modèle de sélection de base tel que décrit dans la section précédente. À partir des tests de convivialité du concepteur de formulaires Windows, les utilisateurs s’attendaient à un accès sans faille aux objets contenus sans intervenir (imposé par l’objet de confinement).

#### <a name="disjoint-and-region-selections"></a>Sélections disjointes et régions
 Les éditeurs d’objets graphiques doivent prendre en charge les sélections de disjoints. Veuillez noter que ce graphique ne montre pas l’apparence de contrôle pour Visual Studio. Voir [l’apparence de sélection d’objets graphiques](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) pour des spécifications visuelles détaillées.

 ![Sélecteurs de régions et disjoints](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Sélection de disjoints**

 Les éditeurs graphiques devraient également fournir des sélections de régions avec un indicateur de sélection de type chapiteau. Si l’éditeur graphique prend en charge d’autres types d’objets (comme le texte), les sélections de régions peuvent ne pas être possibles en fonction des contraintes de ces autres types d’objets.

 ![Sélection de texte défilant](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **Sélection de texte défilant**

#### <a name="primary-and-secondary-selections"></a>Sélections primaires et secondaires
 Certains éditeurs d’objets graphiques permettent à l’utilisateur de modifier ou d’aligner des objets en groupes. Dans ce cas, le concept de sélections primaires et secondaires doit être introduit. La sélection principale est l’objet auquel tous les autres objets répondent pour les opérations de groupe. L’objet que l’utilisateur sélectionne d’abord devient le contrôle principal, et les sélections ultérieures deviennent les sélections secondaires. La sélection primaire a un traitement visuel distinct de la sélection secondaire pour indiquer quel objet est primaire :

 ![Sélection principale et secondaire](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **Sélection primaire avec deux sélections secondaires**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a>Apparence de sélection d’objets graphiques
 Les poignées de sélection sont des carrés dessinés dans un motif rectangulaire autour de la boîte de délimitation de l’objet. Le tableau ci-dessous montre des exemples des différents états qu’un objet graphique peut avoir avec la poignée, le dimensionnement et l’apparence d’édition en place. La taille des poignées doit être liée à la bordure de fenêtre et aux mesures de bord à l’aide de l’API **GetSystemMetrics.**

| State | Apparence | Détails visuels |
|-------------------------|---------------| - |
| **Non sélectionné** | Default | ![État du bouton par défaut](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState") |
| **Sélection primaire** | Redimensionnable | ![Sélection principale avec des poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize") |
| **Sélection primaire** | Non resizable | ![Sélection principale sans poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize") |
| **Sélection primaire** | Verrouillé | ![Sélection principale verrouillée](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked") |
| **Sélection secondaire** | Redimensionnable | ![Sélection secondaire avec des poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize") |
| **Sélection secondaire** | Non resizable | ![Sélection secondaire sans poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize") |
| **Sélection secondaire** | Verrouillé | ![Sélection secondaire verrouillée](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked") |
| **Assurance-chômage active** | Default | ![État actif de l'interface utilisateur](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive") |

### <a name="view-selection-models"></a>Afficher les modèles de sélection

#### <a name="tree-view"></a>Arborescence
 La sélection dans une vue d’arbre est montrée avec un point culminant simple. Si l’utilisateur clique sur un nom de nœud ou une icône de nœud, le nœud est sélectionné. Les glyphes triangulaires à gauche du nœud se dilatent ou contractent le contrôle de l’arbre mais n’affectent pas la sélection de l’utilisateur, à une exception près : en faisant un nœud parent lorsque la sélection est sur un enfant de ce nœud, la sélection passe au parent.

 ![Arborescence classique dans Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Arborescence classique dans Visual Studio**

 Les vues sur les arbres peuvent soutenir les sélections contigus et décousues, même à plusieurs niveaux de l’arbre. Des sélections multiples contigues ou décousues doivent être faites sur des nœuds d’arbres visibles. Si un nœud s’effondre, la sélection de disjoints est perdue et le nœud qui s’est effondré obtient la sélection. De cette façon, l’utilisateur peut voir les nœuds qui seront affectés par une opération. Lorsque les nœuds sont effondrés, il devient difficile de savoir quels nœuds pourraient être touchés.

 Lorsqu’un nœud parental est choisi, l’opération doit s’appliquer au parent, bien qu’il puisse y avoir des cas où il est logique qu’une opération s’applique au parent et à tous ses enfants. Dans ce cas, fournir une interface utilisateur supplémentaire pendant l’opération, comme une case à cocher ou un dialogue de confirmation pour rendre l’option « appliquer à tous les enfants » explicite à l’utilisateur.

##### <a name="renaming"></a>Renommage
 Si les nœuds dans le support de l’arbre renommage, le changement de nom doit être fait en place. L’opération sur place devrait être la norme sur tous les contrôles d’arbres de Visual Studio. Fournir une commande de renom qui active immédiatement le mode d’édition en place, avec la sélection de texte couvrant l’ensemble du nom du nœud, prêt à accepter l’entrée de l’utilisateur. Si le nœud représente un fichier, le nom de fichier doit contenir l’extension. Le point culminant de sélection doit inclure seulement le corps du nom de fichier et non l’extension.

|Entrée|Résultats|
|-----------|------------|
|Entrée (touche)|Engage l’opération de renommage|
|Clé Esc|Annule l’opération de renommage|
|Cliquer en dehors de la région d’édition sur place|Engage l’opération de renommage|
|Annuler|Fournir un défaire facile pour annuler l’opération de renom|

#### <a name="selection-within-lists-and-grid-controls"></a>Sélection dans les listes et les contrôles de grille
 Le concept clé dans la sélection de liste est qu’il est basé sur la rangée, ce qui signifie que lorsqu’une sélection est faite toute la rangée est sélectionnée comme une unité. En revanche, les grilles peuvent permettre de sélectionner des cellules spécifiques sans affecter aucun autre aspect de la ligne. Les grilles peuvent également contenir une hiérarchie de rangées imbriquées (comme dans un TreeGrid) qui permettent de sélectionner et de désélectionner des branches entières de la hiérarchie en interagissant avec les lignes parentes. La sélection dans les listes est affichée par une couleur de surbrillance simple sur toute la rangée de données. La mise au point est affichée par une bordure pointillée d’un pixel autour de la ligne ou de la cellule modifiable actuelle (ligne si toutes les cellules sont lues uniquement).

> [!NOTE]
> **La mise au point** et **la sélection** sont des concepts différents. *L’accent* est une indication de l’élément d’interface utilisateur visé pour recevoir des entrées non explicitement dirigées vers un autre objet, tandis que la *sélection* se réfère à l’état de l’inclusion d’un objet dans un ensemble d’objets sur lesquels des opérations ultérieures peuvent avoir lieu.

 Les sélections dans les listes peuvent être contigus, disjointes, ou région. Lorsque plusieurs sélections sont autorisées, la sélection contigue et décousue doit toujours être prise en charge, tandis que le soutien aux sélections de région (boîte) est facultatif. Les sélections de régions sont initiées en traînant dans l’espace blanc de l’organe de liste.

| Object | Sélection |
|--------|------------|
| List | Contiguë |
| List | Disjoint |
| List | Région |

 En cliquant une fois sur une liste sélectionne la ligne où le clic s’est produit. Si l’utilisateur arrive à cliquer dans une cellule de liste qui prend en charge l’édition sur place, la cellule est également immédiatement activée pour l’édition en place. Sinon, toute la rangée est immédiatement sélectionnée et montre un point culminant.

 Dragging dans le corps de liste fait l’une des trois choses:

- Initie une sélection de région si la liste la prend en charge et que la souris est dans l’espace blanc

- Initie une opération de drag/drop si la cellule de liste ou la ligne supporte d’être une source de drag

- Sélectionne la ligne actuelle

##### <a name="in-place-editing"></a>Montage sur place
 Lorsque l’édition place est autorisée, il existe deux modèles de base : le contrôle de modification simple et le cueilleur de propriété. Avec un contrôle d’édition simple, le contenu est mis en surbrillance et prêt pour l’entrée de l’utilisateur dès que l’édition place est activée. Lorsqu’un cueilleur de propriété est implémenté, le bouton qui invoque le viseur de propriété est affiché une fois que le mode d’édition en place est activé, et la sélection actuelle n’est pas mise en évidence. Le bouton de cueilleur doit être justifié à juste titre dans la cellule. Pour des exemples d’édition sur place, consultez la fenêtre des **propriétés** et **la liste des tâches** dans Visual Studio.

##### <a name="keyboard-support"></a>Prise en charge du clavier
 Le support clavier pour la sélection dans les listes et les grilles suit les conventions Windows standard :

- Les touches de flèche naviguent dans la liste, en sélectionnant chaque rangée/cellule au fur et à mesure que l’accent est déplacé.

- Le décalage et la flèche effectuent une sélection contigu dans la direction des touches fléchées.

- Ctrl - flèche suivie par Spacebar bascule entre l’ajout et la suppression des éléments de liste de la sélection, la création d’une sélection de décousu.

- Pour les grilles qui contiennent des hiérarchies imbriquées, la clé droite de flèche étend une rangée de parents, et la clé de la Flèche gauche s’effondre.

- La clé Tab déplace la mise au point parmi les cellules de la rangée actuelle si les cellules sont modifiables.

- La clé Enter effectue la commande par défaut sur l’élément de la liste (souvent **Ouvert**).

- La clé F2 active l’édition place pour la cellule actuellement sélectionnée.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a>Paramètres de persistance et d’enregistrement

### <a name="overview"></a>Vue d'ensemble
 Bien que chaque composant logiciel de Visual Studio soit généralement responsable de son état et de sa persistance, Visual Studio enregistre automatiquement les paramètres dans certains cas, comme avec la taille des fenêtres et les positions. Le tableau ci-dessous est une combinaison de paramètres enregistrés automatiquement et de paramètres qui nécessitent une action utilisateur ou programmée explicite à prendre.

|Object|Ce qu’il faut économiser|Quand enregistrer|Où économiser|
|------------|------------------|------------------|-------------------|
|Objet sélectionnable (par exemple, une ligne de code)|Un point d’arrêt sur une ligne de code<br /><br /> Un raccourci utilisateur associé à la ligne de code|Lorsque le projet est sauvegardé|Le fichier **options utilisateur (.suo)** pour le projet|
|Boîte de dialogue|L’emplacement du dialogue, s’il avait été déplacé<br /><br /> La vue que l’utilisateur a utilisé pour la dernière fois dans le dialogue|Lorsque le dialogue se termine<br /><br /> À la fin de la session Visual Studio|En mémoire<br /><br /> Registre en **HKEY_Current_User**|
|Fenêtre|La taille et l’emplacement de la fenêtre|Quand la fenêtre se ferme<br /><br /> Lorsque le mode Visual Studio change<br /><br /> À la fin de la session Visual Studio|Le fichier **options utilisateur (.suo)** pour le projet<br /><br /> Fichier d’options personnalisées pour les paramètres de fenêtre|
|Document|La sélection actuelle dans le document<br /><br /> La vue du document<br /><br /> Les derniers endroits que l’utilisateur a visités|Lorsque le document est enregistré|Le fichier **options utilisateur (.suo)** pour le projet|
|Projet|Références aux fichiers<br /><br /> Références aux répertoires sur disque<br /><br /> Références à d’autres logiciels<br /><br /> Components<br /><br /> Informations de l’État sur le projet lui-même|Lorsque le projet est sauvegardé|Fichier projet|
|Solution|Références aux projets<br /><br /> Références aux fichiers|Lorsque le projet ou la solution est sauvegardé|Le fichier **solution (.sln)**|
|Paramètres dans **les outils > options**|Personnalisations de clavier<br /><br /> Personnalisations de barres d’outils<br /><br /> Schémas de couleurs|Lorsque le dialogue **Tools > Options** se termine<br /><br /> À la fin de la session Visual Studio|Registre en **HKEY_Current_User**|

 Ce que fait l’utilisateur, et quand il le fait, dicte si un paramètre est enregistré dans la mémoire (pendant la session), enregistré sur disque (à travers les sessions comme un paramètre de registre), dans le cadre du fichier de projet ou de solution lui-même, dans le cadre du fichier options de **solution (.suo),** ou comme un fichier de paramètres personnalisés que seul ce composant logiciel connaît. Le tableau ci-dessus montre plusieurs événements auxquels les paramètres peuvent être enregistrés. Cependant, il ya d’autres moments dans lesquels vous pourriez vouloir sauver l’état:

- Lorsque l’utilisateur change d’emplacement dans un dialogue ou une fenêtre

- Lorsque l’utilisateur transfère la mise au point vers une autre fenêtre

- Lorsque l’utilisateur passe du mode design au mode débogé

- Lorsque l’utilisateur se connecte à son compte

- Lorsque l’ordinateur entre en hibernation ou s’arrête

- Lorsque l’ordinateur / disque dur est sur le point d’être reformaté et mis en place à nouveau

### <a name="window-configurations"></a>Configurations de fenêtre
 Une configuration de fenêtre est la présentation de base de l’environnement de développement - il s’agit d’un schéma composé de la liste des fenêtres d’outils présentes et de la façon dont elles sont disposées. Pour les fenêtres gérées par les fenêtres IDE (fenêtres IDE), les informations de mise en page sont persistantes par utilisateur, de sorte que lorsqu’un utilisateur lance l’IDE, la disposition de la fenêtre apparaît comme lors de leur dernière sortie visual Studio. L’état et la position des fenêtres IDE sont persistants dans un fichier d’options personnalisés en format XML. Les fenêtres d’outils qui sont créées par des paquets chargés dans l’IDE persistent leurs informations d’état dans le registre et peuvent ou non être par utilisateur.

#### <a name="profile-specific-layouts"></a>Mises en page spécifiques au profil
 Chaque profil comprend des mises en page de fenêtre d’outils, organisées d’une manière familière à des personnalités spécifiques du développeur (les développeurs visualS CMD s’attendent à voir **l’explorer de solution** sur le côté gauche de l’IDE, tandis que les développeurs C ' s’attendent à voir **l’explorer de solution** sur la droite). Les mises en page des fenêtres spécifiques au profil sont chargées après que l’utilisateur a choisi un profil sur le démarrage. Un auteur de paquets doit déterminer la disposition de la fenêtre la plus adaptée à l’expérience de son client, sachant que les modifications apportées à la configuration de la fenêtre seront alors persistées.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a>Entrée tactile
 Les utilisateurs utilisent de plus en plus les produits de développement Microsoft sur les appareils tactiles. Cependant, il existe des obstacles qui rendent difficile l’utilisation d’outils de développement sur les appareils tactiles. Les utilisateurs s’attendent à ce que nos produits offrent une expérience tactile fiable et précise. L’objectif de ces lignes directrices est d’éclairer les décisions concernant les capacités tactiles à intégrer et d’encourager une expérience tactile cohérente à travers Visual Studio et les produits connexes.

### <a name="levels-of-experience"></a>Niveaux d’expérience
 Les niveaux d’expérience suivants sont destinés à servir de guide pour aider les équipes à décider quelles capacités tactiles offrir en fonction de leur niveau souhaité d’intérêt d’investissement en contact.

- **L’expérience de base** est pour les équipes qui veulent fournir des capacités tactiles afin qu’il n’y ait pas d’impasses tout au long de leur travail.

- **L’expérience optimisée** est pour les équipes qui veulent fournir les capacités tactiles les plus courantes (par exemple, celles généralement disponibles dans les applications de navigateur Internet).

- **L’expérience élevée** est pour les équipes qui veulent ajouter des capacités telles que des gestes ou d’autres capacités facultatives qui peuvent rendre leur application tactile d’abord amicale.

||Expérience de base|Expérience optimisée|Expérience élevée|
|-|----------------------|--------------------------|-------------------------|
|Permet aux utilisateurs de ...|Fixer le code et la lecture au niveau de la solution/projet sans impasses|Effectuer des tâches d’entretien, de refacteurs et de navigation|Opérer dans une expérience cohérente, intuitive et fluide avec confiance|
|Éditeur|Panoramique tactile et sélection<br /><br /> Touche de barre de défilement pour sauter et presser|Zoom de pincement<br /><br /> Défilement rapide<br /><br /> Sélection<br /><br /> Utilisation facile du menu contextuelle||
|Fenêtres d’outils supérieures|Liste panoramique<br /><br /> Sélection d’élément<br /><br /> Touche de barre de défilement pour sauter et presser|Mise en défilement et sélection d’objets faciles||
|Fenêtrage||Fenêtre resize<br /><br /> Accès rapide||
|Bien documenter||Navigation facile entre les fichiers ouverts||
|Mouvements||Veiller à ce que les gestes communs fonctionnent dans l’ensemble de l’IDE|Actions basées sur les gestes<br /><br /> Soutenir le drag-and-drop et les concepteurs|
|Autres considérations|||Clavier personnalisé à l’écran|

#### <a name="gestures"></a>Mouvements
 Les gestes fournissent aux utilisateurs un raccourci vers des commandes qui pourraient autrement nécessiter une interaction plus compliquée. Reportez-vous aux directives De Windows sur les [gestes tactiles courants pour les applications de bureau,](/windows/desktop/wintouch/windows-touch-gestures-overview)et suivez ces conseils pour la plupart des gestes, y compris des gestes simples tels que panoramique et zoom.
