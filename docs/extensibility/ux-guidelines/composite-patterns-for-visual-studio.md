---
title: Modèles de composite pour Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6515b5aefc0536ea92f09a92b1a17050b820008d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148949"
---
# <a name="composite-patterns-for-visual-studio"></a>Modèles de composite pour Visual Studio
Modèles composites combinent des éléments de conception et d’interaction dans des configurations distinctes. Les modèles composites plus importantes dans Visual Studio en matière de cohérence sont les suivantes :  
  
-   [Visualisation des données](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)  
  
-   [L’interface utilisateur sur l’objet et la lecture](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
-   [Modèles de sélection](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
-   [Persistance et l’enregistrement des paramètres](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
-   [Entrée tactile](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)  
  
##  <a name="BKMK_DataVisualization"></a> Visualisation des données  
  
### <a name="overview"></a>Vue d'ensemble  
 Les graphiques sont un moyen visuel d’agrégation et de visualiser les données afin d’améliorer la prise de décision. Elles peuvent aider les utilisateurs confrontés à une grande quantité de données, mais ce qui signifie peu voir qu’ils méritent une attention et besoins une action.  
  
 L’utilisateur tire parti d’un graphique, si une des conditions suivantes est vraie :  
  
-   Le graphique permettra aux utilisateurs identifier les tâches qu’ils peuvent agir sur ?  
  
-   Le graphique permettra aux utilisateurs de prévoir les conséquences d’une modification éventuelle ?  
  
-   Sera le graphique aider les utilisateurs à découvrir des tendances et identifier des modèles ?  
  
-   Le graphique permettra aux utilisateurs de prendre de meilleures décisions ?  
  
-   Le graphique aidera à répondre à une question spécifique que les utilisateurs devront peut-être dans le contexte donné ?  
  
#### <a name="general-rules-for-charts"></a>Règles générales pour les graphiques  
  
-   Clairement les données d’étiquette. Illustrations sans aucune explication sont simplement de belles images.  
  
-   Démarrer les axes à zéro pour éviter les proportions d’inclinaison. Taille de la longueur et de la barre de ligne sont des signaux visuels importants pour comprendre les relations entre les points de données.  
  
-   Créer des graphiques, pas graphisme d’information. Graphisme d’information est des représentations artistiques des données, et leur objectif principal est une narration visual. Les graphiques peuvent (et doivent) être visuellement attrayante, mais laisser les données parlent d’elles-mêmes.  
  
-   Évitez de skeumorphism, la représentation graphique des graphiques à barres, contraste hashmarks et autres touches finales, le graphisme d’information.  
  
-   N’utilisez pas d’effets 3D comme un élément décoratif. Utilisez-les uniquement si elles réellement partie intégrante de la capacité de l’utilisateur à comprendre les informations.  
  
-   Évitez d’utiliser plusieurs lignes et remplissages, en plus de deux couleurs peuvent rendre ce type de graphique difficile à lire et interpréter correctement.  
  
-   N’utilisez pas d’un graphique (ou n’importe quel illustration) comme le seul moyen de comprendre un concept ou l’interaction avec les données. Cela pose des difficultés pour les utilisateurs ayant des troubles visuels.  
  
-   N’utilisez pas les graphiques en tant qu’éléments gratuites ou décoratifs sur une page. En d’autres termes, si un graphique n’ajoute pas tous les utilisateurs de la valeur ou à l’aide à résoudre un problème, ne l’utilisez.  
  
### <a name="chart-types"></a>Types de graphiques  
 Types de graphiques utilisées dans Visual Studio incluent des graphiques à barres, graphiques en courbes, un graphique à secteurs modifié appelé « graphique en anneau, « chronologies, les graphiques en anneau ou en nuage de points tracés (également appelés « cluster graphiques ») et des diagrammes de Gantt. Chaque type de graphique est utile pour la communication d’un autre type d’informations.  
  
### <a name="other-charting-considerations"></a>Autres considérations relatives à la création de graphiques  
  
#### <a name="color"></a>Color  
 Il existe une palette spécifique du graphique des couleurs sont définies pour une utilisation dans Visual Studio. La palette est accessible pour les principaux types de personnes et les couleurs peuvent être différenciés même lorsqu’elle sert de secteurs très étroits de couleur. Vous pouvez utiliser ces couleurs dans n’importe quelle combinaison de tout type de graphique dans votre interface utilisateur. Vous n’avez pas besoin d’utiliser toutes les couleurs de sept si vous n’avez pas besoin que de nombreuses couleurs distinctes. Ces couleurs ne sont pas conçus pour être utilisé avec tous les éléments de premier plan, donc vous ne placez ne pas de texte ou des glyphes sur ces couleurs. Ces teintes doivent être codé en dur et exposés à la personnalisation par l’utilisateur sous **Outils > Options** (consultez [exposant des couleurs pour les utilisateurs finaux](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).  
  
|Échantillon|Hex|RVB|  
|------------|---------|---------|  
|![Échantillon 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|  
|![Échantillon BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|  
|![Échantillon FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|  
|![Échantillon 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|  
|![Échantillon 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|  
|![Échantillon 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|  
|![Échantillon B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|  
  
##  <a name="BKMK_OnObjectUI"></a> L’interface utilisateur sur l’objet et la lecture  
 Cette section donne le contexte pour la lecture, également appelé mode de lecture de code, un type d’interface utilisateur sur les objets spécifique à Visual Studio.  
  
### <a name="overview"></a>Vue d'ensemble  
  
-   L’interface utilisateur sur l’objet doit fournir l’utilisateur plus d’informations ou l’interactivité sans lui leur tâche principale.  
  
-   Le modèle principal pour l’interface utilisateur sur les objets dans Visual Studio est appelé « informations au point d’une attention ».  
  
-   L’interface utilisateur sur l’objet dans Visual Studio est soit inline ou flottant et durable ou temporaire.  
  
    -   Mode de lecture du code, un type de l’interface utilisateur sur les objets dans Visual Studio, est en ligne et durable.  
  
    -   CodeLens, un type de l’interface utilisateur sur les objets dans Visual Studio, est à virgule flottante et temporaires  
  
 Comprendre le fonctionne d’un fragment de code, ou rechercher des informations sur ce code, requiert souvent un développeur changer de contexte et accédez à tout autre contenu ou d’une autre fenêtre. Ces équipes de contexte peuvent être sans interruption, car les utilisateurs peuvent perdre le focus sur leur tâche d’origine s’ils quittent leur fenêtre principale. En outre, l’obtention de qu’arrière de contexte d’origine peut être difficile, surtout si le basculement de windows a provoqué son code d’origine être masquées par toute autre interface utilisateur.  
  
 L’interface utilisateur sur l’objet suit un modèle appelé « informations au point d’une attention ». Ces messages, fenêtres et boîtes de dialogue permettent aux utilisateurs des informations supplémentaires pertinentes qui ajoute une clarification ou l’interactivité sans perdre le focus sur leur tâche principale. Exemples de l’interface utilisateur sur les objets incluent les fenêtres indépendantes qui s’affichent lorsqu’un utilisateur place le pointeur sur une icône dans la zone de notification, la ligne ondulée rouge sous un mot mal orthographié et la vue Aperçu introduite dans Visual Studio 2013.  
  
### <a name="decision-points"></a>Points de décision  
 Dans Visual Studio, il existe plusieurs façons d’utiliser ce modèle d’informations dans la phase de votre attention. En choisissant le mécanisme de droite et de mise en œuvre d’une manière cohérente et prévisible sont essentiel de l’expérience globale. Dans le cas contraire, les utilisateurs peuvent s’afficher avec une expérience de confusion ou incohérente porte atteinte le focus à partir du contenu proprement dit.  
  
#### <a name="relationships-between-master-and-detail-content"></a>Relations entre maître / détail contenu  
 Informations au point d’une attention particulière sont utilisées pour afficher une relation entre le contenu que l’utilisateur se concentrent sur (le contenu « maître ») et d’autres concerne le contenu (le contenu de « détail »). Dans ce modèle, le contenu de détail concerne clairement le contenu de l’utilisateur travaille avec et peut être affiché proche du contenu principal. Informations supplémentaires ou des informations qui ne peuvent pas être résumées sans surcharger le contenu principal doivent suivre un autre modèle, telle qu’une fenêtre outil.  
  
-   **Toujours** afficher le contenu de détail à proximité du contenu principal.  
  
-   **Toujours** Assurez-vous que le contenu de détail permet toujours d’un utilisateur à rester concentré sur le contenu principal. Souvent, la meilleure façon d’effectuer cette opération est rendu du contenu de détail comme proche le contenu principal que possible. Cela est possible en les affichant le contenu de détail dans une fenêtre indépendante en regard du contenu principal, ou en les affichant le contenu en détail ligne sous le contenu principal.  
  
-   **Jamais** utiliser les informations dans la phase d’attention qui dirige l’utilisateur en s’éloignant de contenu principal. Si les utilisateurs ont besoin afficher le contenu de détail séparément, exposer une action explicite qui permet à l’utilisateur pour ce faire.  
  
#### <a name="design-details"></a>Détails de la conception  
 Une fois que vous avez déterminé que l’interface utilisateur sur l’objet est le bon choix, il existe quatre considérations de conception principale :  
  
1.  **Persistance :** le contenu doit être durable ou temporaire ?   
    Les utilisateurs voudrez garder les informations visibles pour faire référence à ou interagir avec ? Ou, les utilisateurs souhaiteront aperçu rapidement les informations et poursuivez leur tâche principale ?  
  
2.  **Type de contenu :** le contenu sera d’information, utilisables ou navigation ?   
    L’utilisateur n’a besoin des détails supplémentaires sur le contenu principal ? L’utilisateur a-t-il besoin pour effectuer une tâche qui affecte le contenu principal ? Ou bien, l’utilisateur doit être dirigé vers une autre ressource ?  
  
3.  **Type d’indicateur :** n’a un indicateur ambiant sens ?   
    Les informations sont résumées dans une méthode utile et sans surcharger le contenu principal ?  
  
4.  **Mouvements :** mouvements de ce qui sera utilisé pour appeler et ignorer l’interface utilisateur ?   
    Comment l’utilisateur affiche le contenu de détail et envoyer immédiatement ? Existe-t-il des valeur lors de l’ajout d’un mouvement telles que l’épinglage pour basculer entre les états transitoires et durables ?  
  
 Chacun de ces points de quatre décision aura un impact sur les principaux composants de l’interface utilisateur de l’objet.  
  
### <a name="on-object-ui-components"></a>Composants d’interface utilisateur sur l’objet  
  
1.  Type de conteneur (présentateur de contenu)  
  
    -   Virgule flottante  
  
    -   Inline  
  
2.  Type de contenu  
  
    -   Information : les données qui peuvent être statiques ou dynamiques  
  
    -   Utilisables : commandes qui modifient le contenu principal  
  
    -   Navigation : des liens qui dirige l’utilisateur vers une autre fenêtre ou une application, telles que MSDN  
  
3.  Mouvements  
  
    -   Invocation  
  
    -   Renvoi  
  
    -   Épinglage  
  
    -   Autres interactions  
  
4.  Modèle de persistance et de validation  
  
    -   Transient  
  
    -   Durable  
  
    -   Automatique  
  
    -   À la demande  
  
5.  Indicateurs ambiantes (facultatifs)  
  
    -   Soulignement de trait de soulignement ondulé  
  
    -   Icône de balise active  
  
    -   Autres indicateurs ambiantes  
  
#### <a name="container-content-presenter-type"></a>Type de conteneur (présentateur de contenu)  
 Il existe deux principales options disponibles pour présenter un contenu au point d’attention :  
  
1.  **Inline :** un présentateur inline, telles que la vue Aperçu qui a été introduit dans l’éditeur de Code Visual Studio 2013, rend l’espace pour le nouveau contenu par le passage du contenu existant.  
  
    -   **Préférez** présentateurs inline si vous pensez que les utilisateurs souhaitent beaucoup de temps faisant référence à ou d’interagir avec le contenu que vous présentez.  
  
    -   **Éviter** présentateurs inline si vous pensez que les utilisateurs souhaiterez œil les informations vous présentez, puis poursuivez leur tâche principale avec une perturbation minimale.  
  
2.  **Flottant :** présentateur flottant est positionné aussi proche au contenu sélectionné en tant que possible, mais ne modifie pas la disposition du contenu existant. Différentes stratégies peuvent être utilisés, comme l’affichage d’un panneau flottant de contenu sur le plus proche de l’espace blanc au symbole sélectionné.  
  
    -   **Préférez** flottante présentateurs si vous pensez que les utilisateurs souhaiterez œil les informations vous présentez, puis poursuivez leur tâche principale avec une perturbation minimale.  
  
    -   **Éviter** flottante présentateurs si vous pensez que les utilisateurs souhaiterez beaucoup de temps faisant référence à ou d’interagir avec le contenu vous intéresse.  
  
#### <a name="content-type"></a>Type de contenu  
 Il existe trois principaux types de contenu qui peuvent être affichés à l’intérieur de n’importe quel conteneur de l’interface utilisateur sur l’objet. N’importe quelle combinaison de ces types d’informations peut être affiché. Les trois types sont :  
  
1.  **Information :** la plupart des objets conteneurs de l’interface utilisateur affiche un type de contenu d’information. Le contenu peut représenter des informations sur l’état actuel de l’environnement, ou il peut représenter des informations sur un état futur potentielle de l’environnement. Par exemple, il peut être utilisé pour montrer l’effet d’une commande particulière, par exemple une refactorisation du code existant de.  
  
    -   **Toujours** utiliser la représentation canonique des informations que vous affichez. Par exemple, le code doit se présenter comme le code, avec la syntaxe et doit respecter des polices et autres paramètres de que l’utilisateur a défini l’environnement.  
  
    -   **Toujours** prendre en compte la prise en charge des actions sur le contenu d’information qui serait possible si ces mêmes informations sont présentées sous forme de contenu principal. Par exemple, si présentant un code existant à l’intérieur d’un conteneur d’interface utilisateur sur l’objet, envisagez la possibilité de parcourir et modifier ce code de prise en charge.  
  
    -   **Toujours** envisagez d’utiliser une couleur d’arrière-plan si présentant le contenu d’information qui représente un état futur potentiel.  
  
2.  Action : certains conteneurs de l’interface utilisateur sur l’objet fournit la possibilité d’effectuer une action sur le contenu principal, telle que l’exécution d’une opération de refactorisation.  
  
    -   **Toujours** positionner les commandes utilisables séparément à partir du contenu d’information.  
  
    -   **Toujours** activer et désactiver les actions lorsque cela est approprié.  
  
    -   **Toujours** reportez-vous aux instructions standards pour représenter des commandes à l’intérieur des boîtes de dialogue.  
  
    -   **Toujours** conserver le nombre d’actions qui sont exposées dans un conteneur d’interface utilisateur sur l’objet au strict minimum. Interaction avec l’interface utilisateur de l’objet doit être une expérience léger et rapide. L’utilisateur ne doit pas avoir d’étendre l’énergie sur la gestion du conteneur de l’interface utilisateur sur l’objet.  
  
    -   **Toujours** Pensez comment et quand un conteneur d’interface utilisateur sur l’objet sera fermé ou ignoré. Comme meilleure pratique, toute action qui se termine à la boîte de dialogue entre le masque et le contenu de détail doit également fermer le conteneur de l’interface utilisateur sur l’objet lorsque cette action est appelée.  
  
3.  **Navigation :** certains objets conteneurs de l’interface utilisateur incluent des liens qui dirige l’utilisateur vers une autre fenêtre ou une application, telles que l’ouverture d’un article MSDN dans le navigateur web de l’utilisateur.  
  
    -   **Toujours** ajouter n’importe quel lien de navigation « Ouvert » afin que les utilisateurs ne seront pas surpris par la cible de la navigation sur un autre contenu.  
  
    -   **Toujours** séparer des liens de navigation à partir des liens pouvant être actionnées.  
  
#### <a name="ambient-indicators-optional"></a>Indicateurs ambiantes (facultatifs)  
 Indicateurs ambiantes peuvent être subtiles, y compris le texte présenté dans une couleur de contraste du reste du code, ou évident, y compris les symboles installer tels que les soulignements tilde et icônes de balise active. Indicateurs ambiantes communiquent la disponibilité des informations complémentaires utiles. Dans l’idéal, ils fournissent des informations utiles même sans que l’utilisateur d’interagir avec eux.  
  
-   **Toujours** positionner un indicateur ambiant afin qu’il ne pas distraire ou éviter tout problème de l’utilisateur. S’il est impossible de placer un indicateur ambiant de manière, envisagez une autre solution.  
  
-   **Toujours** positionner l’indicateur ambiante aussi proche que possible pour le contenu qui lui sont associés.  
  
-   **Toujours** essaie de créer un indicateur qui résume les informations qu’il rend disponibles. Si possible, donnez un décompte du nombre d’éléments de données disponibles (par exemple, « 3 références » au lieu de simplement « références ») ou d’une autre façon pour synthétiser les données de réflexion.  
  
    -   Dans les cas où les données d’un indicateur ne peut pas toujours être calculées et affichées, immédiatement envisagez de fournir des commentaires progressif comme les valeurs sont calculées. Par exemple, considérez l’animation de modification qui reflètent les mises à jour des données disponibles, similaires à celle de que la vignette dynamique de la messagerie sur Windows Phone actualise en tant que le nombre de messages électroniques non lus augmente.  
  
-   **Jamais** ajouter des indicateurs de plus qu’un utilisateur peut raisonnablement pour un élément de contenu donné. Indicateurs ambiantes doivent être utiles sans nécessiter d’intervention de l’utilisateur. Indicateurs de perdre leur ambiance s’ils ont besoin de dépassement de capacité et d’autres contrôles de gestion pour les afficher dans la vue.  
  
#### <a name="gestures"></a>Mouvements  
 Un aspect clé de permettre à l’utilisateur permet de conserver le focus sur le contenu principal est prise en charge les mouvements de droite pour ouvrir et fermer le contenu des détails supplémentaires.  
  
-   **Toujours** oblige l’utilisateur à effectuer des mouvements explicite pour ouvrir le contenu supplémentaire. Mouvements ouvrir courantes sont les suivantes :  
  
    -   **Pointage :** info-bulles ou le contenu d’information non interactif  
  
    -   **Commande explicite :** inline présentateur  
  
    -   **Double-cliquez sur l’indicateur ambiante :** fenêtre contextuelle CodeLens  
  
-   **Toujours** faire disparaître le contenu en détail chaque fois que l’utilisateur appuie sur la touche ÉCHAP.  
  
-   **Toujours** prendre en compte le contexte de l’interface utilisateur sur l’objet. Pour les présentateurs de contenu qui permet l’interaction du conteneur, étudiez attentivement le s’il faut afficher des informations supplémentaires pour le pointage, qui est susceptible d’entraîner des perturbations pour les flux de travail de l’utilisateur.  
  
-   **Jamais** afficher du contenu pointage qui semble être modifiables ou invite l’intervention de l’utilisateur. Ce comportement peut nuire aux utilisateurs fonctionnalité s’ils tentent déplacer le curseur sur le contenu de détail, le comportement standard d’une info-bulle doit immédiatement fermer le curseur n’est plus sur le contrôleur de contenu qui l’a produit.  
  
##  <a name="BKMK_SelectionModels"></a> Modèles de sélection  
  
### <a name="overview"></a>Vue d'ensemble  
 Un modèle de sélection est le mécanisme utilisé pour indiquer et confirmer les opérations sur un ou plusieurs objets d’intérêt dans l’interface utilisateur. Cette rubrique décrit les modèles d’interaction de sélection dans les éditeurs de document de Visual Studio : éditeurs de texte, des surfaces de dessin et des surfaces de modélisation.  
  
 Les utilisateurs doivent disposer d’un moyen d’indiquer à Visual Studio, ils travaillent sur, et Visual Studio doit répondre comme prévu avec des commentaires pour qu’il fonctionne sur les utilisateurs. Différences ou une mauvaise entre l’utilisateur et l’interface utilisateur peut entraîner l’utilisateur non détection d’une action, ce qui peut avoir des conséquences inattendues. Souvent, l’erreur passe inaperçue jusqu'à ce que l’utilisateur voit que quelque chose est manquante ou a été modifié. Modèles de sélection sont par conséquent, un des éléments essentiels de conception de l’interface utilisateur. Bien que les modèles de sélection dans Visual Studio sont cohérentes avec Windows, il existe de légères variantes.  
  
 Dans Visual Studio, comme dans Windows, les modèles de sélection diffèrent selon le contexte dans lequel l’interaction se produit. Sélections peuvent se produire dans les quatre types d’objets :  
  
-   Texte  
  
-   Objets graphiques  
  
-   Listes et les arborescences  
  
-   Grilles  
  
 Au sein de ces objets, il existe trois types de sélections :  
  
-   Contiguës  
  
-   Disjoints  
  
-   Région  
  
#### <a name="scope"></a>Portée  
 Le composant essentiel de la sélection est de vous assurer que l’utilisateur connaît la fenêtre dans laquelle ils travaillent (activation) et où le focus est située (sélection). Visual Studio étend les fonctionnalités de gestion de fenêtre dans Windows, mais le schéma d’activation est identique : interaction avec une fenêtre place le focus dans la fenêtre. Visual Studio a deux indicateurs pour l’activation : un pour les fenêtres de document et un pour les fenêtres Outil.  
  
 Pour les fenêtres de document, la fenêtre active est indiquée par un onglet de fenêtre de document à venir au premier plan et en modifiant sa couleur d’arrière-plan :  
  
 ![Sélection de l’onglet actif dans Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")  
  
 **Sélection de l’onglet actif**  
  
 Pour les fenêtres Outil, la fenêtre active est indiquée par une modification de la couleur de la barre de titre de la fenêtre d’outil :  
  
 ![Sélection de la fenêtre Outil active dans Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")  
  
 **Afficher la sélection principale d’un nœud de la fenêtre outil Active**  
  
 ![Sélection de la fenêtre outil inactive dans Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")  
  
 **Fenêtre outil inactif, montrant latente sélection du nœud**  
  
 Une fois qu’une fenêtre est active, le focus est indiquée selon les modèles de sélection décrites dans cette section des lignes directrices.  
  
#### <a name="context"></a>Contexte  
 Visual Studio a été conçu pour conserver un fort concept de contexte, le suivi du où l’utilisateur travaille. Une seule fenêtre est active, s’il s’agit d’une fenêtre outil ou le document. Toutefois, la fenêtre de document au premier plan conserve toujours une sélection latente. Bien que le focus dans une fenêtre outil, la fenêtre de document qui était actif affiche une sélection, même dans un état inactif. Pour cela, pour conserver le contexte de l’utilisateur dans le document, qu'ils ont été modifiant, en leur indiquant que Visual Studio a conservé leur état afin qu’ils peuvent retourner et passer en toute transparence les fenêtres Outil et fenêtres de document.  
  
### <a name="text-selection"></a>Sélection de texte  
 Les éditeurs de Visual Studio qui sont strictement textuelles, tels que l’éditeur de texte intégré, utilisent le même modèle de sélection de texte et d’apparence décrites dans le [la souris et les pointeurs](https://msdn.microsoft.com/en-us/library/dn742466.aspx) page des directives d’Interaction expérience utilisateur Windows sur MSDN. Le focus d’entrée dans l’éditeur de texte est indiqué par une barre verticale, appelée le point d’insertion. Le point d’insertion est un seul pixel épais et coloré en tant que l’inverse de l’élément qui apparaît derrière lui. Il clignote en fonction de la fréquence définie par le **clignotement du curseur** définition dans le **vitesse** onglet de la **clavier** située dans le panneau de configuration.  
  
#### <a name="contiguous-and-disjoint-selection"></a>Sélection contiguë et disjointe  
 Sélection dans l’éditeur de texte est contigue uniquement. De texte disjointes sélections ne sont pas autorisées, mais doivent être traitées dans les éditeurs de l’objet graphique. Lorsque le pointeur de la souris se trouve sur une zone de texte, le curseur se transforme en i. Un seul clic place le point d’insertion dans l’éditeur de texte à l’emplacement du clic. Le bouton de souris enfoncé démarre la surbrillance de sélection et relâcher le bouton de la souris termine la surbrillance de la sélection.  
  
#### <a name="region-selection-box-selection"></a>Sélection de région (sélection de la)  
 Visual Studio prend en charge les sélections de la région dans l’éditeur de texte, et il s’agit de la sélection. Sélection de zone permet à l’utilisateur à sélectionner une zone de texte qui ne respecte pas le flux de texte standard. Comme avec la sélection de texte standard, la sélection doit être contiguë. La sélection est initiée par la touche Alt enfoncée tout en faisant glisser la souris. La sélection peut également être lancée en appuyant sur les touches Alt et MAJ tout en utilisant les touches de direction pour indiquer la région de sélection. Sélection de zone utilise la mise en surbrillance de la sélection normale et affiche le curseur du point d’insertion clignote à la fin de la zone de sélection.  
  
 ![Régional &#40;zone&#41; sélection dans Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")  
  
 **Sélection de région (zone) dans Visual Studio**  
  
#### <a name="text-selection-appearance"></a>Apparence de la sélection de texte  
 Les couleurs utilisées pour la sélection active ou inactive dans l’éditeur peuvent être personnalisés. Pour personnaliser l’apparence visuelle de l’éditeur, un utilisateur peut atteindre **Outils > Options**, puis regardez sous **environnement > polices et couleurs > Éditeur de texte**.  
  
### <a name="graphical-selection"></a>Sélection de graphique  
  
#### <a name="interaction"></a>Interaction  
 Sélection d’un objet de graphique peut être complexe et dépend de plusieurs facteurs :  
  
-   **Modèle de sélection principale de l’éditeur.** Éditeurs qui contiennent des objets graphiques peuvent également servir à modifier du texte ou des grilles. Par exemple, l’éditeur peut être un éditeur de texte qui prend également en charge le positionnement des objets graphiques, tels que le concepteur Visual Studio XAML. Prise en charge de plusieurs types d’objets peut affecter comment l’utilisateur sélectionne les groupes de différents types d’objets.  
  
-   **Prise en charge des États de la sélection principale et secondaire.** Un éditeur peut fournir des États de sorte que les objets peuvent être modifiés de concert, alignés avec d’autres, redimensionné ensemble, et ainsi de suite de sélection principale et secondaire.  
  
-   **Prise en charge de modification sur place.** Éditeurs peuvent également permettre le contenu de leurs objets de graphiques à modifier. Par exemple, une forme de rectangle peut également contenir le texte à l’intérieur qui peut être modifié par l’utilisateur. En outre, ce texte peut être centré ou justifié. Modification sur place implique un niveau plus détaillé de l’interaction utilisateur et par conséquent requiert un ensemble approprié d’aides visuelles permettant de présenter des informations d’état à l’utilisateur.  
  
#### <a name="mouse-interaction"></a>Interaction souris  
  
|Entrée|Résultat|  
|-----------|------------|  
|Cliquez sur un objet non sélectionné|Sélectionne l’objet et affiche une ligne en pointillés et les handles de sélection, si l’objet est redimensionnable.|  
|Cliquez sur un objet sélectionné|Active la modification sur place si l’objet prend en charge. Cliquez en dehors de l’objet désactive le mode de modification sur place.|  
|Double-cliquez sur un objet|Ouvre le code-behind de l’objet à modifier et peut insérer un gestionnaire d’événements par défaut, le cas échéant.|  
|Pointez sur un objet|Remplace le pointeur jusqu’au curseur de déplacement. Apparence de l’objet, telles que sa couleur, ou la luminosité peut changer.|  
|Pointez sur une poignée de sélection|Remplace le pointeur jusqu’au curseur de redimensionnement. Pour les objets qui prennent en charge de la rotation, des poignées de sélection peuvent changer le pointeur d’un curseur de rotation que le pointeur est positionné différemment (par exemple, déplacé loin) en ce qui concerne la poignée de sélection.|  
|Faites glisser|Même si l’objet n’est pas déjà sélectionné, remplace le pointeur par le curseur de déplacement et déplace l’objet.|  
|Éditeur perd le focus|Désactive le mode de modification sur place, bien que l’objet conserve le contenu et l’apparence qu’il avait lors de son dernier état de sélection d’opération.|  
|Sélection d’objets|Indiqué par une bordure, ligne en pointillés ou tout autre traitement visuellement distincte pour mettre en surbrillance de la limite de l’objet.|  
|Redimensionner un objet sélectionné|Indiqué par les poignées de sélection.<br /><br /> Un objet redimensionnable possède huit poignées, représentant chaque direction dans laquelle il peut être redimensionné. Nombre de handles peuvent être utilisés si l’objet peut uniquement être redimensionné dans certaines directions. Lorsque l’utilisateur redimensionne un objet jusqu’où huit poignées ne serait pas interactives, quatre poignées peuvent ensuite être utilisées. Handle de tailles doivent être liées à la métrique de bordure et le bord de fenêtre avec le **GetSystemMetrics** fonction d’API à la taille en fonction de la résolution d’affichage.<br /><br /> ![Poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|  
|Faire pivoter un objet sélectionné|![Poignées de rotation](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|  
  
#### <a name="keyboard-interaction"></a>Interaction du clavier  
  
|Entrée|Résultat|  
|-----------|------------|  
|Onglet|Déplace l’indicateur de focus entre l’ordre logique des objets dans l’éditeur. Cela peut être de gauche à droite ou de haut en bas en fonction de **TabIndex** (ou équivalent) valeur de propriété, ordre de création de l’objet et l’objectif global de l’éditeur. Maj + Tab inverse le sens de l’indicateur de focus.|  
|Barre d’espace|Active le mode panoramique lors de la séquence de touches est conservée. Entrée de la souris supplémentaire est nécessaire pour effectuer un panoramique sur la position de la fenêtre d’affichage.|  
|Ctrl+Barre d'espace|Active le mode de zoom lors de la séquence de touches est conservée. Entrée de la souris supplémentaire est requis pour augmenter et diminuer le facteur de zoom.|  
|Ctrl + Alt + signe moins|Réduit le facteur de zoom d’un niveau.|  
|Ctrl + Alt + signe Plus|Augmente le facteur de zoom d’un niveau.|  
|Touche MAJ ou Ctrl|Ajoute l’objet au groupe de sélection. CTRL vous permet également à supprimer les objets individuellement à partir du groupe de sélection.|  
|Entrée|Exécute la commande par défaut pour l’objet (généralement ouvrir ou modifier).|  
|F2|Active la modification sur place pour l’objet.|  
|Touches de direction|Déplace les objets sélectionnés dans la direction de la touche enfoncée par petits incréments (par exemple, 1 pixel à la fois)|  
|CTRL + touches de direction|Déplace les objets sélectionnés dans la direction de la touche enfoncée, dans les incréments de grande taille (par exemple, 10 pixels à la fois)|  
|Maj + flèche clés|Redimensionne les objets sélectionnés sur l’axe respectif, en petits incréments (par exemple, 1 pixel à la fois)|  
|CTRL + MAJ + touches de direction|Redimensionne les objets sélectionnés sur l’axe respectif, en incréments de grande taille (par exemple, 10 pixels à la fois)|  
  
 Lorsque les utilisateurs modifient des contrôles en place, il peut être utile pour les objets à redimensionner automatiquement avec l’entrée d’utilisateur. Par exemple, si l’utilisateur modifie un contrôle d’étiquette, l’étiquette doit augmenter pour afficher le texte entrés par l’utilisateur uniquement. Si cela n’est pas fait, l’utilisateur doit redimensionner le contrôle manuellement après la modification du texte. Si l’utilisateur a un grand nombre de contrôles, cela devient une tâches répétitives et les tâches non productives.  
  
#### <a name="graphical-containers"></a>Conteneurs graphiques  
 Dans certains cas, éditeurs graphiques fournissent des conteneurs pour d’autres objets graphiques, tels que le contrôle Panel Windows Forms ou le contrôle de disposition de grille dans le Concepteur HTML. Si votre éditeur fournit des conteneurs pour d’autres objets de graphiques, le modèle de sélection suivante doit être utilisé pour le conteneur uniquement (objets au sein de la suite de conteneur que le modèle standard comme décrit ci-dessus) :  
  
|Entrée|Résultat|  
|-----------|------------|  
|Cliquez sur le conteneur|Sélectionne l’objet conteneur sans directement en sélectionnant un des objets qu’il contient. Le conteneur peut être déplacé et/ou redimensionné avec la souris et clavier (comme décrit ci-dessus). Objets qu’il contient sont déplacés par rapport au conteneur, mais les objets qu’il contient ne sont pas redimensionnées, sauf si elles sont sélectionnées directement.|  
|Placez le curseur sur une région de limites du conteneur|Active la souris dans le curseur de déplacement, indiquant que le conteneur peut être déplacé.|  
|Faites glisser la région des limites du conteneur|Modifie la souris pour le curseur de déplacement et déplace le conteneur (et les objets contenus dans). Impossible de déplacer sans d’abord le conteneur de sélection d’un seul clic.|  
|Cliquer sur un objet dans le conteneur|Désactive le conteneur (si) et sélectionne uniquement l’objet sélectionné.|  
|MAJ + cliquez sur ou Ctrl + cliquez sur un objet contenu et/ou d’un conteneur|Ajoute l’objet sélectionné à une sélection ou d’un groupe de sélection. Si l’objet sélectionné est déjà membre du groupe de sélection, il est supprimé du groupe de sélection.|  
  
 Les objets contenus doivent respecter le modèle de sélection de base comme décrit dans la section précédente. Test de la facilité d’utilisation du Concepteur Windows Forms, les utilisateurs prévu, un accès transparent aux objets qu’il contient sans étapes intermédiaires (imposées par l’objet de relation contenant-contenu).  
  
#### <a name="disjoint-and-region-selections"></a>Disjointes et les sélections de région  
 Éditeurs de l’objet graphique doivent prendre en charge les sélections disjointes. Notez que ce graphique n’affiche pas l’apparence du contrôle pour Visual Studio. Consultez [apparence de sélection d’objet graphique](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) des spécifications visual détaillées.  
  
 ![Disjointes sélecteurs de régions et](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")  
  
 **Sélection disjointe**  
  
 Éditeurs graphiques doivent également fournir les sélections de région avec un indicateur de sélection de type texte défilant. Si l’éditeur graphique prend en charge d’autres types d’objet (par exemple, texte), les sélections de région ne peuvent pas être possibles selon les contraintes de ces autres types d’objet.  
  
 ![Sélection](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")  
  
 **Rectangle de sélection**  
  
#### <a name="primary-and-secondary-selections"></a>Sélections principale et secondaire  
 Certains éditeurs de l’objet graphique autoriser l’utilisateur à modifier ou à aligner des objets dans des groupes. Dans ce cas, le concept de sélections principale et secondaire doit être introduite. La sélection principale est l’objet auquel tous les autres objets répondent pour les opérations de groupe. L’objet que l’utilisateur sélectionne le premier devient le principal contrôle, et les sélections suivantes deviennent les sélections secondaire. La sélection principale a un traitement visual distinct à partir de l’ou des sélections secondaire pour indiquer quel objet principal :  
  
 ![Sélection principale et secondaire](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")  
  
 **Sélection principale avec deux sélections secondaire**  
  
####  <a name="BKMK_GraphicalObjectSelectionAppearance"></a> Apparence de la sélection d’objet graphique  
 Les poignées sont des carrés dans un rectangle autour de la zone englobante de l’objet. Le graphique ci-dessous montre des exemples des différents États qu’un objet graphique peut avoir avec poignée de dimensionnement et apparence de modification sur place. La taille des handles doit être liée à la bordure de fenêtre et les métriques de bord à l’aide du **GetSystemMetrics** API.  
  
|État|Apparence|Détails de Visual|  
|-----------|----------------|--------------------|  
|**Non sélectionné**|Par défaut|![État du bouton par défaut](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState")||  
|**Sélection principale**|Redimensionnable|![Sélection principale avec des poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize")|![Sélection principale avec des poignées de redimensionnement &#40;zoom&#41;](../../extensibility/ux-guidelines/media/0713-12_primaryresizezoom.png "0713-12_PrimaryResizeZoom")|  
|**Sélection principale**|Ne peut pas être redimensionnée|![Sélection principale sans poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize")|![Sélection principale sans poignées de redimensionnement &#40;zoom&#41;](../../extensibility/ux-guidelines/media/0713-14_primarynoresizezoom.png "0713-14_PrimaryNoResizeZoom")|  
|**Sélection principale**|Verrouillé|![Sélection principale verrouillée](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked")|![Sélection principale verrouillée &#40;zoom&#41;](../../extensibility/ux-guidelines/media/0713-16_primarylockedzoom.png "0713-16_PrimaryLockedZoom")|  
|**Sélection secondaire**|Redimensionnable|![Sélection secondaire avec des poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize")|![Sélection secondaire avec des poignées de redimensionnement &#40;zoom&#41;](../../extensibility/ux-guidelines/media/0713-18_secondaryresizezoom.png "0713-18_SecondaryResizeZoom")|  
|**Sélection secondaire**|Ne peut pas être redimensionnée|![Sélection secondaire sans poignées de redimensionnement](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize")|![Sélection secondaire sans poignées de redimensionnement &#40;zoom&#41;](../../extensibility/ux-guidelines/media/0713-20_secondarynoresizezoom.png "0713-20_SecondaryNoResizeZoom")|  
|**Sélection secondaire**|Verrouillé|![Sélection secondaire verrouillée](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked")|![Sélection secondaire verrouillée &#40;zoom&#41;](../../extensibility/ux-guidelines/media/0713-22_secondarylockedzoom.png "0713-22_SecondaryLockedZoom")|  
|**Interface utilisateur active**|Par défaut|![État actif de l’interface utilisateur](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive")|![État actif de l’interface utilisateur &#40;zoom&#41;](../../extensibility/ux-guidelines/media/0713-24_uiactivezoom.png "0713-24_UIActiveZoom")|  
  
### <a name="view-selection-models"></a>Afficher les modèles de sélection  
  
#### <a name="tree-view"></a>Arborescence  
 Sélection dans une arborescence est affichée en surbrillance simple. Si l’utilisateur clique sur un nom de nœud ou une icône de nœud, le nœud est sélectionné. Les glyphes triangulaires à gauche du nœud développer ou de contrat de l’arborescence, mais n’affectent pas la sélection de l’utilisateur, à une exception près : lors de la réduction d’un nœud parent lorsque la sélection se trouve sur un enfant de ce nœud, la sélection se déplace vers le parent.  
  
 ![Arborescence classique dans Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")  
  
 **Arborescence classique dans Visual Studio**  
  
 Vues de l’arborescence peuvent prendre en charge les sélections contigues et disjointes, même à travers plusieurs niveaux dans l’arborescence. Contigu ou dissocié sélections multiples doivent être effectuées sur les nœuds d’arbre visible. Si un nœud est réduit, la sélection distincte est perdue et le nœud qui a été réduit Obtient la sélection. De cette façon, l’utilisateur peut voir les nœuds qui seront affectés par une opération. Lorsque les nœuds sont réduits, il devient difficile de savoir quels nœuds peuvent être affectées.  
  
 Lorsqu’un nœud parent est sélectionné, l’opération doit s’appliquer au parent, s’il peut y avoir des cas où il est préférable pour une opération à appliquer au parent et tous ses enfants. Dans ce cas, fournissent une interface utilisateur supplémentaire pendant l’opération, tel qu’une case à cocher ou de la boîte de dialogue de confirmation pour rendre l’option « appliquer à tous les enfants » explicite à l’utilisateur.  
  
##### <a name="renaming"></a>Renommage  
 Si les nœuds dans l’arborescence de prendre en charge le changement de nom, le changement de nom doit être effectuée en place. L’opération de déplacement doit être standard pour tous les contrôles d’arborescence dans Visual Studio. Fournir une commande rename immédiatement Active le mode de modification sur place, avec la sélection de texte couvrant le nom entier du nœud, prêt à accepter l’entrée d’utilisateur. Si le nœud représente un fichier, le nom de fichier doit contenir l’extension. La surbrillance de la sélection doit inclure uniquement le corps du nom de fichier et pas l’extension.  
  
|Entrée|Résultat|  
|-----------|------------|  
|Entrée (touche)|Valide l’opération de changement de nom|  
|Touche ÉCHAP|Annule l’opération de changement de nom|  
|Cliquez en dehors de la zone d’édition|Valide l’opération de changement de nom|  
|Annuler|Fournir facilement Annuler pour annuler l’opération de changement de nom|  
  
#### <a name="selection-within-lists-and-grid-controls"></a>Sélection dans les listes et les contrôles de grille  
 Le concept clé dans la sélection de liste est qu’il est basé sur la ligne, ce qui signifie que lorsqu’une sélection est effectuée à la ligne entière est sélectionné en tant qu’unité. En revanche, grilles peuvent autoriser des cellules spécifiques à sélectionner sans affecter tous les autres aspects de la ligne. Grilles de peuvent également contenir une hiérarchie de lignes imbriquées (par exemple, dans un contrôle TreeGrid) qui autorisent les branches entières de la hiérarchie sélectionnée et désélectionnée en interagissant avec les lignes parentes. Sélection dans les listes est indiquée par une couleur de surbrillance simple sur toute la ligne de données. Le focus est affiché par une bordure en pointillés pixels autour de la ligne modifiable ou d’une cellule (ligne si toutes les cellules sont en lecture seule).  
  
> [!NOTE]
>  **Le focus** et **sélection** sont des concepts différents. *Le focus* indique de quelle interface utilisateur de l’élément cible pour recevoir une entrée qui ne sont pas explicitement dirigée vers un autre objet, tandis que *sélection* fait référence à l’état de l’inscription d’un objet dans un ensemble d’objets sur lesquels suivantes opérations peuvent avoir lieu.  
  
 Les sélections dans les listes peuvent être contiguës, disjoint, ou une région. Lorsque plusieurs sélections sont autorisées, contiguës et sélection disjointe doit toujours être pris en charge, lors de la prise en charge des sélections de région (zone) sont facultatif. Les sélections de région sont lancées en faisant glisser dans l’espace blanc du corps de la liste.  
  
|Object|Sélection|  
|------------|---------------|  
|Liste|Contiguës|Toujours pris en charge (plusieurs sélections sont autorisées).|  
|Liste|Disjoints|Toujours pris en charge (plusieurs sélections sont autorisées).|  
|Liste|Région|Prise en charge facultative. Lancé en faisant glisser la souris dans l’espace blanc du corps de la liste.|  
  
 Cliquez une fois sur une liste pour sélectionner la ligne où le clic s’est produit. Si l’utilisateur de cliquer dans une cellule de liste qui prend en charge la modification sur place, la cellule est immédiatement activée pour la modification sur place. Sinon, la ligne entière est immédiatement sélectionnée et affiche une mise en surbrillance.  
  
 Faire glisser dans le corps de la liste effectue une des trois opérations :  
  
-   Lance une sélection de région, si la liste prend en charge et le bas de la souris est dans un espace blanc  
  
-   Initie une opération de glisser-déplacer si la cellule de la liste ou de la ligne prend en charge en cours d’une source de glissement  
  
-   Sélectionne la ligne actuelle  
  
##### <a name="in-place-editing"></a>Modification sur place  
 Lors de la modification sur place est autorisée, il existe deux modèles de base : sélecteur de contrôle et la propriété Edition simple. Avec un contrôle d’édition simple, le contenu est mis en surbrillance et prêt pour l’utilisateur d’entrée dès que la modification sur place est activé. Lorsqu’un sélecteur de propriété est implémenté, le bouton qui appelle le sélecteur de propriétés s’affiche une fois que le mode de modification sur place est activé, et la sélection actuelle n’est pas mis en surbrillance. Le bouton de sélecteur doit être aligné à droite dans la cellule. Pour des exemples de modification sur place, consultez la **fenêtre Propriétés** et **liste des tâches** dans Visual Studio.  
  
##### <a name="keyboard-support"></a>Prise en charge du clavier  
 Prise en charge du clavier pour la sélection dans les listes et des grilles suit les conventions Windows :  
  
-   Touches de direction accéder à la liste, en sélectionnant chaque cellule/ligne que le focus est déplacé.  
  
-   Maj + flèche effectue une sélection contiguë dans la direction des touches de direction.  
  
-   Ctrl + flèche suivie fait basculer la barre d’espace entre l’ajout et suppression d’éléments de la sélection, la création d’une sélection disjointe.  
  
-   Pour les grilles qui contiennent des hiérarchies imbriquées, la touche flèche droite développe une ligne parente, et la touche flèche gauche réduit un.  
  
-   La touche Tab déplace le focus entre les cellules de la ligne actuelle si les cellules sont modifiables.  
  
-   La touche entrée exécute la commande par défaut sur l’élément dans la liste (souvent **ouvrir**).  
  
-   La touche F2 Active la modification sur place pour la cellule actuellement sélectionnée.  
  
##  <a name="BKMK_PersistenceAndSavingSettings"></a> Persistance et l’enregistrement des paramètres  
  
### <a name="overview"></a>Vue d'ensemble  
 Bien que chaque composant de logiciel dans Visual Studio est généralement responsable de son propre état et de persistance, Visual Studio enregistre automatiquement les paramètres dans certains cas, comme avec les positions et les tailles de fenêtre. Le tableau ci-dessous est une combinaison de paramètres enregistrés automatiquement et qui nécessitent un utilisateur explicite ou programmé l’action à entreprendre.  
  
|Object|Les éléments à enregistrer|Quand l’enregistrer|Emplacement d’enregistrement|  
|------------|------------------|------------------|-------------------|  
|Objet sélectionnable (par exemple, une ligne de code)|Un point d’arrêt sur une ligne de code<br /><br /> Un raccourci de l’utilisateur associé à la ligne de code|Lorsque le projet est enregistré.|Le **options (.suo) de l’utilisateur** fichier pour le projet|  
|Boîte de dialogue|L’emplacement de la boîte de dialogue, s’il avait été déplacé<br /><br /> La vue de l’utilisateur a utilisé dans la boîte de dialogue|Lorsque la boîte de dialogue se ferme<br /><br /> Lorsque la session de Visual Studio se termine|Dans la mémoire<br /><br /> Registre dans **HKEY_Current_User**|  
|Fenêtre|La taille et l’emplacement de la fenêtre|Lorsque la fenêtre se ferme<br /><br /> Lorsque le mode de Visual Studio est modifié<br /><br /> Lorsque la session de Visual Studio se termine|Le **options (.suo) de l’utilisateur** fichier pour le projet<br /><br /> Fichier d’options personnalisées pour les paramètres de la fenêtre|  
|Document|La sélection actuelle dans le document<br /><br /> La vue du document<br /><br /> L’avant-dernière position plusieurs visité par l’utilisateur|Lorsque le document est enregistré.|Le **options (.suo) de l’utilisateur** fichier pour le projet|  
|Projet|Références aux fichiers<br /><br /> Références à des répertoires sur le disque<br /><br /> Références à d’autres logiciels<br /><br /> Composants<br /><br /> Informations d’état sur le projet lui-même|Lorsque le projet est enregistré.|Le fichier projet|  
|Solution|Références aux projets<br /><br /> Références aux fichiers|Lorsque le projet ou la solution est enregistrée|Le **solution (.sln)** fichier|  
|Paramètres de **Outils > Options**|Personnalisations de clavier<br /><br /> Personnalisations de la barre d’outils<br /><br /> Jeux de couleurs|Lorsque le **Outils > Options** boîte de dialogue se ferme.<br /><br /> Lorsque la session de Visual Studio se termine|Registre dans **HKEY_Current_User**|  
  
 Ce que l’utilisateur effectue et quand ils font, détermine si un paramètre est enregistré dans la mémoire (pendant la session), enregistré sur le disque (entre les sessions en tant qu’un paramètre de Registre), en tant que partie du fichier projet ou solution lui-même, dans le cadre de la **solution Options (.suo)** de fichiers, ou que des paramètres personnalisés de fichiers seulement ce composant logiciel connaît. Le tableau ci-dessus montre plusieurs événements à laquelle les paramètres peuvent être enregistrés. Toutefois, il existe d’autres moments dans lequel vous pouvez souhaiter enregistrer l’état :  
  
-   Lorsque l’utilisateur modifie l’emplacement au sein d’une fenêtre ou une boîte de dialogue  
  
-   Lorsque l’utilisateur transfère le focus vers une autre fenêtre  
  
-   Lorsque l’utilisateur bascule de la conception en mode débogage  
  
-   Lorsque l’utilisateur se déconnecte leur compte  
  
-   Lorsque l’ordinateur en veille prolongée ou s’arrête  
  
-   Lorsque le disque dur/ordinateur est sur le point d’être reformaté et configurez une nouvelle  
  
### <a name="window-configurations"></a>Configurations de fenêtres  
 Une configuration de la fenêtre est la présentation de l’environnement de développement de base - il s’agit d’un jeu comprenant la liste des fenêtres Outil présents et celui dans lequel ils sont organisés. Pour windows gérés par l’IDE (IDE windows), les informations de disposition sont conservées par l’utilisateur, ainsi, lorsqu’un lancement de l’utilisateur l’IDE, la disposition de fenêtre s’affiche, le même que lors de la dernière quitté de Visual Studio. L’état et la position des fenêtres de l’IDE est rendue persistante dans un fichier d’options personnalisées au format XML. Les fenêtres Outil sont créés par les packages chargés dans l’IDE conserver leurs informations d’état dans le Registre et peuvent ou ne peuvent pas être par utilisateur.  
  
#### <a name="profile-specific-layouts"></a>Dispositions spécifiques au profil  
 Chaque profil comprend des dispositions des fenêtres Outil, organisées de manière familière aux personnes approuvées du développeur spécifique (les développeurs Visual C++ s’attendre à voir les **l’Explorateur de solutions** sur le côté gauche de l’IDE, tandis que les développeurs c# s’attendre à voir les  **L’Explorateur de solutions** à droite). Dispositions de fenêtres spécifiques au profil sont chargées après que l’utilisateur choisit un profil au démarrage. Un auteur du package doit déterminer la disposition de fenêtre plus appropriée pour une expérience de leurs clients, en sachant que les modifications apportées par l’utilisateur à la configuration de la fenêtre sont ensuite rendues persistantes.  
  
##  <a name="BKMK_TouchInput"></a> Entrée tactile  
 Les utilisateurs ont recours à des produits de développement Microsoft sur les appareils tactiles. Toutefois, il existe des barrières qui rendent difficile à utiliser les outils de développement sur les appareils tactiles. Les utilisateurs seront attend à recevoir nos produits pour offrir une expérience tactile fiable et précise. Le but de ces instructions est à indiquer des décisions sur les fonctions tactiles à intégrer et à encourager une expérience tactile cohérent entre Visual Studio et les produits connexes.  
  
### <a name="levels-of-experience"></a>Niveau d’expérience  
 Les niveaux suivants de l’expérience sont destinées à servir de guide pour aider les équipes à déterminer les fonctionnalités tactiles en fonction du niveau d’intérêt d’investissement en contact souhaité.  
  
-   Le **expérience de base** est pour les équipes qui souhaitent fournir touchent capacités, donc il n’y a pas d’ends mortes tout au long de leur travail.  
  
-   Le **optimisé expérience** est pour les équipes qui souhaitent fournir le meilleur parti des fonctionnalités tactiles courantes (par exemple, celles qui sont généralement disponibles dans les applications de navigateur internet).  
  
-   Le **élevé expérience** est pour les équipes qui souhaitent ajouter des fonctionnalités telles que mouvements ou autres fonctionnalités facultatives qui peuvent rendre leurs applications tactiles d’abord convivial.  
  
||Expérience de base|Expérience optimisée|Expérience avec élévation de privilèges|  
|-|----------------------|--------------------------|-------------------------|  
|Permet aux utilisateurs de...|Corrigez le code et solution/projet au niveau de la lecture sans les extrémités de lettres mortes|Effectuer des tâches de maintenance, refactorisations et navigation|Fonctionner dans une expérience cohérente, intuitive et fluide en toute confiance|  
|Éditeur|Sélectionnez le panoramique et sélection<br /><br /> Tactile de barre de défilement pour atteindre et appuyez sur + faire glisser|Zoom avant<br /><br /> Défilement rapide<br /><br /> Sélection<br /><br /> Simple d’utilisation du menu contextuel||  
|Fenêtres Outil supérieur|Panoramique de liste<br /><br /> Sélection d’éléments<br /><br /> Tactile de barre de défilement pour atteindre et appuyez sur + faire glisser|Défilement de l’élément facile et la sélection||  
|Fenêtrage||Redimensionner la fenêtre<br /><br /> Accès rapide||  
|Document bien||Facilite la navigation entre les fichiers ouverts||  
|Mouvements||Assurer les mouvements courantes dans l’IDE|Actions basées sur les mouvements<br /><br /> Prend en charge des concepteurs et glisser-déplacer|  
|Autres considérations|||Clavier visuel personnalisé|  
  
#### <a name="gestures"></a>Mouvements  
 Mouvements de fournissent aux utilisateurs un raccourci pour les commandes qui pourraient sinon requérir une interaction plus complexe. Reportez-vous aux instructions de Windows sur [des entrées tactiles courantes pour les Applications de bureau](http://msdn.microsoft.com/en-us/library/windows/desktop/dd940543\(v=vs.85\).aspx), suivez ces conseils pour la plupart des mouvements, y compris des gestes simples telles que le panoramique et zoom.