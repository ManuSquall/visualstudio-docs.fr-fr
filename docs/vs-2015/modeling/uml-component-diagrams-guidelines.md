---
title: 'Diagrammes de composants UML : Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 6c1bdd60-369e-477e-83ed-7f6fe75c9f0b
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0b4a5e7e626e7cf9510047f0b016ff80ea8203e1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056781"
---
# <a name="uml-component-diagrams-guidelines"></a>Diagrammes de composants UML : Recommandations
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, vous pouvez dessiner un *diagramme de composant* pour afficher la structure d’un système logiciel. Pour une démonstration vidéo, consultez [Designing the Physical Structure à l’aide de diagrammes de composants](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-6-Designing-a-Projects-Physical-Structure/).  
  
 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Prise en charge des versions pour les outils d'architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Pour créer un diagramme de composant UML, dans le **Architecture** menu, cliquez sur **nouveau UML ou diagramme de couche**.  
  
 Un composant est une unité modulaire remplaçable dans son environnement. Ses éléments internes sont masqués, mais il a un ou plus bien définis *interfaces fournies* via ses fonctions accessibles. Un composant peut également avoir *interfaces obligatoires*. Une interface requise définit les fonctions ou services qu'elle exige des autres composants. En connectant les interfaces fournies et requises de plusieurs composants, un plus grand composant peut être développé. Un système logiciel complet peut donc être considéré comme un composant.  
  
 Le dessin de diagrammes de composants présente plusieurs avantages :  
  
- La réflexion à propos de votre conception relativement aux principaux blocs permet à l’équipe de développement de comprendre une conception existante ou d’en créer une.  
  
- En considérant votre système comme une collection de composants intégrant des interfaces fournies et requises bien définies, vous améliorez la séparation entre les différents composants. Cela facilite ensuite la compréhension de la conception, ainsi que sa modification lors de celle des impératifs.  
  
  Vous pouvez utiliser un diagramme de composant pour représenter votre conception, indépendamment du langage ou de la plateforme que la conception utilise ou utilisera.  
  
## <a name="OtherDiagrams"></a> Relation aux autres diagrammes  
 Vous pouvez utiliser un diagramme de composant avec d'autres diagrammes.  
  
|Autre diagramme|Permet d'évoquer et de communiquer ces aspects de votre conception|  
|-------------------|--------------------------------------------------------------------|  
|Diagramme de séquence UML|-Les interactions entre les composants d’un système<br />-Les interactions entre les différentes parties à l’intérieur d’un composant.<br /><br /> Pour plus d’informations, consultez [diagrammes de séquence UML : Les instructions](../modeling/uml-sequence-diagrams-guidelines.md).|  
|Diagramme de classes UML|-Les interfaces d’un composant. Le diagramme de classes vous permet de détailler les méthodes de l'interface.<br />-Les données envoyées dans les paramètres sur les interfaces de composants.<br /><br /> Pour plus d'informations, consultez [Diagrammes de classes UML : Les instructions](../modeling/uml-class-diagrams-guidelines.md).|  
|Diagrammes d'activités|-Le traitement interne exécuté par un composant en réponse aux messages entrants.<br /><br /> Pour plus d’informations, consultez [diagrammes d’activités UML : Les instructions](../modeling/uml-activity-diagrams-guidelines.md).|  
|Diagrammes de couche|-Couches architecturales logiques de vos composants.<br /><br /> Pour plus d’informations, consultez [diagrammes de couche : Référence](../modeling/layer-diagrams-reference.md).|  
  
## <a name="Basics"></a> Étapes de base pour dessiner des diagrammes de composant  
 Pour plus d’informations de référence sur les éléments de diagrammes de composants, consultez [diagrammes de composants UML : Référence](../modeling/uml-component-diagrams-reference.md).  
  
 Pour plus d’informations sur l’utilisation des diagrammes de composants en cours de conception, consultez [modéliser l’architecture de votre application](../modeling/model-your-app-s-architecture.md).  
  
