---
title: "Mod&#232;les composites pour Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Mod&#232;les composites pour Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Modèles composites combinent des éléments de conception et l’interaction de configurations distinctes. Parmi les modèles les plus importants composites dans Visual Studio en matière de cohérence :  
  
-   [Visualisation des données](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)  
  
-   [L’interface Utilisateur et la lecture sur les objets](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
-   [Modèles de sélection](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
-   [Persistance et l’enregistrement des paramètres](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
-   [Entrée tactile](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)  
  
##  <a name="a-namebkmkdatavisualizationa-data-visualization"></a><a name="BKMK_DataVisualization"></a> Visualisation des données  
  
### <a name="overview"></a>Vue d'ensemble  
 Les graphiques sont un moyen visuel d’agrégation et de visualiser les données afin d’améliorer la prise de décision. Ils peuvent aider les utilisateurs confrontés à un grand nombre de données, mais peu de signification voir ce qui mérite une attention et ce qui peuvent nécessiter une action.  
  
 L’utilisateur bénéficieront d’un graphique si une des conditions suivantes est vraie :  
  
-   Sera le graphique d’aider les utilisateurs à identifier les tâches qu’ils peuvent agir sur ?  
  
-   Le graphique permettra aux utilisateurs de prévoir les conséquences des modifications potentielles ?  
  
-   Sera le graphique d’aider les utilisateurs à découvrir des tendances et identifier des modèles ?  
  
-   Le graphique permettra aux utilisateurs de prendre de meilleures décisions ?  
  
-   Le graphique aideront à répondre à des questions spécifiques que les utilisateurs devront peut-être dans le contexte donné ?  
  
#### <a name="general-rules-for-charts"></a>Règles générales pour les graphiques  
  
-   Clairement les données d’étiquette. Illustrations sans aucune explication ne sont que de belles images.  
  
-   Démarrer les axes à zéro, afin d’éviter les proportions d’inclinaison. Taille de ligne de longueur et de la barre sont des signaux visuels importants à comprendre les relations entre les points de données.  
  
-   Créer des graphiques, des éléments d’infographie pas. Infographie est des représentations artistiques de données, et leur objectif principal est de narration visual. Les graphiques peuvent (et devraient) être attrayante, mais que les données parlent d’elles-mêmes.  
  
-   Évitez de skeumorphism, la représentation graphique des graphiques à barres, contraste hashmarks et autres fonctions tactiles infographie.  
  
-   N’utilisez pas d’effets 3D comme élément décoratif. Utilisez-les uniquement si elles réellement partie intégrante de la capacité de l’utilisateur à comprendre les informations.  
  
-   Évitez d’utiliser plusieurs lignes et remplissages, en plus de deux couleurs peuvent rendre ce type de graphique difficile à lire et interpréter correctement.  
  
-   N’utilisez pas un graphique (ou toute illustration) sont les seuls moyens de comprendre un concept ou l’interaction avec les données. Cela pose des difficultés pour les utilisateurs ayant des troubles visuels.  
  
-   N’utilisez pas les graphiques en tant qu’éléments superflues ou décoratifs sur une page. En d’autres termes, si un graphique n’ajoute pas tous les utilisateurs de valeur ou de l’aide à résoudre un problème, n’utilisez pas cela.  
  
### <a name="chart-types"></a>Types de graphiques  
 Types de graphiques utilisées dans Visual Studio incluent des graphiques à barres, graphiques en courbes, un graphique à secteurs modifié appelé un « donut graphique, « chronologies, ou en anneau à nuages de points (également appelés « cluster graphiques ») des graphiques et diagrammes de Gantt. Chaque type de graphique est utile pour la communication d’un autre type d’informations.  
  
### <a name="other-charting-considerations"></a>Autres considérations relatives à la création de graphiques  
  
#### <a name="color"></a>Couleur  
 Il existe une palette spécifique des graphiques couleurs sont définies pour une utilisation dans Visual Studio. La palette est accessible pour les principaux types de daltonisme, et les couleurs peuvent être différenciés même lorsqu’elle sert de tranches très étroits de couleur. Vous pouvez utiliser ces couleurs dans n’importe quelle combinaison de tout type de graphique dans votre interface Utilisateur. Il est inutile d’utiliser toutes les couleurs de sept si vous n’avez pas besoin d’autant de couleurs distinctes. Ces couleurs ne sont pas conçus pour être utilisé avec tous les éléments de premier plan, donc vous ne placez ne pas de texte ou des glyphes sur ces couleurs. Ces teintes doivent être codé en dur et exposées à la personnalisation de l’utilisateur sous **Outils > Options** (voir [exposant des couleurs pour les utilisateurs finaux](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).  
  
|Échantillon|Hex|RVB|  
|------------|---------|---------|  
|![Échantillon 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71 B 252|113,178,82|  
|![Échantillon BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|  
|![Échantillon FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|  
|![Échantillon 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|  
|![Échantillon 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|  
|![Échantillon 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|  
|![Échantillon B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|  
  
##  <a name="a-namebkmkonobjectuia-on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a> L’interface Utilisateur et la lecture sur les objets  
 Cette section fournit un contexte pour la lecture, également appelé mode Aperçu de code, un type d’INTERFACE sur les objets spécifique à Visual Studio.  
  
### <a name="overview"></a>Vue d'ensemble  
  
-   L’interface Utilisateur de l’objet doit fournir l’utilisateur plus d’informations ou l’interactivité sans se départir de leurs tâches principales.  
  
-   Le modèle principal pour les objets interface Utilisateur dans Visual Studio est appelé « information au point une attention ».  
  
-   L’interface Utilisateur sur les objets dans Visual Studio est soit inline ou flottant et durable ou transitoire.  
  
    -   Mode de lecture du code, un type d’interface Utilisateur sur les objets dans Visual Studio, est en ligne et durable.  
  
    -   CodeLens, un type d’interface Utilisateur sur les objets dans Visual Studio, est à virgule flottante et temporaires  
  
 Comprendre le fonctionne d’un élément de code ou de trouver plus d’informations sur ce code, nécessite souvent un développeur de basculer le contexte et accédez à tout autre contenu ou d’une autre fenêtre. Ces changements de contexte peuvent être sans interruption, car les utilisateurs peuvent perdre le focus sur leurs tâches d’origine s’ils quittent leur fenêtre principale. En outre, l’obtention qu’arrière de contexte d’origine peut être difficile, surtout si ce changement windows provoqué leur code d’origine pour être masquées par toute autre interface Utilisateur.  
  
 L’interface Utilisateur de l’objet suit un modèle appelé « information au point une attention ». Ces messages, fenêtres et boîtes de dialogue de donnent aux utilisateurs des informations complémentaires utiles qui ajoute une clarification ou l’interactivité sans perdre le focus sur leurs tâches principales. Exemples de l’interface Utilisateur sur les objets incluent des fenêtres publicitaires qui s’affichent lorsqu’un utilisateur pointe le pointeur sur une icône dans la zone de notification, la ligne ondulée rouge sous un mot mal orthographié, la vue Aperçu introduite dans Visual Studio 2013.  
  
### <a name="decision-points"></a>Points de décision  
 Dans Visual Studio, il existe plusieurs façons d’utiliser ce modèle d’informations au moment de l’attention. Choix du mécanisme de droite et l’implémentation d’une manière cohérente et prévisible sont essentielle pour l’expérience globale. Dans le cas contraire, les utilisateurs peuvent s’afficher avec une expérience confuse ou incohérente qui porte atteinte le focus à partir du contenu lui-même.  
  
#### <a name="relationships-between-master-and-detail-content"></a>Relations entre un maître et détail de contenu  
 Pour plus d’informations au moment de l’attention sont utilisés pour afficher une relation entre le contenu que l’utilisateur est consacré (le contenu « maître ») et d’autres liées contenu (le contenu de « détail »). Dans ce modèle, le contenu détaillé est clairement lié au contenu, l’utilisateur travaille avec et peut être affiché près du contenu principal. Des informations supplémentaires ou des informations qui ne peuvent pas être résumées sans pour autant submerger le contenu principal doivent suivre un autre modèle, telle qu’une fenêtre outil.  
  
-   **Toujours** Afficher le contenu de détail à proximité du contenu principal.  
  
-   **Toujours** vous assurer que le contenu de détail permet toujours à un utilisateur de rester concentré sur le contenu principal. Souvent, la meilleure façon d’y parvenir consiste à restituer le contenu de détail comme proche du contenu principal que possible. Cela est possible en rendant le contenu détaillé dans une fenêtre contextuelle en regard du contenu principal, ou via le rendu de la ligne de contenu de détail sous le contenu principal.  
  
-   **Jamais** utiliser des informations au moment de l’attention qui dirige l’utilisateur en dehors du contenu principal. Si les utilisateurs doivent consulter le contenu de détail séparément, exposer une action explicite qui permet à l’utilisateur pour ce faire.  
  
#### <a name="design-details"></a>Détails de la conception  
 Une fois que vous avez déterminé que l’interface Utilisateur de l’objet est le bon choix, il existe quatre considérations de conception principale :  
  
1.  **Persistance :** le contenu doit être durable ou temporaire ?   
    Les utilisateurs souhaitent que les informations visibles à faire ou interagir avec ? Ou les utilisateurs souhaiteront aperçu rapidement les informations et puis poursuivre leur tâche principale ?  
  
2.  **Type de contenu :** le contenu sera d’information, exploitables ou navigation ?   
    L’utilisateur doit-il des détails supplémentaires sur le contenu principal ? L’utilisateur a-t-il besoin pour effectuer une tâche qui a une incidence sur le contenu principal ? Ou l’utilisateur doit être dirigé vers une autre ressource ?  
  
3.  **Type d’indicateur :** a un indicateur ambiant sens ?   
    Les informations peuvent être résumées de manière utile et affichées sans pour autant submerger le contenu principal ?  
  
4.  **Mouvements :** mouvements de ce qui sera utilisé pour appeler et fermer l’interface Utilisateur ?   
    Comment l’utilisateur affiche le contenu de détail et envoyer immédiatement ? Existe-t-il des valeur lors de l’ajout d’un mouvement telles que l’épinglage pour basculer entre les états transitoires et durables ?  
  
 Chacun de ces points de quatre décision aura un impact sur les principaux composants de l’interface Utilisateur de l’objet.  
  
### <a name="on-object-ui-components"></a>Composants d’interface Utilisateur sur les objets  
  
1.  Type de conteneur (présentateur de contenu)  
  
    -   Virgule flottante  
  
    -   Inline  
  
2.  Type de contenu  
  
    -   Information : données pouvant être statique ou dynamique  
  
    -   Action : commandes qui modifient le contenu principal  
  
    -   Navigation : des liens qui dirige l’utilisateur vers une autre fenêtre ou application, telles que MSDN  
  
3.  Mouvements  
  
    -   Invocation  
  
    -   Licenciement  
  
    -   L’épinglage  
  
    -   Autres interactions  
  
4.  Modèle de persistance et de validation  
  
    -   Temporaire  
  
    -   Durable  
  
    -   Automatique  
  
    -   À la demande  
  
5.  Indicateurs ambiantes (facultatifs)  
  
    -   Soulignement de trait de soulignement ondulé  
  
    -   Icône de balise active  
  
    -   Autres indicateurs ambiantes  
  
#### <a name="container-content-presenter-type"></a>Type de conteneur (présentateur de contenu)  
 Il existe deux principales options sont disponibles pour présenter un contenu au point d’attention :  
  
1.  **Inline :** un présentateur inline, telles que la vue Aperçu qui a été introduit dans l’éditeur de Code Visual Studio 2013, libère de l’espace pour le nouveau contenu en déplaçant le contenu existant.  
  
    -   **Préférez** Présentateurs inline si vous pensez que les utilisateurs souhaitent passent beaucoup de temps faisant référence à ou interagir avec le contenu que vous présentez.  
  
    -   **Éviter** Présentateurs inline si vous pensez que les utilisateurs souhaiteront coup de œil les informations vous présenterez, puis poursuivez leur tâche principale avec une interruption minimale.  
  
2.  **Flottant :** présentateur flottant est positionné le plus proche au contenu sélectionné que possible, mais ne modifie pas la disposition du contenu existant. Différentes stratégies peuvent être employées, telles que l’affichage d’un panneau flottant contenu via le plus proche de l’espace disponible pour le symbole sélectionné.  
  
    -   **Préférez** flottante présentateurs si vous pensez que les utilisateurs souhaiteront coup de œil les informations vous présenterez, puis poursuivez leur tâche principale avec une interruption minimale.  
  
    -   **Éviter** flottante présentateurs si vous pensez que les utilisateurs souhaiteront consacrer beaucoup de temps faisant référence à ou interagir avec le contenu vous intéresse.  
  
#### <a name="content-type"></a>Type de contenu  
 Il existe trois principaux types de contenu qui peuvent être affichés à l’intérieur de n’importe quel conteneur de l’interface Utilisateur sur les objets. N’importe quelle combinaison de ces types d’informations peut être affichée. Les trois types sont :  
  
1.  **Information :** la plupart des objets conteneurs de l’interface Utilisateur affiche un type de contenu d’information. Le contenu peut représenter des informations sur l’état actuel de l’environnement, ou il peut représenter des informations sur un état future potentielle de l’environnement. Par exemple, il peut être utilisé pour montrer l’effet d’une commande particulière, par exemple une refactorisation du code existant.  
  
    -   **Toujours** utilisation de la représentation canonique des informations que vous affichez. Par exemple, le code doit se présenter comme le code, avec la syntaxe et doit respecter des polices et autres paramètres d’environnement que l’utilisateur a défini.  
  
    -   **Toujours** envisager la prise en charge de toutes les actions sur le contenu d’information qui serait possible si ces mêmes informations sont présentées sous forme de contenu principal. Par exemple, si présentant le code existant à l’intérieur d’un conteneur de l’interface Utilisateur sur les objets, fortement d’envisager la possibilité de parcourir et modifier ce code de prise en charge.  
  
    -   **Toujours** envisager d’utiliser une couleur d’arrière-plan différente si Presentation de contenu d’information qui représente un état futur potentiel.  
  
2.  Exploitables : certains conteneurs de l’interface Utilisateur sur les objets seront offrent la possibilité d’effectuer une action sur le contenu principal, telles que l’exécution d’une opération de refactorisation.  
  
    -   **Toujours** positionner des commandes séparément à partir du contenu d’information.  
  
    -   **Toujours** Activer et désactiver les actions lorsque cela est approprié.  
  
    -   **Toujours** reportez-vous aux instructions standards pour représenter les commandes dans les boîtes de dialogue.  
  
    -   **Toujours** conserver le nombre d’actions qui sont exposées dans un conteneur de l’interface Utilisateur sur les objets au strict minimum. Interaction avec l’interface Utilisateur de l’objet doit être une expérience léger et rapide. L’utilisateur ne devez pas à étendre l’énergie sur la gestion du conteneur de l’interface Utilisateur sur les objets.  
  
    -   **Toujours** envisager comment et quand un conteneur de l’interface Utilisateur sur les objets est fermé ou rejeté. Comme meilleure pratique, toute action qui conclut la boîte de dialogue entre maître et détail contenu doit également fermer le conteneur de l’interface Utilisateur sur les objets lorsque cette action est appelée.  
  
3.  **Navigation :** certains objets conteneurs de l’interface Utilisateur incluent des liens qui dirige l’utilisateur vers une autre fenêtre ou application, telle que l’ouverture d’un article MSDN dans le navigateur web de l’utilisateur.  
  
    -   **Toujours** Ajouter n’importe quel lien de navigation « Ouvert » afin que les utilisateurs ne seront pas être surpris par cible de la navigation sur un autre contenu.  
  
    -   **Toujours** séparer les liens de navigation de liens utilisables.  
  
#### <a name="ambient-indicators-optional"></a>Indicateurs ambiantes (facultatifs)  
 Indicateurs ambiantes peuvent être subtiles, y compris le texte présenté dans une couleur contrastée du reste du code, ou évident, y compris les symboles installer tels que les soulignements tilde et icônes de balise active. Indicateurs ambiantes communiquent la disponibilité des informations complémentaires utiles. Dans l’idéal, ils fournissent des informations utiles même sans que l’utilisateur d’interagir avec eux.  
  
-   **Toujours** positionner un indicateur ambiant afin qu’il ne pas distraire ou submerger l’utilisateur. S’il est impossible de placer un indicateur ambiant de manière, envisagez une autre solution.  
  
-   **Toujours** positionner l’indicateur ambiante aussi proche que possible pour le contenu qui lui sont associés.  
  
-   **Toujours** essaie de créer un indicateur qui synthétise les informations qu’il rend disponibles. Envisagez de fournir un décompte du nombre d’éléments de données disponibles (par exemple, « 3 références » au lieu de simplement « références ») ou considérer une autre façon pour synthétiser les données.  
  
    -   Dans les cas où les données d’un indicateur ne peut pas toujours être calculées et affichées, envisagez immédiatement commentaires progressif comme les valeurs sont calculées. Par exemple, envisagez d’animer des modifications qui reflètent les mises à jour des données disponibles, la même manière que le nombre de courriers électroniques non lus, des actualisations de la vignette dynamique par courrier électronique sur Windows Phone.  
  
-   **Jamais** Ajouter des indicateurs de plus qu’un utilisateur peut raisonnablement un élément donné de contenu. Indicateurs ambiantes doivent être utiles sans nécessiter l’intervention de l’utilisateur. Indicateurs de perdre leur ambiance s’ils requièrent le dépassement de capacité et d’autres contrôles de gestion pour les afficher dans la vue.  
  
#### <a name="gestures"></a>Mouvements  
 Un aspect clé de permettre à l’utilisateur de conserver le focus sur le contenu principal est en prenant en charge les mouvements de droite pour ouvrir et fermer le contenu des détails supplémentaires.  
  
-   **Toujours** nécessite que l’utilisateur effectuer des mouvements explicite pour ouvrir le contenu supplémentaire. Mouvements open courantes sont les suivantes :  
  
    -   **Pointage :** info-bulles ou non interactif contenu informatif  
  
    -   **Commande explicite :** inline présentateur  
  
    -   **Double-cliquez sur l’indicateur ambiante :** fenêtre contextuelle CodeLens  
  
-   **Toujours** faire disparaître le contenu en détail chaque fois que l’utilisateur appuie sur la touche ÉCHAP.  
  
-   **Toujours** prendre en compte le contexte de l’interface Utilisateur sur les objets. Pour les présentateurs de contenu qui permettent l’interaction du conteneur, déterminer s’il faut afficher des informations supplémentaires pour le pointage, qui est susceptible de causer des perturbations pour les flux de travail de l’utilisateur.  
  
-   **Jamais** afficher du contenu pointage qui semble être modifiable ou invite l’interaction de l’utilisateur. Ce comportement peut embêter les utilisateurs s’ils tentent de déplacer le curseur sur le contenu de détail, comme le comportement standard d’une info-bulle est pour fermer immédiatement lorsque le curseur n’est plus sur le contrôleur de contenu qui l’a produit.  
  
##  <a name="a-namebkmkselectionmodelsa-selection-models"></a><a name="BKMK_SelectionModels"></a> Modèles de sélection  
  
### <a name="overview"></a>Vue d'ensemble  
 Un modèle de sélection est le mécanisme utilisé pour indiquer et vérifier les opérations sur un ou plusieurs objets d’intérêt dans l’interface utilisateur. Cette rubrique traite des modèles d’interaction de sélection dans les éditeurs de document Visual Studio : éditeurs de texte, aires de conception et modélisation des surfaces.  
  
 Les utilisateurs doivent avoir un moyen d’indiquer à Visual Studio qu’ils travaillent et Visual Studio doit répondre prévisible avec des commentaires pour qu’il fonctionne sur les utilisateurs. Différences ou une mauvaise entre l’utilisateur et l’interface utilisateur peut entraîner l’utilisateur ne pas remarquer une action, ce qui peut avoir des conséquences inattendues. Souvent, l’erreur passe inaperçue jusqu'à ce que l’utilisateur ne voit que quelque chose est manquante ou a été modifié. Modèles de sélection sont donc un des éléments essentiels de conception de l’interface utilisateur. Bien que les modèles de sélection dans Visual Studio sont cohérentes avec Windows, il existe de légères variantes.  
  
 Dans Visual Studio, comme dans Windows, les modèles de sélection diffèrent selon le contexte dans lequel l’interaction se produit. Sélections peuvent se produire dans les quatre types d’objets :  
  
-   Texte  
  
-   Objets graphiques  
  
-   Listes et les arborescences  
  
-   Grilles  
  
 Au sein de ces objets, il existe trois types de sélections :  
  
-   Contiguës  
  
-   Disjoints  
  
-   Region  
  
#### <a name="scope"></a>Portée  
 Le composant le plus important de sélection est de s’assurer que l’utilisateur sait fenêtre dans laquelle ils travaillent (activation) et où le focus est située (sélection). Visual Studio étend les fonctionnalités de gestion de fenêtre dans Windows, mais le schéma d’activation est identique : interaction avec une fenêtre place le focus dans la fenêtre. Visual Studio a deux indicateurs pour l’activation : un pour les fenêtres de document et un pour les fenêtres Outil.  
  
 Pour les fenêtres de document, la fenêtre active est indiquée par un onglet de fenêtre de document entrant au premier plan et en modifiant sa couleur d’arrière-plan :  
  
 ![Sélection de l'onglet actif dans Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")  
  
 **Sélection de l’onglet actif**  
  
 Fenêtres Outil, la fenêtre active est indiquée par une modification de la couleur de la zone de barre de titre de la fenêtre outil :  
  
 ![Sélection de la fenêtre Outil active dans Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")  
  
 **Fenêtre outil Active montrant la sélection principale d’un nœud**  
  
 ![Sélection de la fenêtre Outil inactive dans Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")  
  
 **Fenêtre outil inactive, affichant une sélection du nœud**  
  
 Une fois qu’une fenêtre est active, son objectif est indiquée selon les modèles de sélection décrites dans cette section des lignes directrices.  
  
#### <a name="context"></a>Contexte  
 Visual Studio a été conçu pour conserver un fort concept de contexte, le suivi du où l’utilisateur travaille. Une seule fenêtre est active, s’il s’agit d’une outil ou fenêtre de document. Toutefois, la fenêtre de document au premier plan conserve toujours une sélection latente. Bien que le focus dans une fenêtre outil, la fenêtre de document qui était actif affiche une sélection, même dans un état inactif. Cela est fait pour conserver le contexte de l’utilisateur dans le document, qu'ils ont été modifié, leur indiquant que Visual Studio a conservé leur état afin qu’ils puissent renvoyer et déplacer en toute transparence entre les fenêtres Outil et les fenêtres de document.  
  
### <a name="text-selection"></a>Sélection de texte  
 Les éditeurs Visual Studio qui sont strictement textuels, tels que l’éditeur de texte intégré, utilisent le même modèle de sélection de texte et en apparence décrites dans le [la souris et des pointeurs](https://msdn.microsoft.com/en-us/library/dn742466.aspx) page des directives d’Interaction expérience utilisateur Windows sur MSDN. Le focus d’entrée dans l’éditeur de texte est indiqué par une barre verticale, appelée le point d’insertion. Le point d’insertion est un seul pixel épais et coloré en tant que l’inverse de l’élément qui apparaît derrière lui. Il clignote en fonction de la fréquence définie par le **clignotement du curseur** dans les **vitesse** onglet de la **clavier** applet du Panneau de configuration.  
  
#### <a name="contiguous-and-disjoint-selection"></a>Sélection contiguë et disjoint  
 Sélection dans l’éditeur de texte est contigue uniquement. De texte disjointes sélections ne sont pas autorisées, mais doivent être traitées dans les éditeurs de l’objet graphique. Lorsque le pointeur de la souris se trouve sur une zone de texte, le curseur se transforme en i. Un seul clic place le point d’insertion dans l’éditeur de texte à l’emplacement du clic. Le bouton de la souris enfoncé démarre la surbrillance de sélection et relâcher le bouton de la souris termine la surbrillance de sélection.  
  
#### <a name="region-selection-box-selection"></a>Sélection de zone (sélection de zone)  
 Visual Studio prend en charge les sélections de la région dans l’éditeur de texte, et il s’agit de sélection de zone. Sélection de zone permet à l’utilisateur de sélectionner une zone de texte qui ne respecte pas le flux de texte normal. Comme avec la sélection de texte standard, la sélection doit être contigue. Sélection de zone est lancée en maintenant la touche Alt enfoncée tout en faisant glisser la souris. Sélection de zone peut également être lancée en appuyant sur les touches Alt et MAJ tout en utilisant les touches de direction pour indiquer la région de sélection. Sélection de zone utilise la mise en surbrillance de sélection normale et affiche le curseur du point d’insertion clignote à la fin de la zone de sélection.  
  
 ![Régionales &#40 ; boîte &#41 ; sélection dans Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")  
  
 **Sélection de zone (zone) dans Visual Studio**  
  
#### <a name="text-selection-appearance"></a>Apparence de sélection de texte  
 Les couleurs utilisées pour la sélection active et inactive dans l’éditeur peuvent être personnalisés. Pour personnaliser l’apparence visuelle de l’éditeur, un utilisateur peut atteindre **Outils > Options**, puis regardez sous **environnement > polices et couleurs > Éditeur de texte**.  
  
### <a name="graphical-selection"></a>Sélection de graphique  
  
#### <a name="interaction"></a>Interaction  
 Sélection d’un objet graphique peut être complexe et dépend de plusieurs facteurs :  
  
-   **Modèle de sélection principale de l’éditeur.** Éditeurs qui contiennent des objets graphiques peuvent également servir à modifier du texte ou des grilles. Par exemple, l’éditeur peut être un éditeur de texte qui prend également en charge le positionnement des objets graphiques, tels que le concepteur Visual Studio XAML. Prise en charge de plusieurs types d’objets peut affecter comment l’utilisateur sélectionne les groupes de différents types d’objets.  
  
-   **Prise en charge des États de la sélection principale et secondaire.** Un éditeur peut fournir la sélection principale et secondaire États afin que les objets peuvent être modifiés de concert, alignés avec d’autres, redimensionné, et ainsi de suite.  
  
-   **Prise en charge de modification sur place.** Les éditeurs permettent également le contenu de leurs objets de graphique à modifier. Par exemple, une forme de rectangle peut contenir également le texte à l’intérieur qui peut être modifié par l’utilisateur. En outre, ce texte peut être centré ou justifié. Modification sur place implique un niveau plus détaillé de l’interaction utilisateur et nécessite donc un ensemble approprié de signaux visuels pour présenter des informations d’état à l’utilisateur.  
  
#### <a name="mouse-interaction"></a>Interaction souris  
  
|Entrée|Résultat|  
|-----------|------------|  
|Cliquez sur un objet non sélectionné|Sélectionne l’objet et affiche une ligne en pointillé et les poignées de sélection, si l’objet peut être redimensionnée.|  
|Cliquez sur un objet sélectionné|Active la modification sur place si l’objet prend en charge. Cliquant à l’extérieur de l’objet désactive le mode de modification sur place.|  
|Double-cliquez sur un objet|Ouvre le code-behind de l’objet à modifier et peut insérer un gestionnaire d’événements par défaut, le cas échéant.|  
|Pointez sur un objet|Remplace le pointeur par le curseur de déplacement. Apparence de l’objet, telles que sa couleur, ou la luminosité peut changer.|  
|Pointez sur une poignée de sélection|Remplace le pointeur par le curseur de redimensionnement. Pour les objets qui prennent en charge de la rotation, des poignées de sélection peuvent modifier le pointeur d’un curseur de rotation que le pointeur est positionné différemment (par exemple, déplacé éloignés) en ce qui concerne la poignée de sélection.|  
|Glisser|Même si l’objet n’est pas déjà sélectionné, remplace le pointeur par le curseur de déplacement et déplace l’objet.|  
|Éditeur perd le focus|Désactive le mode de modification sur place, bien que l’objet conserve le contenu et l’apparence qu’il avait lors de son dernier état de sélection d’opération.|  
|Sélection d’objets|Indiqué par une bordure, pointillés ou tout autre traitement visuellement distincte pour mettre en surbrillance les limites de l’objet.|  
|Redimensionner un objet sélectionné|Indiqué par les poignées de sélection.<br /><br /> Un objet redimensionnable possède huit poignées, représentant chaque direction dans laquelle il peut être redimensionné. Nombre de handles peuvent être utilisées si l’objet peut uniquement être redimensionné dans certaines directions. Lorsque l’utilisateur redimensionne un objet jusqu’où huit poignées ne serait pas interactives, quatre poignées peuvent ensuite être utilisées. Handle de tailles doivent être liées à la métrique de bordure et le bord de fenêtre avec la **GetSystemMetrics** fonction de l’API à la taille en fonction de la résolution d’affichage.<br /><br /> ![Poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|  
|Faire pivoter un objet sélectionné|![Poignées de rotation](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|  
  
#### <a name="keyboard-interaction"></a>Interaction du clavier  
  
|Entrée|Résultat|  
|-----------|------------|  
|Onglet|Déplace l’indicateur de focus entre l’ordre logique des objets dans l’éditeur. Cela peut être de gauche à droite ou de haut en bas en fonction de **TabIndex** (ou équivalent) valeur de la propriété, l’ordre de création d’objet et l’objectif global de l’éditeur. Maj + Tab inverse le sens de l’indicateur de focus.|  
|Barre d’espacement|Active le mode panoramique tandis que la séquence de touches est conservée. Entrée de souris supplémentaire est nécessaire pour effectuer un panoramique de la position de la fenêtre d’affichage.|  
|Ctrl+Barre d'espace|Active le mode de zoom tandis que la séquence de touches est conservée. Entrée de souris supplémentaire est nécessaire pour augmenter et diminuer le facteur de zoom.|  
|Ctrl + Alt + signe moins|Réduit le facteur de zoom d’un niveau.|  
|Ctrl + Alt + signe Plus|Augmente le facteur de zoom d’un niveau.|  
|MAJ ou Ctrl|Ajoute l’objet au groupe de sélection. CTRL vous permet également de vous permet de supprimer les objets individuellement à partir du groupe de sélection.|  
|Touche Entrée|Exécute la commande par défaut pour l’objet (généralement ouvrir ou modifier).|  
|F2|Active la modification sur place pour l’objet.|  
|Touches de direction|Déplace les objets sélectionnés dans le sens de la touche enfoncée, par petits incréments (par exemple, de 1 pixel à la fois)|  
|CTRL + touches de direction|Déplace les objets sélectionnés dans le sens de la touche enfoncée, plus vite (par exemple, 10 pixels à la fois)|  
|Maj + flèche clés|Redimensionne les objets sélectionnés dans le sens respectif, par petits incréments (par exemple, de 1 pixel à la fois)|  
|CTRL + MAJ + touches de direction|Redimensionne les objets sélectionnés sur l’axe respectif, en incréments de grande taille (par exemple, 10 pixels à la fois)|  
  
 Lorsque les utilisateurs modifient des contrôles en place, il peut être utile pour les objets à redimensionner automatiquement avec l’entrée d’utilisateur. Par exemple, si l’utilisateur modifie un contrôle d’étiquette, l’étiquette doit atteindre pour afficher le texte saisi par l’utilisateur uniquement. Si vous ne le faites pas, l’utilisateur doit redimensionner le contrôle manuellement après avoir modifié le texte. Si l’utilisateur possède un grand nombre de contrôles, cela devient un tâches répétitives et les tâches non productives.  
  
#### <a name="graphical-containers"></a>Conteneurs graphiques  
 Dans certains cas, les éditeurs graphiques fournissent des conteneurs pour d’autres objets graphiques, tels que le contrôle Panel Windows Forms ou le contrôle de disposition de grille dans le Concepteur HTML. Si votre éditeur fournit des conteneurs pour d’autres objets graphiques, le modèle de sélection suivantes doit être utilisé pour le conteneur uniquement (les objets dans le suivi de conteneur du modèle standard comme décrit ci-dessus) :  
  
|Entrée|Résultat|  
|-----------|------------|  
|Cliquez sur le conteneur|Sélectionne l’objet conteneur sans sélectionner directement les objets de relation contenant-contenu. Le conteneur peut-être être déplacé et/ou redimensionné avec la souris et clavier (comme décrit ci-dessus). Objets contenus sont déplacés par rapport au conteneur, mais les objets qu’il contient ne sont pas redimensionnées, sauf si elles sont sélectionnées directement.|  
|Pointez sur une région de limite du conteneur|Active la souris dans le curseur de déplacement, indiquant que le conteneur peut être déplacé.|  
|Faites glisser la zone de bordure du conteneur|Modifie la souris pour le déplacement de curseur et déplace le conteneur (et les objets contenus dans). Le conteneur ne peut pas être déplacé sans d’abord sélectionné en un seul clic.|  
|Cliquez sur un objet dans le conteneur|Désactive le conteneur (si) et sélectionne uniquement l’objet sélectionné.|  
|MAJ + cliquez sur OR Ctrl + cliquez sur un objet contenu et/ou d’un conteneur|Ajoute l’objet sélectionné à une sélection ou un groupe de sélection. Si l’objet sélectionné est déjà membre du groupe de sélection, il est supprimé du groupe de sélection.|  
  
 Les objets contenus doivent respecter le modèle de sélection de base comme décrit dans la section précédente. Test de la facilité d’utilisation du Concepteur Windows Forms, les utilisateurs prévu un accès transparent à ces objets sans étapes intermédiaires (imposées par l’objet de relation contenant-contenu).  
  
#### <a name="disjoint-and-region-selections"></a>Disjointes et sélections de région  
 Éditeurs de l’objet graphique doivent prendre en charge les sélections disjointes. Veuillez noter que ce graphique n’affiche pas l’apparence du contrôle pour Visual Studio. Consultez [apparence de sélection d’objet graphique](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) des spécifications visual détaillées.  
  
 ![Sélecteurs de régions et disjoints](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")  
  
 **Sélection distincte**  
  
 Éditeurs de graphique doivent également fournir des sélections de région avec un indicateur de sélection de type texte défilant. Si l’éditeur graphique prend en charge d’autres types d’objet (par exemple, texte), les sélections de région ne peut-être pas possibles selon les contraintes de ces autres types d’objet.  
  
 ![Sélection de texte défilant](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")  
  
 **Sélection de texte défilant**  
  
#### <a name="primary-and-secondary-selections"></a>Sélections principale et secondaires  
 Certains éditeurs de l’objet graphique autoriser l’utilisateur à modifier ou à aligner des objets dans des groupes. Dans ce cas, le concept de sélections principale et secondaires doit être introduits. La sélection principale est l’objet auquel tous les autres objets répondent pour les opérations de groupe. L’objet que l’utilisateur sélectionne le premier devient le contrôle principal et les sélections suivantes deviennent les sélections secondaires. La sélection principale a un traitement visual distinct à partir de l’ou des sélections secondaires pour indiquer quel est l’objet principal :  
  
 ![Sélection principale et secondaire](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")  
  
 **Sélection principale avec deux sélections secondaires**  
  
####  <a name="a-namebkmkgraphicalobjectselectionappearancea-graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a> Apparence de sélection d’objet graphique  
 Les poignées sont des carrés dans un rectangle autour de la zone englobante de l’objet. Le tableau ci-dessous montre des exemples des différents États qu’un objet graphique peut avoir avec poignée, dimensionnement et apparence modification sur place. La taille des poignées doit être liée à la bordure de fenêtre et les mesures de bord à l’aide du **GetSystemMetrics** API.  
  
|État|Apparence|Détails visuels|  
|-----------|----------------|--------------------|  
|**Non sélectionné**|Par défaut|![État du bouton par défaut](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState")||  
|**Sélection principale**|Redimensionnement|![Sélection principale avec des poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize")|![Sélection principale avec redimensionner les poignées &#40 ; Zoom &#41 ;](../../extensibility/ux-guidelines/media/0713-12_primaryresizezoom.png "0713-12_PrimaryResizeZoom")|  
|**Sélection principale**|Pas redimensionnables|![Sélection principale sans poignées de redimensionnement](~/extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize")|![Sélection principale sans redimensionner les poignées &#40 ; Zoom &#41 ;](../../extensibility/ux-guidelines/media/0713-14_primarynoresizezoom.png "0713-14_PrimaryNoResizeZoom")|  
|**Sélection principale**|Verrouillé|![Sélection principale verrouillée](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked")|![Sélection principale verrouillée &#40 ; Zoom &#41 ;](../../extensibility/ux-guidelines/media/0713-16_primarylockedzoom.png "0713-16_PrimaryLockedZoom")|  
|**Sélection secondaire**|Redimensionnement|![Sélection secondaire avec des poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize")|![Sélection secondaire avec redimensionner les poignées &#40 ; Zoom &#41 ;](~/extensibility/ux-guidelines/media/0713-18_secondaryresizezoom.png "0713-18_SecondaryResizeZoom")|  
|**Sélection secondaire**|Pas redimensionnables|![Sélection secondaire sans poignées de redimensionnement](~/extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize")|![Sélection secondaire sans redimensionnement &#40 ; Zoom &#41 ;](~/extensibility/ux-guidelines/media/0713-20_secondarynoresizezoom.png "0713-20_SecondaryNoResizeZoom")|  
|**Sélection secondaire**|Verrouillé|![Sélection secondaire verrouillée](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked")|![Sélection secondaire verrouillée &#40 ; Zoom &#41 ;](../../extensibility/ux-guidelines/media/0713-22_secondarylockedzoom.png "0713-22_SecondaryLockedZoom")|  
|**Interface Utilisateur active**|Par défaut|![État actif de l'interface utilisateur](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive")|![L’interface Utilisateur état actif &#40 ; Zoom &#41 ;](../../extensibility/ux-guidelines/media/0713-24_uiactivezoom.png "0713-24_UIActiveZoom")|  
  
### <a name="view-selection-models"></a>Afficher les modèles de sélection  
  
#### <a name="tree-view"></a>Arborescence  
 Sélection dans une arborescence est affichée avec une simple mise en surbrillance. Si l’utilisateur clique sur un nom de nœud ou une icône de nœud, le nœud est sélectionné. Les glyphes triangulaires à gauche du nœud développer ou de contrat de l’arborescence, mais n’affectent pas la sélection de l’utilisateur, à une exception près : lors de la réduction d’un nœud parent lorsque la sélection se trouve sur un enfant de ce nœud, la sélection se déplace vers le parent.  
  
 ![Arborescence classique dans Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")  
  
 **Arborescence classique dans Visual Studio**  
  
 Vues de l’arborescence peuvent prendre en charge les sélections contigues et disjointes, même à travers plusieurs niveaux dans l’arborescence. Contiguës ou disjoints plusieurs sélections doivent être effectuées sur les nœuds d’arbre visible. Si un nœud est réduit, la sélection distincte est perdue et le nœud qui a été réduit Obtient la sélection. De cette façon, l’utilisateur peut voir les nœuds qui seront affectés par une opération. Lorsque les nœuds sont réduits, il devient difficile de savoir quels nœuds peuvent être affectées.  
  
 Lorsqu’un nœud parent est sélectionné, l’opération doit s’appliquer à la page parente, s’il peut y avoir des cas où il est préférable pour une opération à appliquer au disque parent et tous ses enfants. Dans ce cas, fournissent l’interface Utilisateur supplémentaire pendant l’opération, tel qu’une case à cocher ou de la boîte de dialogue de confirmation que l’option « appliquer à tous les enfants » explicites à l’utilisateur.  
  
##### <a name="renaming"></a>Changement de nom  
 Si les nœuds dans l’arborescence prennent en charge le changement de nom, le changement de nom doit être effectuée en place. L’opération de déplacement doit être standard sur tous les contrôles d’arborescence dans Visual Studio. Fournir une commande rename immédiatement Active le mode de modification sur place, avec la sélection de texte couvrant l’intégralité du nom du nœud, prêt à accepter une entrée utilisateur. Si le nœud représente un fichier, le nom de fichier doit contenir l’extension. La surbrillance de sélection doit inclure uniquement le corps du nom de fichier et non son extension.  
  
|Entrée|Résultat|  
|-----------|------------|  
|Entrée (touche)|Valide l’opération de changement de nom|  
|Touche ÉCHAP|Annule l’opération de changement de nom|  
|En cliquant sur la région d’édition|Valide l’opération de changement de nom|  
|Annuler|Fournir facilement Annuler pour annuler l’opération de changement de nom|  
  
#### <a name="selection-within-lists-and-grid-controls"></a>Sélection dans les listes et des contrôles de grille  
 Le concept clé dans la sélection de la liste est qu’il est basé sur la ligne, ce qui signifie que lorsqu’une sélection est effectuée à la ligne entière est sélectionné en tant qu’unité. En revanche, grilles peuvent autoriser des cellules spécifiques à sélectionner sans affecter tous les autres aspects de la ligne. Grilles peuvent également contenir une hiérarchie de lignes imbriquées (comme dans un contrôle TreeGrid) qui permettent ensemble branches de la hiérarchie sélectionnée et désélectionnée en interagissant avec les lignes parentes. Sélection dans les listes est indiquée par une couleur de surbrillance simple sur toute la ligne de données. Le focus est indiqué par une bordure en pointillés pixels autour de la ligne modifiable actuelle ou d’une cellule (ligne si toutes les cellules sont en lecture seule).  
  
> [!NOTE]
>  **Focus** et **sélection** sont des concepts différents. *Focus* indique de quelle interface Utilisateur de l’élément cible pour recevoir une entrée qui ne sont pas explicitement dirigée vers un autre objet, tandis que *sélection* fait référence à l’état d’inclusion d’un objet dans un ensemble d’objets sur lesquels les opérations suivantes peuvent avoir lieu.  
  
 Les sélections dans les listes peuvent être contiguës, disjoint, ou une région. Lorsque plusieurs sélections sont autorisées, contiguës et sélection distincte doit toujours être pris en charge, lors de la prise en charge des sélections de zone (zone) sont facultative. Les sélections de région sont initiées en faisant glisser dans l’espace blanc du corps de la liste.  
  
|Objet|Sélection|  
|------------|---------------|  
|Liste|Contiguës|Toujours pris en charge (sélections multiples sont autorisées).|  
|Liste|Disjoints|Toujours pris en charge (sélections multiples sont autorisées).|  
|Liste|Region|Prise en charge facultative. Lancé en faisant glisser la souris dans l’espace blanc du corps de la liste.|  
  
 Cliquez une fois sur une liste sélectionne la ligne où le clic s’est produit. Si l’utilisateur venait à cliquer dans une cellule de liste qui prend en charge la modification sur place, la cellule est immédiatement activée pour la modification sur place. Sinon, la ligne entière est immédiatement sélectionnée et affiche une mise en surbrillance.  
  
 Faire glisser dans le corps de la liste effectue l’une des trois choses :  
  
-   Lance une sélection de région, si la liste prend en charge et le bas de la souris se trouve dans un espace blanc  
  
-   Initie une opération de glisser-déplacer si la cellule ou la ligne prend en charge en cours d’une source de glissement  
  
-   Sélectionne la ligne actuelle  
  
##### <a name="in-place-editing"></a>Modification sur place  
 Lors de la modification sur place est autorisée, il existe deux modèles de base : sélecteur de contrôle et la propriété Edition simple. Avec un contrôle d’édition simples, le contenu est mis en surbrillance et prêt pour l’utilisateur d’entrée dès que la modification sur place est activée. Lorsqu’un sélecteur de propriété est implémenté, le bouton qui appelle le sélecteur de propriétés s’affiche une fois que le mode de modification sur place est activé et la sélection actuelle n’est pas mis en surbrillance. Le bouton de sélecteur doit être aligné à droite dans la cellule. Pour des exemples de modification sur place, consultez la **fenêtre Propriétés** et **liste des tâches** dans Visual Studio.  
  
##### <a name="keyboard-support"></a>Prise en charge du clavier  
 Prise en charge du clavier pour la sélection dans les listes et les grilles suit les conventions Windows :  
  
-   Touches de direction parcourir la liste, en sélectionnant chaque cellule/ligne lorsque le focus est déplacé.  
  
-   Maj + flèche effectue une sélection contiguë dans le sens des touches de direction.  
  
-   Ctrl + flèche suivie des bascules d’espace entre l’ajout et suppression d’éléments de la sélection, la création d’une sélection distincte.  
  
-   Pour les grilles qui contiennent des hiérarchies imbriquées, la touche droite développe une ligne parente, et la touche de direction gauche réduit un.  
  
-   La touche Tab déplace le focus entre les cellules de la ligne actuelle si les cellules sont modifiables.  
  
-   La touche entrée exécute la commande par défaut sur l’élément dans la liste (souvent **Open**).  
  
-   La touche F2 Active la modification sur place pour la cellule actuellement sélectionnée.  
  
##  <a name="a-namebkmkpersistenceandsavingsettingsa-persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a> Persistance et l’enregistrement des paramètres  
  
### <a name="overview"></a>Vue d'ensemble  
 Bien que chaque composant logiciel dans Visual Studio est généralement responsable de son propre état et la persistance, Visual Studio enregistre automatiquement les paramètres dans certains cas, comme avec les positions et les tailles de fenêtre. Le tableau ci-dessous est une combinaison de paramètres enregistrés automatiquement et qui requièrent un utilisateur explicit ou programmé l’action à entreprendre.  
  
|Objet|Les éléments à enregistrer|Quand l’enregistrer|Emplacement d’enregistrement|  
|------------|------------------|------------------|-------------------|  
|Objet sélectionnable (par exemple, une ligne de code)|Un point d’arrêt sur une ligne de code<br /><br /> Un raccourci de l’utilisateur associé à la ligne de code|Lorsque le projet est enregistré.|Le **options utilisateur (.suo)** fichier pour le projet|  
|Boîte de dialogue|L’emplacement de la boîte de dialogue, s’il a été déplacé<br /><br /> La vue que l’utilisateur a utilisé la boîte de dialogue|Lorsque la boîte de dialogue se ferme<br /><br /> Lorsque la session de Visual Studio se termine|Dans la mémoire<br /><br /> Registre **HKEY_Current_User**|  
|Fenêtre|La taille et l’emplacement de la fenêtre|Lorsque la fenêtre se ferme<br /><br /> Lorsque le mode de Visual Studio modifie<br /><br /> Lorsque la session de Visual Studio se termine|Le **options utilisateur (.suo)** fichier pour le projet<br /><br /> Fichier d’options personnalisées pour les paramètres de fenêtre|  
|Document|La sélection actuelle dans le document<br /><br /> L’affichage du document<br /><br /> Les dernière plusieurs emplacements visité de l’utilisateur|Lorsque le document est enregistré.|Le **options utilisateur (.suo)** fichier pour le projet|  
|Projet|Références aux fichiers<br /><br /> Références à des répertoires sur le disque<br /><br /> Références à d’autres logiciels<br /><br /> Composants<br /><br /> Informations d’état sur le projet lui-même|Lorsque le projet est enregistré.|Le fichier de projet|  
|Solution|Références aux projets<br /><br /> Références aux fichiers|Lorsque la solution ou le projet est enregistrée|Le **solution (.sln)** fichier|  
|Paramètres de **Outils > Options**|Personnalisations de clavier<br /><br /> Personnalisations de la barre d’outils<br /><br /> Jeux de couleurs|Lorsque le **Outils > Options** boîte de dialogue se ferme<br /><br /> Lorsque la session de Visual Studio se termine|Registre **HKEY_Current_User**|  
  
 Ce que fait l’utilisateur et lorsqu’ils font, détermine si un paramètre est enregistré dans la mémoire (pendant la session), enregistré sur le disque (via des sessions sous la forme d’un paramètre du Registre), en tant que partie du fichier projet ou solution lui-même, dans le cadre de la **options de solution (.suo)** de fichiers, ou que des paramètres personnalisés de fichiers seulement ce composant logiciel connaît. Le tableau ci-dessus montre plusieurs événements à laquelle les paramètres peuvent être enregistrés. Toutefois, il existe d’autres cas dans lesquels vous souhaiterez enregistrer l’état :  
  
-   Lorsque l’utilisateur modifie l’emplacement au sein d’une fenêtre ou boîte de dialogue  
  
-   Lorsque l’utilisateur transfère le focus vers une autre fenêtre  
  
-   Lorsque l’utilisateur bascule de la conception au mode de débogage  
  
-   Lorsque l’utilisateur se déconnecte leur compte  
  
-   Lorsque l’ordinateur en veille prolongée ou s’arrête  
  
-   Lorsque le disque dur / l’ordinateur est sur le point d’être reformaté et configurer de nouveau  
  
### <a name="window-configurations"></a>Configurations de fenêtres  
 Une configuration de fenêtres est la présentation de l’environnement de développement de base : c’est un jeu composé de la liste des fenêtres Outil présents et celui dans lequel ils sont organisés. Pour windows gérés par l’IDE (IDE windows), les informations de mise en page sont conservées par utilisateur, donc lorsqu’un utilisateur lance l’IDE, la disposition de fenêtre s’affiche, le même que lors de la dernière sortie Visual Studio. L’état et la position des fenêtres de l’IDE est rendue persistante dans un fichier d’options personnalisées au format XML. Les fenêtres Outil qui sont créés par les packages chargés dans l’IDE conserver leurs informations d’état dans le Registre et ne peuvent pas forcément par utilisateur.  
  
#### <a name="profile-specific-layouts"></a>Dispositions spécifiques au profil  
 Chaque profil inclut des dispositions de fenêtres Outil, organisées de façon familière aux acteurs de développeur spécifique (les développeurs Visual C++ vous attendre à voir la **l’Explorateur de solutions** sur le côté gauche de l’IDE, tandis que les développeurs c# vous attendre à voir la **l’Explorateur de solutions** sur la droite). Dispositions de fenêtres de profil spécifiques sont chargées une fois que l’utilisateur sélectionne un profil au démarrage. Auteur d’un package doit déterminer la disposition des fenêtres plus appropriée pour l’expérience de leurs clients, sachant que les modifications apportées par l’utilisateur à la configuration de la fenêtre sont ensuite rendues persistantes.  
  
##  <a name="a-namebkmktouchinputa-touch-input"></a><a name="BKMK_TouchInput"></a> Entrée tactile  
 Les utilisateurs ont recours à des produits de développement Microsoft sur les appareils tactiles. Toutefois, il existe des obstacles qui le rendent difficile à utiliser les outils de développement sur les appareils tactiles. Les utilisateurs s’attendent à nos produits pour fournir une expérience tactile fiable et précise. L’objectif de ces instructions consiste à indiquer des décisions sur les fonctions tactiles à intégrer et à encourager une expérience tactile cohérente entre Visual Studio et les produits connexes.  
  
### <a name="levels-of-experience"></a>Niveaux d’expérience  
 Les niveaux d’expérience ci-dessous sont destinées à servir de guide pour aider les équipes à déterminer les fonctions tactiles à offrir en fonction de leur niveau souhaité d’intérêt d’investissement en contact.  
  
-   Le **expérience de base** est pour les équipes qui souhaitent fournir les fonctionnalités tactiles il n’y pas d’ends mortes tout au long de leur travail.  
  
-   Le **optimisé expérience** pour les équipes qui souhaitent permettent le plus commun tactile (par exemple, ceux généralement disponibles dans les applications de navigateur internet).  
  
-   Les **élevées expérience** est pour les équipes qui souhaitent ajouter des fonctionnalités telles que mouvements ou autres fonctionnalités facultatives qui peuvent rendre leurs applications tactiles d’abord convivial.  
  
||Expérience de base|Expérience optimisée|Expérience avec élévation de privilèges|  
|-|----------------------|--------------------------|-------------------------|  
|Permet aux utilisateurs de...|Corriger le code et solution/projet-lecture sans mortes terminaisons|Effectuer des tâches de maintenance, refactorisations qu’et navigation|Fonctionner en une expérience cohérente, intuitive et fluide en toute confiance|  
|Éditeur|Mouvement panoramique tactile et sélection<br /><br /> Tactile de barre de défilement pour accéder et appuyez sur + faire glisser|Zoom de pincement<br /><br /> Défilement rapide<br /><br /> Sélection<br /><br /> Utilisation simple de menu contextuel||  
|Fenêtres d’outils supérieure|Panoramique de la liste<br /><br /> Sélection d’éléments<br /><br /> Tactile de barre de défilement pour accéder et appuyez sur + faire glisser|Élément facilement le défilement et la sélection||  
|Fenêtrage||Redimensionner la fenêtre<br /><br /> Accès rapide||  
|Document bien||Facilite la navigation entre les fichiers ouverts||  
|Mouvements||Vérifiez que mouvements courants fonctionnent dans l’IDE|Actions basées sur les mouvements<br /><br /> Prise en charge du glisser-déplacer et les concepteurs|  
|Autres considérations|||Clavier visuel personnalisé|  
  
#### <a name="gestures"></a>Mouvements  
 Mouvements de fournissent aux utilisateurs un raccourci pour les commandes qui pourraient nécessiter une interaction plus complexe. Reportez-vous aux instructions de Windows sur [tactiles commun pour les Applications de bureau](http://msdn.microsoft.com/en-us/library/windows/desktop/dd940543\(v=vs.85\).aspx), et suivre ces instructions pour la plupart des gestes, y compris les gestes simples telles que le panoramique et le zoom.