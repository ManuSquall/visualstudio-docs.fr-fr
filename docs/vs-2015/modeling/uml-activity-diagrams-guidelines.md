---
title: 'Diagrammes d’activités UML : Instructions | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
ms.assetid: fe5dbe96-79ab-483a-b9bc-44d0d1d3efc2
caps.latest.revision: 50
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 81fcc0c4d747a59f287bc12e7413c5ccab204f7c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874447"
---
# <a name="uml-activity-diagrams-guidelines"></a>Diagrammes d'activités UML : instructions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, vous pouvez dessiner un diagramme d'activités pour décrire un processus d'entreprise ou un algorithme de logiciel sous la forme d'un flux de travail via une série d'actions. Les personnes, composants logiciels ou périphériques peuvent exécuter ces actions. Pour une démonstration vidéo, consultez : [capturer des flux de travail à l’aide de diagrammes d’activités](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-4-Capture-Business-Workflows/).  
  
 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Prise en charge des versions pour les outils d'architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Pour créer un diagramme d’activités UML, sur le **Architecture** menu, cliquez sur **nouveau UML ou diagramme de couche**.  
  
 Vous pouvez utiliser un diagramme d'activités à de nombreuses fins :  
  
- décrire un processus d'entreprise ou un flux de travail entre les utilisateurs et votre système Pour plus d’informations, consultez [modéliser les besoins de l’utilisateur](../modeling/model-user-requirements.md).  
  
- décrire les étapes exécutées dans un cas d'usage Pour plus d’informations, consultez [diagrammes de cas d’usage UML : indications](../modeling/uml-use-case-diagrams-guidelines.md).  
  
- décrire une méthode, une fonction ou une opération dans le logiciel Pour plus d’informations, consultez [modèle d’architecture de votre application](../modeling/model-your-app-s-architecture.md).  
  
  La représentation sous forme de dessin d'un diagramme d'activités peut vous aider à améliorer un processus. Si le diagramme d'un processus existant s'avère particulièrement complexe, vous pouvez envisager de le simplifier.  
  
  Pour plus d’informations de référence sur les éléments sur les diagrammes d’activités, consultez [diagrammes d’activités UML : référence](../modeling/uml-activity-diagrams-reference.md).  
  
##  <a name="Relationships"></a> Relation aux autres diagrammes  
 Si vous dessinez un diagramme d'activités pour décrire un processus d'entreprise ou la manière dont les utilisateurs se servent de votre système, vous pouvez dessiner un diagramme de cas d'usage pour afficher une vue différente des mêmes informations. Dans le diagramme de cas d'usage, vous dessinez des actions sous la forme de cas d'usage. Attribuez aux cas d'usage les mêmes noms que ceux des actions correspondantes. Grâce à la vue des cas d'usage, vous pouvez :  
  
- afficher dans un même diagramme la façon dont les actions/cas d'usage importants sont composés d'actions/cas d'usage de plus petite taille, à l'aide de la relation Include ;  
  
- connecter explicitement chaque action/cas d'usage aux utilisateurs ou aux systèmes externes impliqués dans leur exécution ;  
  
- dessiner des limites autour des actions/cas d'usage pris en charge par votre système, ou chacun de ses composants principaux.  
  
  Vous pouvez également dessiner un diagramme d'activités pour décrire la conception détaillée d'une opération logicielle.  
  
  Dans un diagramme d'activités, vous pouvez afficher le flux des données passées entre des actions. Consultez la section sur [décrivant le flux de données](#DataFlows). Mais un diagramme d'activités ne décrit pas la structure des données. Pour cela, vous pouvez dessiner un diagramme de classes UML. Pour plus d’informations, consultez [diagrammes de classes UML : indications](../modeling/uml-class-diagrams-guidelines.md).  
  