> [!NOTE]
>  Les étapes détaillées pour créer un des diagrammes de modélisation sont décrites dans [modèles et diagrammes UML modifier](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-component-diagram"></a>Pour créer un diagramme de composant  
  
1. Sur le **Architecture** menu, cliquez sur **nouveau UML ou diagramme de couche**.  
  
2. Sous **modèles**, cliquez sur **diagramme de composant UML**.  
  
3. Nommez le diagramme.  
  
4. Dans **ajouter au projet de modélisation**, sélectionnez un projet de modélisation existant dans votre solution, ou **créer un nouveau projet de modélisation**, puis cliquez sur **OK**...  
  
     Un nouveau diagramme de composant apparaît avec le langage UML **diagramme de composant** boîte à outils. La boîte à outils contient les relations et éléments requis.  
  
### <a name="drawing-components"></a>Dessin de composants  
 ![Composants avec interfaces](../modeling/media/uml-compdrawing.png "UML_CompDrawing")  
  
 Créer un *composant* (1) pour chaque unité fonctionnelle principale dans votre système ou application.  
  
 Les exemples possibles sont les suivants : une application, un périphérique matériel, un service Web, un assembly .NET, une classe de programmes ou un groupe de classes, ou encore tout segment séparable d'un programme.  
  
##### <a name="to-create-components"></a>Pour créer des composants  
  
1. Cliquez sur **composant** dans la boîte à outils, puis cliquez sur une partie vide du diagramme.  
  
     \- ou -  
  
     Copiez et collez un composant existant.  
  
    1. Recherchez un composant existant dans un diagramme ou dans **Explorateur de modèles UML**.  
  
    2. Cliquez sur le composant, puis cliquez sur **copie**.  
  
    3. Ouvrez le diagramme dans lequel vous souhaitez que le composant copié apparaisse.  
  
    4. Cliquez sur une partie vide du diagramme, puis cliquez sur **coller**.  
  
         Une copie du composant apparaît alors avec un nouveau nom.  
  
2. Cliquez sur le nom du composant pour le modifier.  
  
3. Cliquez sur le chevron (5) si vous souhaitez uniquement afficher l'en-tête du composant.  
  
### <a name="showing-the-ports-of-a-component"></a>Affichage des ports d'un composant  
 Un *port* (2, 3) représente un groupe de messages ou d’appels d’opérations qui passent ou non par un composant. Le groupe est décrit par une interface qui définit le type du port. Un port peut fournir une interface ou en requérir une.  
  
 Un port avec un *interface fournie* (2) apporte des opérations qui sont implémentées par le composant, et qui peut être utilisé par d’autres composants.  
  
 Les exemples possibles sont les suivants : une interface utilisateur, un service Web, une interface .NET ou encore une collection de fonctions dans tous les langages de programmation.  
  
 Un port avec un *interface requise* (3) représente un impératif de composant pour un groupe d’opérations ou services fournis par d’autres composants ou systèmes externes.  
  
 Par exemple, un navigateur Web requiert des serveurs Web ou encore un complément d'application exige des services de l'application.  
  
 Un composant peut disposer de n'importe quel nombre de ports.  
  
##### <a name="to-add-ports-to-a-component"></a>Pour ajouter des ports à un composant  
  
1. Dans la boîte à outils, cliquez sur **Interface fournie** ou **Interface requise**.  
  
2. Cliquez sur le composant auquel vous souhaitez l'ajouter.  
  
    Un port apparaît sur la limite du composant.  
  
    Une nouvelle interface est créée en tant que type du port. Cette interface s’affiche dans **Explorateur de modèles UML**.  
  
3. Faites glisser le port autour de la limite du composant pour le placer là où vous le souhaitez.  
  
4. Faites glisser l'étiquette du port pour régler sa position.  
  
5. Cliquez sur l'étiquette pour la modifier. L'étiquette affiche le nom de l'interface. Si vous la modifiez, vous modifiez également le nom de l'interface.  
  
   Si vous souhaitez afficher les attributs et les opérations de l'interface, vous pouvez le faire en les ajoutant à l'interface dans l'Explorateur de modèles UML. Vous pouvez sinon faire glisser l'interface de l'Explorateur de modèles UML sur un diagramme de classes, puis ajouter les opérations et les attributs ici.  
  
### <a name="linking-between-components"></a>Liaison entre différents composants  
 Utilisez une dépendance (4) pour montrer qu'un impératif de composant peut être satisfait par les opérations ou services fournis par un autre composant.  
  
##### <a name="to-show-that-a-provided-interface-can-satisfy-a-required-interface"></a>Pour montrer qu'une interface fournie peut satisfaire une interface requise  
  
1. Dans la boîte à outils, cliquez sur **dépendance**.  
  
2. Cliquez sur le port avec l'interface requise sur un composant, puis sur le port avec l'interface fournie dans un autre composant.  
  
   Vous devez tenter d'éviter de concevoir des boucles de dépendance dans lesquelles tous les composants d'un groupe dépendent de tous les autres.  
  
##### <a name="to-add-a-port-for-an-existing-interface-to-a-component"></a>Pour ajouter un port pour une interface existante à un composant  
  
- Recherchez l’interface dans **Explorateur de modèles UML** , puis faites-la glisser jusqu’au composant.  
  
     - ou -  
  
- Copiez et collez une référence vers une interface à partir d'un diagramme.  
  
    1. Dans un diagramme de classes ou un diagramme de composant, avec le bouton droit de l’interface, puis sur **copie**.  
  
    2. Sur le diagramme de composant, cliquez sur le composant, puis cliquez sur **coller la référence**.  
  
         Une interface fournie apparaît alors sur le composant. Une balise d'action apparaît juste à côté.  
  
        > [!NOTE]
        >  Si vous utilisez **coller** au lieu de **coller la référence**, une nouvelle interface qui porte un nouveau nom sera créée.  
  
    3. Si vous souhaitez créer une interface requise, cliquez sur la balise d’Action, puis **convertir en Interface requise**.  
  
## <a name="Parts"></a> Affichage des éléments internes d’un composant  
 ![Diagramme de composant montrant des composants internes](../modeling/media/uml-compshowing.png "UML_CompShowing")  
  
 Vous pouvez placer des parties (3) dans un composant (1) pour montrer qu'il se compose de plus petits composants qui interagissent entre eux.  
  
 Le diagramme de l'illustration spécifie que toutes les instances du type Service Web DinnerNow contiennent une instance de Serveur Clients et une autre de Serveur Cuisine.  
  
 Une partie est une propriété de son composant parent, comme un attribut appartient à une classe ordinaire. Une partie possède son propre type, qui est généralement aussi un composant. L'étiquette de la partie présente la même forme qu'un attribut ordinaire :  
  
 `+ partName : TypeName`  
  
 Dans le composant parent, chaque partie affiche les interfaces fournies et requises définies pour son type (4, 5). Les opérations ou services requis par une partie peuvent être fournis par une autre. Vous pouvez utiliser **partie Assembly** des connecteurs pour montrer comment les parties sont interconnectées (6).  
  
 Vous pouvez également montrer qu'une interface du composant parent est réellement fournie ou requise par l'une de ses parties. Vous pouvez vous connecter à un port du parent à un port d’une partie interne à l’aide un **délégation** relation (9). Les deux ports doivent être du même genre (fourni ou requis) et leurs genres d'interfaces doivent être compatibles.  
  
 Vous pouvez créer une partie avec un nouveau type ou à partir d'un type existant.  
  
#### <a name="to-add-parts-to-a-component"></a>Pour ajouter des parties à un composant  
  
1. Créez une partie pour chaque unité fonctionnelle principale que vous considérez comme étant une partie du composant parent.  
  
    1. Cliquez sur **composant** dans la boîte à outils, puis cliquez sur dans le composant parent (1).  
  
         Un nouveau composant (3) apparaît à l'intérieur du composant parent.  
  
         Un composant est créé dans **Explorateur de modèles UML**. Il s'agit du type de la nouvelle partie.  
  
         \- ou -  
  
         Faites glisser un composant existant entre l'Explorateur de modèles UML et le composant parent.  
  
         Un nouveau composant (3) apparaît à l'intérieur du composant parent. Son type est le composant que vous avez fait glisser depuis l'Explorateur de modèles UML.  
  
         \- ou -  
  
         Avec le bouton droit à un composant, dans un diagramme ou dans l’Explorateur de modèles UML et puis cliquez sur **copie**.  
  
         Avec le bouton droit sur le composant parent, puis cliquez sur **coller la référence**.  
  
         Un nouveau composant (3) apparaît à l'intérieur du composant parent. Son type est le composant que vous avez copié.  
  
    2. Cliquez sur le nom de la nouvelle partie pour le modifier. Vous ne pouvez pas modifier son type.  
  
    3. Vous pouvez ajouter des interfaces fournies et requises (4, 5) à la nouvelle partie. Cliquez sur le **Interface fournie** ou **Interface requise** outil, puis cliquez sur dans la partie.  
  
         \- ou -  
  
         Faites glisser une interface existante à partir de **Explorateur de modèles UML** sur la partie.  
  
         Les interfaces sont ajoutées au type de la partie et apparaissent sur la partie elle-même. Si nécessaire, le composant parent règle sa taille.  
  
2. Interconnectez les parties.  
  
    - Utilisez le **dépendance** outil pour connecter les ports de différentes parties (6).  
  
3. Connectez les parties aux ports du composant parent :  
  
    1. Créez un ou plusieurs ports (7) sur le composant parent. Cliquez sur **Interface requise** ou **Interface fournie** sur la boîte à outils, puis cliquez sur le composant parent.  
  
    2. Déléguez (9) le port à une ou plusieurs parties. Cliquez sur le **délégation** outil, puis un port sur le composant parent et un port sur une partie. De la même manière, vous pouvez connecter des ports qui fournissent ou requièrent des interfaces.  
  
### <a name="showing-the-parts-of-a-part"></a>Affichage des parties d'une autre partie  
 Après avoir divisé un composant en différentes parties, vous pouvez faire de même pour chacun des types de parties à l'aide de parties internes spécifiques.  
  
 Il est plus facile de créer les couches de décomposition dans un diagramme de composant distinct. Vous devez d'abord localiser le type de la partie. Par exemple, l'une des parties est nommée `DNCustomerServer`dans l'illustration et son type est un composant appelé `CustomerServer`. Vous pouvez rechercher ce type dans l'Explorateur de modèles UML et le placer dans un autre diagramme. Puis, vous pouvez créer ses propres parties internes.  
  
##### <a name="to-place-a-parts-type-on-a-diagram"></a>Pour placer le type d'une partie dans un diagramme  
  
1. Déterminez le nom qualifié complet du type de la partie.  
  
     Avec le bouton droit de la partie, puis cliquez sur **propriétés**.  
  
     Le nom du type s’affiche dans le **Type** champ de la fenêtre Propriétés.  
  
2. Recherchez le type de pièce dans **Explorateur de modèles UML**.  
  
     Cliquez sur **vue**, pointez sur **Windows autres**, puis cliquez sur **Explorateur de modèles UML**.  
  
     Développez le projet et, si nécessaire, tous les packages auxquels appartient le type.  
  
     Le type est répertorié comme un **composant**.  
  
     Si vous le souhaitez, vous pouvez modifier son nom ici.  
  
3. Ouvrez ou créez un autre diagramme de composant.  
  
4. Effectuez un glisser-déposer depuis le type dans l'Explorateur de modèles UML vers le diagramme.  
  
     Une vue du type s'affiche alors en tant que composant dans le diagramme.  
  
     Elle intègre les mêmes interfaces que vous avez définies pour la partie.  
  
     Vous pouvez maintenant y ajouter des parties.  
  
## <a name="Designing"></a> Conception du composant  
  
### <a name="describing-how-the-parts-collaborate"></a>Description de la collaboration des parties  
 Vous pouvez dessiner un diagramme de séquences pour montrer comment les parties collaborent, en réponse à un message qui arrive dans le composant parent.  
  
 Vous pouvez utiliser ces diagrammes pour décrire un composant existant et pour en concevoir un nouveau.  
  
 Si le composant est toujours en cours de conception, vous pouvez dessiner des diagrammes de séquences avant d'avoir déterminé les parties qui lui seront intégrées. Vous pouvez utiliser les diagrammes de séquences pour utiliser différentes parties, interfaces requises ou encore séquences de messages. Dessinez des diagrammes de séquences pour les messages entrants les plus fréquents et les plus importants. Vous pouvez ensuite créer des parties dans votre composant qui correspondent aux lignes de vie que vous avez déterminées.  
  
 Utilisez les diagrammes de séquences pour évaluer comment le travail du système est réparti entre les différents composants.  
  
- Si une quantité trop importante est affectée à une partie donnée, l'application sera probablement plus difficile à mettre à jour que si le travail est uniformément réparti.  
  
- Si le travail est trop uniformément réparti et que de nombreuses interactions sont présentes, il se peut que le système s'exécute de manière incorrecte et qu'il soit difficile à comprendre.  
  
  ![Diagramme présentant collaboration les parties de la séquence](../modeling/media/uml-compdescparts.png "UML_CompDescParts")  
  
##### <a name="to-draw-a-sequence-diagram-that-shows-collaboration-between-parts"></a>Pour dessiner un diagramme de séquences qui affiche une collaboration entre les différentes parties  
  
1. Créez un diagramme de séquences.  
  
     Pour plus d’informations, consultez [diagrammes de séquence UML : Les instructions](../modeling/uml-sequence-diagrams-guidelines.md).  
  
2. Créez une ligne de vie pour un composant externe, un utilisateur, un périphérique ou un autre acteur (1) qui envoie des messages à ce composant.  
  
     Vous pouvez définir le **acteur** propriété de cette ligne de vie sur true, pour indiquer qu’il est externe au composant concerné. Un dessin minimaliste apparaît au-dessus de la ligne de vie.  
  
3. Créez une ligne de vie pour l'interface fournie (2) de ce composant auquel l'acteur choisi envoie des messages.  
  
4. Créez une ligne de vie pour chaque partie (3) du composant.  
  
5. Créez une ligne de vie pour chaque interface requise (4) du composant.  
  
6. Dessinez des messages à partir de l'acteur externe (5). Montrez comment le message est passé aux parties et comment elles collaborent pour répondre au message.  
  
7. Si nécessaire, affichez les messages envoyés à une interface requise (6). N'affichez pas de détail dans l'exécution du message.  
  
### <a name="is-the-component-more-than-its-parts"></a>Le composant est-il plus qu'un assemblage de différentes parties ?  
 Dans certains cas, un composant n'est pas plus qu'un nom donné à une collection de parties. L’ensemble du travail est effectué par les parties et, au moment de l’exécution, aucun code ou autre artefact ne représente le composant.  
  
 Vous pouvez indiquer cela dans le modèle en définissant le **Is Indirectly Instantiated** propriété du composant. Dans ce cas, toutes les interfaces du composant doivent se trouver au niveau des ports, avec des délégations aux parties internes.  
  
### <a name="describing-the-process-inside-each-part"></a>Description du processus à l'intérieur de chaque partie  
 Vous pouvez utiliser des diagrammes d'activités pour montrer comment un composant traite chaque message entrant. Pour plus d’informations, consultez [diagrammes d’activités UML : Les instructions](../modeling/uml-activity-diagrams-guidelines.md).  
  
 ![Diagramme d’activités avec tampon de données](../modeling/media/uml-compdescribingproc.png "UML_CompDescribingProc")  
  
 Utilisez une action Accepter un événement (1) pour montrer qu'un message entrant démarre un nouveau thread.  
  
 Utilisez des nœuds d'objets et des broches d'entrée/de sortie pour afficher le flux d'informations et l'emplacement de stockage des informations. Dans l'exemple, un nœud d'objet (2) permet d'afficher des éléments mis en mémoire tampon entre deux threads.  
  
### <a name="defining-data-and-classes"></a>Définition des données et des classes  
 Vous pouvez utiliser un diagramme de classes UML pour décrire le contenu détaillé des éléments suivants :  
  
- Interfaces des composants. Lorsque vous ajoutez un port requis ou fourni à un composant, une interface s'affiche dans l'Explorateur de modèles UML. Vous pouvez la faire glisser ou la copier dans un diagramme de classes UML pour afficher ses attributs et opérations, et ses relations avec d'autres interfaces.  
  
- Données passées dans les paramètres d'opérations dans les interfaces.  
  
- Données stockées dans les composants (par exemple, comme indiqué dans les flux d'objets des diagrammes d'activités).  
  
### <a name="general-dependencies-between-components"></a>Dépendances générales entre composants  
 Vous ne pouvez utiliser un diagramme de composant que pour afficher les principales parties de votre conception et leurs interdépendances.  
  
 ![Une dépendance entre les composants](../modeling/media/uml-compdepend.png "UML_CompDepend")  
  
 Utilisez le **dépendance** pour dessiner une dépendance. Cela indique que la conception d'un composant compte sur un autre.  
  
 Les genres classiques de dépendances sont les suivants :  
  
- Un composant appelle le code dans l'autre.  
  
- Un composant instancie une classe définie dans une autre.  
  
- Un composant utilise des informations créées par un autre.  
  
  Vous pouvez utiliser le nom de la flèche de dépendance pour dénoter un genre particulier d'utilisation. Pour définir le nom, cliquez sur la flèche, puis cliquez sur **propriétés**et définissez le **nom** champ dans la fenêtre Propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier des modèles UML et des diagrammes](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagrammes de composants UML : Référence](../modeling/uml-component-diagrams-reference.md)   
 [Diagrammes de séquence UML : Référence](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagrammes de cas d’usage UML : Référence](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagrammes de classes UML : Référence](../modeling/uml-class-diagrams-reference.md)   
 [Diagrammes de composants UML : Référence](../modeling/uml-component-diagrams-reference.md)   
 [Vidéo : Conception de la Structure physique à l’aide de diagrammes de composants](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-6-Designing-a-Projects-Physical-Structure/)