##  <a name="BasicSteps"></a> Étapes de base pour dessiner des diagrammes d’activités  
 Les étapes détaillées pour créer un des diagrammes de modélisation sont décrites dans [modèles et diagrammes UML modifier](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-draw-an-activity-diagram"></a>Pour dessiner un diagramme d'activités  
  
1.  Sur le **Architecture** menu, cliquez sur **nouveau UML ou diagramme de couche**.  
  
2.  Sous **modèles**, cliquez sur **diagramme d’activités UML**.  
  
3.  Nommez le diagramme.  
  
4.  Dans **ajouter au projet de modélisation**, sélectionnez un projet de modélisation existant dans votre solution, ou **créer un nouveau projet de modélisation**.  
  
#### <a name="to-draw-elements-on-an-activity-diagram"></a>Pour dessiner des éléments sur un diagramme d'activités  
  
1.  Faites glisser les éléments de la boîte à outils sur le diagramme.  
  
     Commencez par placer les activités principales sur le diagramme, connectez-les, puis apportez les dernières finitions telles que les nœuds initiaux et finaux.  
  
    > [!NOTE]
    >  Vous ne pouvez pas faire glisser d'éléments existants sur le diagramme à partir de l'Explorateur de modèles UML.  
  
2.  Pour connecter les éléments, procédez comme suit :  
  
    1.  Dans le **diagramme d’activités** boîte à outils, cliquez sur **connecteur**.  
  
    2.  Sur le diagramme, cliquez sur l'élément source.  
  
    3.  Cliquez sur l'élément cible.  
  
        > [!NOTE]
        >  Pour utiliser un outil plusieurs fois, double-cliquez sur celui-ci dans la boîte à outils.  
  
#### <a name="to-move-an-activity-to-another-package"></a>Pour déplacer une activité vers un autre package  
  
-   Dans **Explorateur de modèles UML**, faites glisser l’activité dans un package.  
  
     \- ou -  
  
-   Dans **Explorateur de modèles UML**, cliquez sur l’activité et cliquez sur **couper**. Cliquez sur le package, puis cliquez sur **coller**.  
  
    > [!NOTE]
    >  L'activité apparaît uniquement dans l'Explorateur de modèles UML quand vous ajoutez le premier élément au diagramme.  
  
##  <a name="SimpleControlFlow"></a> Description du flux de contrôle  
 Un diagramme d'activités décrit un processus d'entreprise ou un algorithme de logiciel sous la forme d'une série d'actions. Les flèches du connecteur montrent la façon dont le contrôle passe de manière séquentielle d'une action à la suivante. En règle générale, une action peut uniquement démarrer au terme de l'exécution de l'action précédente.  
  
 L'illustration suivante est un exemple d'affichage d'une séquence d'actions montrant des actions, des connecteurs, des branches et des boucles. Chaque élément est expliqué en détail dans les sections suivantes.  
  
 ![Un diagramme d’activités simple](../modeling/media/uml-actguidectrl.png "UML_ActGuideCtrl")  
  
 Diagrammes d’activités utilisent **Actions** et **connecteurs** pour décrire votre système ou une application comme une série d’actions avec le flux de manière séquentielle d’une action à l’autre de contrôle.  
  
- Créer un **Action** (1) pour chaque tâche principale exécutée par un utilisateur, le système ou à la fois en collaboration.  
  
  > [!NOTE]
  >  Essayez de décrire votre processus ou algorithme avec seulement quelques actions. Vous pouvez utiliser **action appeler un comportement** pour définir chaque action plus en détail dans un diagramme séparé, comme décrit dans [description des sous-activités avec des Actions appeler un comportement](#Subactivities).  
  
- Assurez-vous que le titre de chaque action indique clairement ce qu'elle accomplit normalement.  
  
- Liez les actions dans une séquence avec **connecteurs** (2).  
  
- Chaque action se termine avant le début de l'action suivante dans le flux de contrôle. Si vous souhaitez décrire des actions qui se chevauchent, utilisez un **nœud de bifurcation** comme décrit dans la section [flux simultanés](#Concurrent).  
  
  Bien que le diagramme décrive la séquence d'actions, il ne décrit pas comment les actions sont exécutées, ni comment le contrôle est passé d'une action à la suivante. Si vous utilisez le diagramme pour représenter un processus d'entreprise, le contrôle peut être passé, par exemple, quand une personne envoie un e-mail à une autre. Si vous utilisez le diagramme pour représenter une conception de logiciels, le contrôle peut être passé par le biais du flux normal d'exécution d'une instruction à la suivante.  
  
### <a name="describing-decisions-and-loops"></a>Description des décisions et des boucles  
  
-   Utilisez un **nœud de décision** (3) pour indiquer un point où le résultat d’une décision dicte l’étape suivante. Vous pouvez dessiner autant de chemins d'accès sortants que vous le souhaitez.  
  
-   Si vous utilisez le diagramme d'activités pour définir une partie d'une application, vous devez définir les gardes (4) pour indiquer clairement quand chaque chemin doit être pris. Cliquez sur le connecteur, cliquez sur **propriétés**, puis, dans le **propriétés** fenêtre, tapez une valeur pour le **Guard** champ.  
  
-   Il n'est pas toujours nécessaire de définir les gardes. Par exemple, si vous utilisez le diagramme d'activités pour décrire un processus d'entreprise ou un protocole d'interaction, une branche définit la plage d'options ouverte à l'utilisateur ou aux composants interactifs.  
  
-   Utilisez un **nœud de fusion** (5) pour réunir deux ou plusieurs autres flux possédant des branches à un **nœud de décision**.  
  
    > [!NOTE]
    >  Vous devez utiliser un **nœud de fusion** pour rassembler les autres flux, au lieu de réunir les flux à une action. Dans l’exemple, il serait correcte pour se connecter à partir du nœud de décision directement dans le **choisir un élément de Menu**. Cela est dû au fait qu'une action ne démarre pas tant que les threads de contrôle ne sont pas arrivés au niveau de tous leurs connecteurs entrants. Par conséquent, vous devez réunir uniquement des flux simultanés au niveau d'une action. Pour plus d’informations, consultez [flux simultanés](#Concurrent).  
  
-   Utilisez des branches pour décrire des boucles, comme indiqué dans l'exemple.  
  
    > [!NOTE]
    >  Essayez d'imbriquer les boucles de manière structurée, comme vous le feriez dans le code du programme. Si vous décrivez un processus d'entreprise existant, vous découvrirez peut-être des moyens de l'améliorer.  
  
### <a name="starting-the-activity"></a>Démarrage de l'activité  
 Vous pouvez indiquer les points d'entrée dans une activité de deux façons :  
  
-   **Nœud initial**  
  
     Créer un **nœud Initial** (6) pour indiquer la première action de l’activité.  
  
     Cette méthode est particulièrement utile quand vous décrivez une sous-activité ou quand il n'est pas nécessaire d'indiquer de manière explicite ce qui initie l'activité. Par exemple, l'activité Commander un repas commence clairement quand un client a faim.  
  
-   **Nœud accepter un événement**  
  
     Créer **nœuds accepter un événement**, comme décrit dans la section [flux simultanés](#Concurrent), pour indiquer le début d’un thread qui répond à un événement particulier, comme une entrée d’utilisateur. Ne fournissez pas de flux entrant au nœud. L'omission d'un flux entrant indique qu'un thread est démarré chaque fois que l'événement se produit.  
  
     Cette méthode est particulièrement utile quand vous décrivez une réponse à un événement externe spécifique.  
  
### <a name="ending-the-activity"></a>Fin de l'activité  
 Utilisez un **nœud Final de l’activité** (7) pour indiquer la fin d’une activité.  
  
-   Lorsqu’un thread de contrôle atteint un **nœud Final de l’activité**, actions simultanées de toute l’activité et des sous-activités se terminent.  
  
-   Vous pouvez utiliser plusieurs nœuds finaux de l'activité pour réduire l'encombrement causé par des connecteurs supplémentaires.  
  
### <a name="interrupting-the-activity"></a>Interruption de l'activité  
 Pour décrire la façon dont le flux ordinaire d'une activité peut être interrompu, par exemple si l'utilisateur décide d'annuler le processus, vous pouvez créer un nœud Accepter un événement à l'écoute de cet événement. Pour plus d’informations, consultez la section [flux simultanés](#Concurrent). Créez un flux de contrôle à partir de là vers un nœud final de l'activité (7).  
  
### <a name="swimlanes"></a>Couloirs  
 Il est parfois utile de réorganiser les actions d'une activité dans les zones correspondant aux différents objets ou rôles d'entreprise qui effectuent les actions. Ces zones sont réorganisées de manière conventionnelle en colonnes et sont appelées *couloirs*.  
  
- Utilisez les lignes ou les rectangles à partir de la **formes simples** section de la boîte à outils pour dessiner des couloirs ou autres zones.  
  
- Pour étiqueter chaque couloir, créez un commentaire et définissez son **Transparent** propriété **True**.  
  
  Les formes simples ne font pas partie du modèle UML et n'apparaissent pas dans l'Explorateur de modèles UML.  
  
##  <a name="DataFlows"></a> Description du flux de données  
 Vous pouvez décrire les données passées vers et depuis une activité de deux manières :  
  
-   Utilisez un **nœud de l’objet**. Il s'agit de la méthode la plus simple pour décrire des informations qui circulent entre des activités. Un nœud d'objet s'apparente à une variable dans un programme. Il représente un élément qui stocke une ou plusieurs valeurs qui passent d'une action à une autre.  
  
-   Utilisez un **broche de sortie** et un **broche d’entrée**. Cette méthode vous permet de décrire séparément les sorties d'une action et les entrées vers une autre. Les broches s'apparentent aux paramètres dans un programme. Les broches représentent des ports par lesquels les objets peuvent entrer dans une action et la quitter.  
  
    > [!NOTE]
    >  Pour une vue d’ensemble des éléments utilisés dans cette section, consultez la section flux de données de la rubrique [diagrammes d’activités UML : référence](../modeling/uml-activity-diagrams-reference.md).  
  
### <a name="describing-data-flow-with-object-nodes"></a>Description du flux de données à l'aide de nœuds d'objet  
 La plupart des flux de contrôle transportent des données. Par exemple, le flux de sortie de l'action « Le client fournit des détails » transporte une référence à l'adresse d'expédition.  
  
 Si vous souhaitez décrire ces données sur votre diagramme, vous pouvez remplacer un connecteur par un nœud d'objet et deux connecteurs, comme indiqué dans l'illustration suivante.  
  
 ![Les nœuds d’objet peuvent afficher des données passées entre les actions](../modeling/media/uml-actguidedata.png "UML_ActGuideData")  
  
 Notez que les rectangles aux angles arrondis, notamment Expédier les marchandises, représentent des actions où se déroule le traitement. Les rectangles aux angles droits, notamment Adresse d'expédition, représentent un flux d'objets d'une action vers une autre.  
  
 Donnez au nœud d'objet un nom qui reflète le rôle du nœud en tant que conduit ou mémoire tampon des objets qui circulent entre les actions.  
  
 Vous pouvez définir le **Type** du nœud d’objet dans la fenêtre Propriétés. Le type peut être un type primitif tel qu'un entier, ou une classe, une interface ou une énumération que vous avez définie dans un diagramme de classes. Par exemple, vous pouvez créer une classe Adresse d'expédition, avec les attributs Adresse postale, Ville, etc. ainsi qu'une association à une autre classe nommée Client. Pour plus d’informations, consultez [diagrammes de classes UML : indications](../modeling/uml-class-diagrams-guidelines.md).  
  
> [!NOTE]
>  Si vous tapez le nom d’un type qui n’a pas encore été défini, un élément est ajouté sous **Types non spécifiés** dans l’Explorateur de modèles UML. Si vous définissez par la suite un type de ce nom dans un diagramme de classes, vous devez réinitialiser le type du nœud d'objet pour qu'il fasse référence au nouveau type.  
  
#### <a name="buffering-data-in-object-nodes"></a>Mise en mémoire tampon de données dans des nœuds d'objet  
 Un nœud d'objet peut jouer le rôle d'une mémoire tampon pour plusieurs objets. Dans l'illustration suivante, le flux de contrôle indique que l'utilisateur peut suivre la boucle [sélection supplémentaire] (1) plusieurs fois, tandis que le nœud d'objet Éléments de menu choisis (2) accumule les choix de l'utilisateur. Enfin, quand l'utilisateur a terminé sa sélection, le contrôle passe à l'action Confirmer la commande (3), qui accepte la liste complète de choix de la mémoire tampon Éléments de menu choisis.  
  
 ![Mise en mémoire tampon des données dans les nœuds d’objet](../modeling/media/uml-actguidebuffer.png "UML_ActGuideBuffer")  
  
 Vous pouvez spécifier la façon dont les éléments sont stockés dans une mémoire tampon en définissant les propriétés du nœud d'objet :  
  
-   Définir le **Ordering** propriété :  
  
    -   **Non ordonnée** pour spécifier un ordre aléatoire ou non spécifié. (valeur par défaut).  
  
    -   **Classés** pour spécifier l’ordre selon une clé spécifique.  
  
    -   **FIFO** pour spécifier l’ordre du premier entré, premier sorti.  
  
    -   **LIFO** pour spécifier l’ordre du dernier entré, premier sorti.  
  
-   Définir le **limite supérieure** propriété pour spécifier le nombre maximal d’objets qui peuvent être contenus dans la mémoire tampon. La valeur par défaut est *. Cela signifie qu'il n'existe aucune limite.  
  
### <a name="describing-data-flow-with-input-and-output-pins"></a>Description du flux de données avec des broches d'entrée et de sortie  
 Utilisez un **broche de sortie** et un **broche d’entrée** pour décrire séparément les sorties d’une action et les entrées à un autre.  
  
 ![Broches d’entrée et de sortie sont des paramètres d’action](../modeling/media/uml-actguidepins.png "UML_ActGuidePins")  
  
 Pour créer un code confidentiel, cliquez sur **broche d’entrée** ou **broche de sortie** sur la boîte à outils puis cliquez sur une action. Vous pouvez ensuite déplacer la broche autour du périmètre de l'action et modifier son nom. Vous pouvez créer une entrée de broches et de sortie sur tout genre d’action, y compris **action appeler un comportement**, **action appeler une opération**, **action Envoyer un Signal**, et  **Accepter les Actions d’événement**.  
  
 Un connecteur entre deux broches représente un flux d'objet, tout comme les flux vers et à partir d'un nœud d'objet.  
  
 Donnez à chaque broche un nom qui indique le rôle des objets qu'il produit ou accepte, tel qu'un nom de paramètre.  
  
 Vous pouvez définir le type des objets transmis dans le **Type** propriété. Il doit s'agir d'un type que vous avez créé dans un diagramme de classes UML.  
  
 Les objets qui circulent entre des broches connectées doivent être compatibles d'une certaine façon. Cela peut notamment être dû au fait que les objets produits par la broche de sortie appartiennent à un type dérivé de celui de la broche d'entrée.  
  
 Vous pouvez également spécifier que le flux d'objet inclut une transformation qui convertit des données entre le type de la broche de sortie et le type de la broche d'entrée. La transformation la plus courante de ce genre extrait juste la partie appropriée d'un plus grand type. L'exemple figurant dans l'illustration implique l'existence d'une transformation qui extrait l'Adresse d'expédition à partir du Détail de la commande.  
  
##  <a name="Details"></a> Définition d’une Action plus en détail  
 Outre l'utilisation du nom de l'action pour clarifier le résultat qui doit être normalement obtenu, voici quelques façons d'ajouter davantage de détails à une action:  
  
-   Écrire une description plus détaillée le **corps** propriété. Par exemple, vous pouvez écrire un fragment de code du programme ou pseudo-code, ou une description complète des résultats obtenus.  
  
-   Remplacez l'action par une Action Appeler un comportement et décrivez son comportement détaillé dans un diagramme d'activités séparé. Consultez [description des sous-activités avec des Actions appeler un comportement](#Subactivities).  
  
-   Définissez l’action **Local Postconditions** et **Local Preconditions** propriétés décrivant son résultat de manière plus détaillée. Pour plus d’informations, consultez [définition de post-conditions et de conditions préalables](#Postcondition).  
  
###  <a name="Subactivities"></a> Description des sous-activités avec des Actions appeler un comportement  
 Vous pouvez décrire le comportement détaillé d'une action à l'aide d'un diagramme d'activités séparé. Un comportement appelé est un diagramme d'activités représenté sur votre diagramme d'activités principal par une Action Appeler un comportement. Vous pouvez également utiliser l'Action Appeler un comportement pour décrire un comportement partagé entre différentes activités pour éviter de dessiner plusieurs fois la sous-activité.  
  
 Dans l'illustration suivante, le diagramme 1 affiche une activité qui présente une Action Appeler un comportement et le diagramme 2 affiche le diagramme de sous-activité qui présente le comportement appelé.  
  
 ![Un diagramme d’activités distinct affiche des actions détaillées](../modeling/media/uml-actguidedetail.png "UML_ActGuideDetail")  
  
##### <a name="to-describe-a-sub-activity-with-a-call-behavior-action"></a>Pour décrire une sous-activité avec une Action Appeler un comportement  
  
1.  Pour créer le diagramme pour la sous-activité, dans **l’Explorateur de solutions**, avec le bouton droit de votre projet de modélisation, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue **modèles** cliquez sur **diagramme d’activités** et dans le **nom** zone, tapez le nom que vous projetez de donner à votre **Action appeler un comportement**.  
  
3.  Dessinez le flux de travail détaillé de la sous-activité. Il s'agit du comportement appelé.  
  
    -   Dans le diagramme de sous-activité appelé, le **nœud Initial** indique où démarre le contrôle lorsque le comportement est appelé. Le **nœud Final de l’activité** montre où le contrôle doit être retourné à l’activité parente.  
  
4.  Définir le **comportement** propriété de la **Action appeler un comportement** pour faire référence à un diagramme de comportement appelé.  
  
    > [!NOTE]
    >  Le diagramme de sous-activité doit contenir des éléments ou le diagramme ne sera pas disponible dans la liste déroulante pour le **comportement** propriété. En outre, l’icône de trident n’apparaît sur votre **Action appeler un comportement** mettre en forme jusqu'à ce que vous définissez son **comportement** propriété.  
  
5.  Définir le **Is Synchronous** propriété de l’action pour indiquer si votre activité attend que l’activité appelée se termine.  
  
    -   Si vous définissez **Is Synchronous** sur false, vous indiquez que le flux peut continuer à l’action suivante avant que l’activité appelée se termine. Vous ne devez pas définir des broches de sortie ou des flux de données sortants à partir de l'action.  
  
### <a name="describing-data-flow-in-and-out-of-sub-activities"></a>Description du flux de données vers et depuis des sous-activités  
 À l'image des paramètres d'un logiciel, vous pouvez décrire le flux de données vers et depuis des sous-activités.  
  
- Créez des broches d'entrée et de sortie (1) sur l'Action Appeler un comportement pour chaque fragment de données transféré vers et depuis l'action. Nommez chacune d'entre elles de manière appropriée.  
  
- Dans le diagramme de sous-activité, créez un **nœud de paramètre d’activité** (2) pour chaque broche d’entrée et de sortie sur l’action appelante. Donnez à chaque nœud le même nom que sa broche correspondante.  
  
  > [!NOTE]
  >  Un nœud du paramètre de l'activité ressemble à un nœud d'objet. Pour vérifier le type de nœud que vous recherchez, cliquez sur le nœud, puis cliquez sur **propriétés**. Le type de nœud est affiché dans l'en-tête de la fenêtre Propriétés.  
  
- Dans le diagramme de sous-activités, dessinez des connecteurs qui montrent le flux d'objets vers et depuis chaque nœud du paramètre de l'activité.  
  
  ![Épingle sur appeler un comportement mappent aux paramètres d’activité](../modeling/media/uml-actguidesub.png "UML_ActGuideSub")  
  
###  <a name="Postcondition"></a> Définition de post-conditions et les conditions préalables  
 Vous pouvez utiliser la **Local Postconditions** et **Local Preconditions** propriétés pour spécifier en détail le résultat d’une action. Ces propriétés décrivent l'effet de l'action sans décrire la façon dont l'effet est obtenu.  
  
 Pour définir ces propriétés, l’action de clic droit, puis cliquez sur **propriétés**. Tapez les valeurs des propriétés dans la fenêtre Propriétés.  
  
#### <a name="local-postconditions"></a>Post-conditions locales  
 Une post-condition est une condition qui doit être satisfaite avant que l'action puisse être considérée comme terminée. Dans l'exemple d'action Confirmer la commande, la post-condition peut être :  
  
 Le client a fourni des détails complets et valides qui sont obligatoires pour le traitement de sa carte de crédit.  
  
 Une post-condition peut exprimer une relation entre les états antérieur et postérieur au déroulement de l'action. Exemple :  
  
 Le taux d'intérêt a doublé par rapport à ce qu'il était précédemment.  
  
 Vous pouvez écrire des post-conditions dans un style plus formel, en faisant référence aux attributs spécifiques des données traitées dans les actions. Exemple :  
  
 `InvoiceTotal == Sum(OrderItem.MenuItem.Price)`  
  
#### <a name="local-preconditions"></a>Conditions préalables locales  
 Une condition préalable est une condition qui doit être remplie quand l'action est prête à commencer. Par exemple, l'action Confirmer la commande peut avoir pour condition préalable :  
  
 Le client a sélectionné au moins un élément du menu.  
  
### <a name="describing-calls-to-operations"></a>Description d'appels aux opérations  
 En général, une action décrit le travail effectué par toute combinaison de personnes, de logiciels ou d'ordinateurs. Mais vous pouvez utiliser une Action Appeler une opération pour décrire un appel à une méthode ou fonction d'un logiciel spécifique.  
  
-   Attribuez à l'Action Appeler une opération un nom indiquant quelle opération est appelée, et sur quel objet ou composant elle porte.  
  
-   Ajoutez des broches d'entrée et de sortie à l'Action Appeler une opération pour décrire les paramètres et les valeurs de retour.  
  
-   Vous pouvez définir le **Is Synchronous** propriété de l’action pour indiquer si votre activité attend que l’opération se termine.  
  
    -   Si vous définissez **Is Synchronous** sur false, vous indiquez que le flux peut continuer à l’action suivante avant la fin de l’opération appelée. Vous ne devez pas définir des broches de sortie ou des flux de données sortants à partir de l'action.  
  
##  <a name="Concurrent"></a> Flux simultanés  
 Vous pouvez utiliser la **nœud de bifurcation** et **nœud de jointure** pour décrire deux ou plusieurs threads d’activités qui peuvent s’exécuter en même temps.  
  
 ![Les nœuds de bifurcation et de jointure affichent des flux simultanés](../modeling/media/uml-actguideconcurrent.png "UML_ActGuideConcurrent")  
  
 L’effet de la **nœud de bifurcation** (1) consiste à diviser le thread de contrôle en deux ou plusieurs threads. Quand l'action précédente se termine, toutes les actions du côté sortie de la bifurcation peuvent démarrer.  
  
 Un **nœud de jointure** (2) réunit des threads simultanés. L’action après le **nœud de jointure** peut ne pas démarrer tant que toutes les actions conduisant à la **nœud de jointure** sont terminées.  
  
### <a name="describing-signals-and-events"></a>Description des signaux et des événements  
 Vous pouvez afficher une étape dans un processus qui envoie un signal sous la forme d'une Action Envoyer un signal dans une activité. Vous pouvez afficher une étape qui attend un signal ou un événement spécifique avant que l'étape ne puisse continuer en tant qu'Action Accepter un événement.  
  
 Par exemple, vous pouvez afficher une étape qui envoie une commande, puis une autre étape qui doit recevoir la commande avant de pouvoir la traiter.  
  
#### <a name="sending-a-signal"></a>Envoi d'un signal  
 Utilisez une Action Envoyer un signal (3) pour indiquer qu'un signal ou un message quelconque est envoyé aux autres activités ou processus. Utilisez le nom de l'action pour indiquer le genre de message qu'il envoie.  
  
-   Le contrôle passe immédiatement à l'action suivante dans le flux de contrôle (le cas échéant).  
  
-   Vous ne pouvez pas utiliser une Action Envoyer un signal pour décrire la façon dont votre processus répond aux informations retournées. Pour ce faire, utilisez une Action Accepter un événement séparée.  
  
-   Vous pouvez afficher le flux de données entrant dans une Action Envoyer un signal pour indiquer les données qui peuvent être envoyées avec le message sortant. Pour plus d’informations, consultez [décrivant le flux de données](#DataFlows).  
  
#### <a name="waiting-for-a-signal-or-event"></a>Attente d'un signal ou d'un événement  
 Utilisez une Action Accepter un événement (4) pour indiquer que cette activité attend un événement externe ou un message entrant. Utilisez le nom de l'action pour indiquer le type d'événement attendu.  
  
-   Pour indiquer que votre activité attend un message ou un événement externe à un point spécifique dans son flux, dessinez une Action Accepter un événement avec un flux entrant à l'emplacement approprié dans l'activité.  
  
-   Pour indiquer que votre activité peut répondre à tout moment à un message ou à un événement externe, dessinez une Action Accepter un événement sans aucun flux entrant. Quand l'événement externe nommé se produit, un nouveau thread commence dans votre activité à partir de l'Action Accepter un événement.  
  
-   Vous ne pouvez pas utiliser une Action Accepter un événement pour décrire une valeur retournée à l'émetteur du signal. Pour cela, utilisez une Action Envoyer un signal.  
  
-   Vous pouvez afficher des flux de données sortants à partir de l'action pour montrer la façon dont votre activité traite des données reçues dans le signal. Si vous souhaitez afficher plusieurs flux de sortie, vous devez définir le **IsUnmarshall** propriété de l’Action Accepter un événement, ce qui indique que l’action analyse le signal entrant dans ses composants séparés. Pour plus d’informations, consultez [décrivant le flux de données](#DataFlows).  
  
### <a name="describing-multiple-data-flows"></a>Description de plusieurs flux de données  
 Vous pouvez dessiner plusieurs flux de contrôle ou flux d'objet sortant d'une action afin d'indiquer que plusieurs threads émergent une fois l'action terminée. L'effet s'apparente à celui d'une bifurcation, à ceci près que vous pouvez utiliser un mélange de flux de contrôle et de flux d'objet.  
  
 L'exemple suivant présente plusieurs flux vers et depuis des actions.  
  
 ![Flux d’objets en parallèle](../modeling/media/uml-actguidemulti.png "UML_ActGuideMulti")  
  
 Quand l'action « Le client fournit des détails » se termine, elle génère deux objets : « Adresse d'expédition » et « Informations de carte de crédit ». Les deux objets sont ensuite traités par différentes actions.  
  
 Étant donné qu'une action nécessite que toutes ses entrées soient disponibles avant de pouvoir démarrer, la dernière action ne démarre pas tant que toutes les actions qui y mènent ne sont pas terminées.  
  
### <a name="streams"></a>Flux  
 Vous pouvez utiliser un diagramme d'activités pour vous aider à décrire un pipeline ou une série d'actions qui s'exécutent simultanément et passent des données en continu d'une action à une autre.  
  
 Dans l'exemple suivant, chaque action peut produire des objets et continuer à travailler. Étant donné qu'il n'y a pas de flux de contrôle, chaque action peut démarrer dès qu'elle reçoit ses premiers objets.  
  
 Notez que les connecteurs dans cet exemple sont des flux d'objet, car ils ont tous au moins une extrémité sur un nœud du paramètre de l'activité, un nœud d'objet ou une broche d'entrée ou de sortie.  
  
 ![Un flux de données](../modeling/media/uml-actguidestream.png "UML_ActGuideStream")  
  
 1. L'exemple montre trois nœuds du paramètre de l'activité, qui représentent ses entrées et ses sorties.  
  
 2. Les nœuds d'objet, les broches d'entrée et les broches de sortie peuvent représenter des mémoires tampons. Vous pouvez affecter à la propriété Upper Bound d'un nœud d'objet une valeur indiquant le nombre d'objets qui peuvent figurer simultanément dans la mémoire tampon.  
  
 3. Vous pouvez utiliser des nœuds de décision pour indiquer qu'un flux de données se divise, en envoyant différents objets le long de branches différentes. Vous pouvez utiliser des commentaires ou les titres de nœuds pour expliquer le critère de division.  
  
 4. Vous pouvez utiliser des nœuds de bifurcation pour montrer que deux copies d'objets ou plus sont effectuées, en les envoyant pour traitement simultané.  
  
 5. Vous pouvez utiliser des nœuds de jointure pour montrer que deux flux de traitement sont refusionnés en un.  
  
### <a name="selection-and-transformation"></a>Sélection et transformation  
 Vous pouvez spécifier que les objets dans un flux d'objet sont transformés, sélectionnés ou les deux à la fois. Un flux d'objet est un flux vers ou depuis une broche ou un nœud d'objet.  
  
- Une transformation décrit la façon dont les objets entrant dans un flux sont convertis en un autre type.  
  
- Une sélection décrit la façon dont seuls quelques-uns des objets entrant dans un flux sont transmis à l'action de réception.  
  
  L'exemple montre une transformation. La première action dans Diagramme 1 génère un code postal au niveau d'une broche de sortie. Cet élément est connecté à une broche d'entrée sur la deuxième action. Mais la deuxième action attend une adresse complète. La conversion d'un type à un autre est spécifiée dans une deuxième activité, Recherche d'adresse. Cet élément est référencé à partir de la propriété Transformation du flux d'objet. L'activité Recherche d'adresse contient un nœud du paramètre de l'activité pour le code postal entrant et un autre pour l'adresse complète sortante.  
  
  ![Transformation définie dans un autre diagramme de l’objet](../modeling/media/uml-actguidetransform.png "UML_ActGuideTransform")  
  
  Vous pouvez spécifier une transformation ou une sélection de deux façons :  
  
- En joignant un commentaire à la broche d'entrée ou de sortie.  
  
  -   Pour distinguer cette description d’un commentaire général, vous pouvez commencer le commentaire avec <\<**transformation**>> ou <\<**sélection**>>.  
  
- En spécifiant en détail la transformation ou la sélection dans un diagramme d'activités séparé.  
  
  -   Si vous utilisez cette méthode, joignez également un commentaire pour que les lecteurs sachent que la transformation a été définie.  
  
##### <a name="to-specify-a-transformation-or-selection-in-a-separate-activity-diagram"></a>Pour spécifier une transformation ou une sélection dans un diagramme d'activités séparé  
  
1. Créez un nouveau diagramme d'activités dans lequel décrire le flux de transformation ou de sélection.  
  
   -   Dans **l’Explorateur de solutions**, cliquez sur votre projet, pointez sur **ajouter**, cliquez sur **un nouvel élément**, puis cliquez sur **diagramme d’activités**. Donnez un nom approprié au diagramme pour le flux de transformation ou de sélection. Cliquez sur **Ajouter**.  
  
2. Dans le nouveau diagramme :  
  
   1.  Créez deux nœuds du paramètre de l'activité, un pour le flux d'entrée et un pour la sortie.  
  
   2.  Créez des actions interconnectées avec des flux d'objet. Cela illustre le fonctionnement de la transformation ou de la sélection.  
  
3. Dans tout diagramme dans lequel vous souhaitez utiliser la transformation ou la sélection :  
  
   1.  Créez un flux d'objet, c'est-à-dire un connecteur depuis ou vers une broche d'entrée ou de sortie, un nœud d'objet ou un nœud du paramètre de l'activité.  
  
   2.  Cliquez sur le flux d’objet, puis sur **propriétés**.  
  
   3.  Dans le **Transformation** ou **sélection** propriété, sélectionnez le diagramme dans lequel vous avez spécifié le flux de transformation ou de sélection.  
  
   Vous pouvez également définir une sélection pour un nœud d'objet, et sur les broches d'entrée et de sortie individuelles. Définissez une activité de sélection comme dans la procédure précédente, puis le **sélection** propriété de nœud d’objet ou la broche d’entrée ou de sortie.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier des modèles UML et des diagrammes](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagrammes de séquence UML : référence](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagrammes de composants UML : référence](../modeling/uml-component-diagrams-reference.md)   
 [Diagrammes de cas d’usage UML : référence](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagrammes de classes UML : référence](../modeling/uml-class-diagrams-reference.md)   
 [Diagrammes de composants UML : référence](../modeling/uml-component-diagrams-reference.md)   
 [Vidéo : Capture des flux de travail à l’aide de diagrammes d’activités](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-4-Capture-Business-Workflows/)



