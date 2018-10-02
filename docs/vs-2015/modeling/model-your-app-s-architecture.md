---
title: Modéliser votre application&#39;architecture s | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML, modeling architecture
ms.assetid: aedce746-9df5-49e1-9662-67eb1b83d313
caps.latest.revision: 21
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: f07ac7b18564a14c3c71e6647f519ee47d40c9a0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504796"
---
# <a name="model-your-app39s-architecture"></a>Modéliser votre application&#39;architecture s
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [modéliser votre application&#39;architecture s](https://docs.microsoft.com/visualstudio/modeling/model-your-app-s-architecture).  
  
Pour vous assurer que votre application ou votre système logiciel répond à vos utilisateurs a besoin, vous pouvez créer des modèles dans Visual Studio dans le cadre de votre description de la structure globale et du comportement de votre application ou votre système logiciel. Avec des modèles, vous pouvez également décrire des modèles utilisés tout au long de la conception. Ces modèles vous aident à comprendre l'architecture existante, à discuter des modifications et à communiquer clairement vos intentions.  
  
 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Prise en charge des versions pour les outils d'architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 L'objectif d'un modèle est de réduire les ambiguïtés présentes dans les descriptions en langage naturel et de vous aider, vous et vos collègues, à visualiser la conception et à discuter des conceptions alternatives. Un modèle doit être utilisé avec d'autres documents ou discussions. En soi, un modèle ne représente pas une spécification complète de l'architecture.  
  
> [!NOTE]
>  Dans cette rubrique, le terme « système » signifie le logiciel que vous développez. Il peut s'agir d'une grande collection de nombreux composants matériels et logiciels, d'une application unique ou d'une partie d'une application.  
  
 L'architecture d'un système peut être divisée en deux parties :  
  
-   [Conception de haut niveau](#Structure). Cette section décrit les principaux composants et comment ils interagissent pour répondre à chaque spécification. Si le système est grand, chaque composant peut avoir sa propre conception de haut niveau qui montre comment il est constitué de composants plus petits.  
  
-   [Modèles de conception](#Patterns) et les conventions utilisées dans les conceptions des composants. Un modèle décrit une approche particulière visant à atteindre un objectif de programmation. En utilisant les mêmes modèles lors de toutes les phases de conception, votre équipe peut réduire le coût des modifications et du développement de nouveaux logiciels.  
  
##  <a name="Structure"></a> Conception de haut niveau  
 Une conception de haut niveau décrit les principaux composants de votre système et la façon dont ils interagissent pour atteindre les objectifs de la conception. Le développement de la conception de haut niveau implique d'effectuer les activités dans la liste ci-dessous, mais pas nécessairement dans un ordre particulier.  
  
 Si vous mettez à jour du code existant, vous pouvez commencer par décrire les principaux composants. Assurez-vous de bien comprendre les modifications apportées aux besoins des utilisateurs, puis ajoutez ou modifiez les interactions entre les composants. Si vous développez un nouveau système, commencez par comprendre les caractéristiques principales des besoins des utilisateurs. Vous pouvez ensuite explorer des séquences d'interactions pour les cas d'usage principaux, puis consolider les séquences dans une conception de composant.  
  
 Dans tous les cas, il est utile de développer les différentes activités en parallèle et de développer le code et les tests à un stade précoce. N'essayez pas de terminer l'un de ces aspects avant d'en commencer un autre. En règle générale, les impératifs et votre compréhension de la meilleure façon de concevoir le système évolueront pendant l'écriture et les tests du code. Vous devez donc commencer par comprendre et coder les caractéristiques principales des impératifs et de votre conception. Remplissez les détails dans les itérations ultérieures du projet.  
  
-   [Comprendre les impératifs](#Requirements). Le point de départ de toute conception est une vision claire des besoins des utilisateurs.  
  
-   [Modèles architecturaux](#BigDecisions). Choix que vous avez effectués concernant les principales technologies et éléments de l'architecture du système.  
  
-   [Composants et leurs Interfaces](#Components). Vous pouvez dessiner des diagrammes de composants pour illustrer les principales parties du système et montrer les interfaces via lesquelles elles interagissent. Les interfaces de chaque composant incluent tous les messages que vous avez identifiés dans les diagrammes de séquence.  
  
-   [Interactions entre les composants](#Interactions). Pour chaque cas d'usage, événement ou message entrant, vous pouvez dessiner un diagramme de séquence qui montre comment les principaux composants du système interagissent pour obtenir le résultat demandé.  
  
-   [Modèle de données des composants et des Interfaces](#Data). Vous pouvez dessiner des diagrammes de classes pour décrire les informations passées entre les composants et stockées dans les composants.  
  
##  <a name="Requirements"></a> Comprendre les impératifs  
 Pour développer efficacement la conception de haut niveau d'une application complète, il est préférable de l'associer à un modèle d'impératifs ou autre description des besoins des utilisateurs. Pour plus d’informations sur les modèles d’impératifs, consultez [modéliser les besoins des utilisateurs](../modeling/model-user-requirements.md).  
  
 Si le système que vous développez est un composant d'un système plus grand, tout ou partie de vos impératifs peuvent être exprimés dans des interfaces de programmation.  
  
 Le modèle d'impératifs fournit les renseignements essentiels suivants :  
  
-   Interfaces fournies. Une interface fournie énumère les services ou les opérations que le système ou le composant doit fournir à ses utilisateurs, qu'il s'agisse d'utilisateurs humains ou d'autres composants logiciels.  
  
-   Interfaces requises. Une interface requise énumère les services ou les opérations que le système ou le composant peut utiliser. Dans certains cas, vous pourrez concevoir tous ces services dans le cadre de votre propre système. Dans d'autres cas, en particulier si vous concevez un composant qui peut être combiné à d'autres composants dans de nombreuses configurations, l'interface requise sera définie par des considérations externes.  
  
-   Impératifs de qualité de service. Objectifs et contraintes de performances, de sécurité, de fiabilité et autres que le système doit satisfaire.  
  
 Le modèle d'impératifs est écrit du point de vue des utilisateurs de votre système, qu'il s'agisse de personnes ou d'autres composants logiciels. Ils ne savent rien des mécanismes internes de votre système. En revanche, votre objectif dans un modèle architectural consiste à décrire les mécanismes internes et à montrer comment ils répondent aux besoins des utilisateurs.  
  
 Avoir des modèles d'impératifs et d'architecture distincts est utile, car cela facilite la discussion des impératifs avec les utilisateurs. Cela aide aussi à refactoriser la conception et à considérer des architectures alternatives tout en laissant les impératifs inchangés.  
  
 Vous pouvez séparer les modèles d'impératifs et d'architecture de deux façons :  
  
-   Conservez-les dans la même solution mais dans des projets différents. Ils apparaîtront comme des modèles séparés dans l'Explorateur de modèles UML. Différents membres d'équipe pourront travailler en parallèle sur les modèles. Vous pourrez créer des types de suivi limités entre les modèles.  
  
-   Placez-les dans le même modèle UML, mais dans différents packages. Cela facilite le suivi des dépendances entre les modèles, mais empêche que plusieurs personnes puissent travailler en même temps sur le modèle. En outre, un modèle très étendu prendra plus de temps à charger dans Visual Studio. Cette approche est donc moins adaptée aux grands projets.  
  
 La quantité de détails que vous devez mettre dans un modèle d'impératifs ou d'architecture dépend de l'échelle du projet et de la taille et de la distribution de l'équipe. Pour une petite équipe sur un projet de courte durée, le dessin d'un diagramme de classes des concepts métier et de quelques modèles de conception peut suffire. Pour un grand projet distribué sur plusieurs régions, beaucoup plus de détails seront nécessaires.  
  
##  <a name="BigDecisions"></a> Modèles architecturaux  
 Lors de la phase initiale de développement, vous devez choisir les principaux éléments et technologies dont dépend la conception. Ces choix porteront sur les aspects suivants :  
  
-   Choix technologiques, tels que le choix entre une base de données et un système de fichiers, le choix entre une application en réseau et un client web, et ainsi de suite.  
  
-   Choix d'infrastructure, tels que le choix entre Windows Workflow Foundation et ADO.NET Entity Framework.  
  
-   Choix de méthode d'intégration, par exemple entre un bus de service d'entreprise et un canal point à point.  
  
 Ces choix sont fréquemment déterminés par les impératifs de qualité de service, tels que l'échelle et la flexibilité, et peuvent être effectués avant que les impératifs détaillés soient connus. Dans un système à grande échelle, les configurations matérielle et logicielle sont étroitement liées.  
  
 Vos sélections affectent votre mode d'utilisation et votre interprétation du modèle architectural. Par exemple, dans un système qui utilise une base de données, les associations dans un diagramme de classes peuvent représenter des relations ou des clés étrangères dans la base de données, tandis que dans un système basé sur des fichiers XML, les associations peuvent indiquer des références croisées qui utilisent XPath. Dans un système distribué, les messages figurant dans un diagramme de séquence peuvent représenter des messages sur le câble. Dans une application autonome, ils peuvent représenter des appels de fonction.  
  
##  <a name="Components"></a> Composants et leurs Interfaces  
 Les principales recommandations de cette section sont les suivantes :  
  
-   Créez des diagrammes de composants pour illustrer les principales parties de votre système.  
  
-   Dessinez des dépendances entre les composants ou leurs interfaces pour illustrer la structure du système.  
  
-   Utilisez des interfaces sur les composants pour montrer les services que chaque composant fournit ou nécessite.  
  
-   Dans une conception à grande échelle, vous pouvez dessiner des diagrammes séparés pour décomposer chaque composant en plus petites parties.  
  
 Ces points sont développés dans le reste de cette section.  
  
### <a name="components"></a>Composants  
 Les vues centrales d'un modèle d'architecture sont les diagrammes de composants qui illustrent les parties principales du système et leurs interdépendances. Pour plus d’informations sur les diagrammes de composants, consultez [diagrammes de composants UML : référence](../modeling/uml-component-diagrams-reference.md).  
  
 ![Diagramme de composant UML illustrant les différentes parties](../modeling/media/uml-barecomponent.png "UML_BareComponent")  
  
 Un diagramme de composant par défaut pour un grand système peut inclure les composants suivants :  
  
-   Présentation. Composant qui fournit l'accès à l'utilisateur, généralement exécuté dans un navigateur web.  
  
-   Composants de service web. Fournit la connexion entre les clients et les serveurs.  
  
-   Contrôleurs de cas d'usage. Guide l'utilisateur lors des étapes de chaque scénario.  
  
-   Cœur de métier. Contient des classes basées sur des classes dans le modèle d'impératifs, implémente les opérations majeures et impose des contraintes d'entreprise.  
  
-   Base de données. Stocke les objets métier.  
  
-   Composants de journalisation et de gestion des erreurs.  
  
### <a name="dependencies-between-components"></a>Dépendances entre composants  
 Outre les composants proprement dits, vous pouvez montrer leurs interdépendances. Une flèche de dépendance entre deux composants indique que changer la conception de l'un pourrait affecter la conception de l'autre. Cela se produit généralement quand un composant utilise les services ou les fonctions fournis par l'autre composant, directement ou indirectement.  
  
 Une architecture correctement structurée présente une disposition claire des dépendances, où les conditions suivantes sont remplies :  
  
-   Il n'y a pas de boucle sur une carte de code.  
  
-   Les composants peuvent être disposés en couches, où chaque dépendance passe d'un composant dans une couche à un composant dans la suivante. Toutes les dépendances entre deux couches vont dans la même direction.  
  
 Vous pouvez afficher les dépendances directement entre les composants ou entre les interfaces requises et fournies associées aux composants. L'utilisation d'interfaces vous permet de définir les opérations qui sont utilisées dans chaque dépendance. En général, les dépendances entre les composants sont indiquées lors du dessin initial des diagrammes, puis elles sont remplacées par des dépendances entre les interfaces à mesure que des informations sont ajoutées. Les deux versions sont des descriptions correctes du logiciel, mais la version avec les interfaces fournit plus de détails que la version antérieure.  
  
 La gestion des dépendances est très importante si l'on souhaite que les logiciels soient faciles à tenir à jour. Les diagrammes de composants doivent refléter toutes les dépendances dans votre code. Si le code existe déjà, assurez-vous que toutes les dépendances sont illustrées dans les diagrammes. Si le code est en cours de développement, assurez-vous qu'il ne comprend pas de dépendances qui ne sont pas planifiées dans le diagramme de composant. Pour vous aider à découvrir des dépendances dans le code, vous pouvez générer des diagrammes de couche. Pour vous aider à garantir que vos contraintes de dépendances planifiées sont respectées, vous pouvez valider le code par rapport aux diagrammes de couche. Pour plus d’informations, consultez [diagrammes de couche : référence](../modeling/layer-diagrams-reference.md).  
  
### <a name="interfaces"></a>Interfaces  
 En plaçant des interfaces sur vos composants, vous pouvez séparer et nommer les principaux groupes d'opérations fournis par chaque composant. Par exemple, les composants d'un système de vente par Internet peuvent avoir une interface via laquelle les clients achètent des articles, une interface via laquelle les fournisseurs mettent à jour leurs catalogues et une troisième interface via laquelle les le système est géré.  
  
 Un composant peut avoir autant d'interfaces fournies et requises que vous le souhaitez. Les interfaces fournies montrent les services fournis par le composant et utilisables par d'autres composants. Les interfaces requises montrent les services que le composant utilise dans d'autres composants.  
  
 Définir à la fois des interfaces fournies et requises vous aide à séparer clairement le composant du reste de la conception, pour pouvoir appliquer ces techniques :  
  
-   Placer le composant dans un atelier de test dans lequel les composants environnants sont simulés par l'atelier de test.  
  
-   Développer votre composant indépendamment des autres composants.  
  
-   Réutiliser le composant dans d'autres contextes en associant ses interfaces à différents composants.  
  
 Quand vous souhaitez définir la liste des opérations dans une interface, vous pouvez créer une autre vue de l'interface sur un diagramme de classes UML. Pour cela, recherchez l'interface dans l'Explorateur de modèles UML et faites-la glisser sur un diagramme de classes. Vous pouvez ensuite ajouter des opérations à l'interface.  
  
 Une opération dans une interface UML peut représenter toute manière par laquelle un comportement d'un composant peut être appelé. Elle peut représenter une demande de service web, un signal ou une interaction d'un autre genre ou un appel de fonction de programme ordinaire.  
  
 Pour déterminer les opérations à ajouter, créez des diagrammes de séquence pour montrer comment les composants interagissent. Consultez [Interactions entre les composants](#Interactions). Chacun de ces diagrammes de séquence montre les interactions qui se produisent dans un cas d'usage différent. De cette manière, vous pouvez ajouter progressivement à la liste des opérations dans l'interface de chaque composant, à mesure que vous explorez les cas d'usage.  
  
### <a name="decomposing-a-component-into-parts"></a>Décomposition d'un composant en parties  
 Vous pouvez appliquer la procédure décrite dans les sections précédentes à chaque composant.  
  
 Dans chaque composant, vous pouvez afficher les sous-composants en tant que Parties. Une Partie est un attribut de son composant parent, qui est un genre de classe. Chaque Partie a son propre type, qui peut être un composant. Vous pouvez placer ce composant sur un diagramme et afficher ses parties. Pour plus d’informations, consultez [diagrammes de composants UML : indications](../modeling/uml-component-diagrams-guidelines.md).  
  
 Il est utile appliquer cette technique à l'ensemble du système. Dessinez-le sous forme de composant unique et affichez ses principaux composants sous forme de parties. Cela vous aide à identifier clairement les interfaces de votre système avec le monde externe.  
  
 Quand votre conception d'un composant utilise un autre composant, vous avez souvent le choix entre le représenter en tant que partie ou en tant que composant distinct auquel vous accédez via une Interface requise.  
  
 Utilisez les Parties dans les situations suivantes :  
  
-   La conception du composant parent doit toujours utiliser le type de composant de la Partie. Ainsi, la conception de la partie fait partie intégrante de la conception du composant parent.  
  
-   Le composant parent en lui-même n'a aucune existence concrète. Par exemple, vous pourriez avoir un composant conceptuel nommé Couche de présentation qui représente une collection de composants réels qui gèrent les vues et les interactions de l'utilisateur.  
  
 Utilisez des composants distincts accessibles par le biais d'interfaces requises dans les situations suivantes :  
  
-   Le composant demandeur peut être associé via ses interfaces à différents composants fournisseurs au moment de l'exécution.  
  
-   La conception est telle qu'il serait facile de remplacer un fournisseur par un autre.  
  
 Il est généralement préférable d'utiliser des interfaces requises plutôt que des parties. Bien que la conception puisse être plus longue, le système qui en résulte est plus flexible. Il est également plus facile de tester les composants séparément. Cela permet d'avoir moins de couplage dans les plans de développement.  
  
##  <a name="Interactions"></a> Interactions entre les composants  
 Les principales recommandations de cette section sont les suivantes :  
  
-   Identifiez les cas d'usage de votre système.  
  
-   Pour chaque cas d'usage, dessinez un ou plusieurs diagrammes pour indiquer comment les composants de votre système parviennent au résultat demandé en collaborant les uns avec les autres et avec les utilisateurs. Habituellement, il s'agit de diagrammes de séquence ou de diagrammes d'activités.  
  
-   Utilisez des interfaces pour spécifier les messages reçus par chaque composant.  
  
-   Décrivez les effets des opérations dans les interfaces.  
  
-   Répétez cette procédure pour chaque composant, en montrant comment interagissent ses parties.  
  
 Par exemple, dans un système de vente basé sur le web, le modèle d'impératifs peut définir un achat de client comme un cas d'usage. Vous pouvez créer un diagramme de séquence pour illustrer les interactions entre le client et les composants de la couche de présentation et pour illustrer les interactions entre ces derniers et les composants d'entrepôt et de comptabilité.  
  
### <a name="identifying-the-initiating-events"></a>Identification des événements de lancement  
 Le travail effectué par la plupart des systèmes logiciels peut facilement être divisé en fonction des réponses fournies selon différentes entrées ou événements. L'événement de lancement peut être l'un des événements suivants :  
  
-   La première action dans un cas d'usage. Elle peut apparaître dans le modèle d'impératifs en tant qu'étape dans un cas d'usage ou action dans un diagramme d'activités. Pour plus d’informations, [diagrammes de cas d’usage UML : indications](../modeling/uml-use-case-diagrams-guidelines.md) et [diagrammes d’activités UML : instructions](../modeling/uml-activity-diagrams-guidelines.md).  
  
-   Un message au niveau d'une interface de programmation. Si le système que vous développez un composant d'un système plus grand, vous devez le décrire en tant qu'opération dans l'une des interfaces du composant. Consultez [composants et leurs Interfaces](#Components).  
  
-   Une condition particulière contrôlée par votre système ou un événement normal tel qu'une heure de la journée.  
  
### <a name="describe-the-computations"></a>Décrire les calculs  
 Dessinez des diagrammes de séquence pour montrer comment les composants répondent à l'événement initial.  
  
 Dessinez une ligne de vie pour chaque instance de composant qui participe à une séquence typique. Dans certains cas, il peut y avoir plusieurs instances de chaque type. Si vous avez décrit votre système entier en tant que composant unique, il doit y avoir une ligne de vie pour chaque Partie qu'il contient.  
  
 Pour plus d’informations, consultez [diagrammes de séquence UML : indications](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 Les diagrammes d'activités sont également utiles dans certains cas. Par exemple, si vos composants ont un flux continu de données, vous pouvez le décrire en tant que flux d'objet. Si votre composant a un algorithme complexe, vous pouvez le décrire en tant que flux de contrôle. Veillez à indiquer clairement quel composant exécute quelle action, par exemple à l'aide de commentaires. Pour plus d’informations, consultez [diagrammes d’activités UML : instructions](../modeling/uml-activity-diagrams-guidelines.md).  
  
### <a name="specify-the-operations"></a>Spécifier les opérations  
 Les diagrammes montrent les opérations qui sont effectuées par chaque composant, représentées sous forme de messages sur un diagramme de séquence ou sous forme d'actions sur un diagramme d'activités.  
  
 Recueillez ces opérations pour chaque composant. Créez des Interfaces fournies sur le composant et ajoutez les opérations aux interfaces. En général, on utilise une interface distincte pour chaque type de client. Les opérations sont plus facilement ajoutées aux interfaces dans **Explorateur de modèles UML**. De la même manière, recueillez les opérations utilisées par chaque composant à partir des autres composants et placez-les dans les Interfaces requises jointes au composant.  
  
 Il est utile d'ajouter des commentaires aux diagrammes d'activités ou de séquence, pour noter ce qui a été accompli après chaque opération. Vous pouvez également écrire l’effet de chaque opération dans son **post-conditions locales** propriété.  
  
###  <a name="Data"></a> Modèle de données des composants et des Interfaces  
 Définissez les paramètres et les valeurs de retour de chaque opération dans les interfaces de composant. Là où les opérations représentent des appels tels que des demandes de service web, les paramètres sont les renseignements envoyés dans le cadre de la demande. Si plusieurs valeurs sont retournées à partir d’une opération, vous pouvez utiliser des paramètres avec le **Direction** propriété définie sur **Out**.  
  
 Chaque paramètre et valeur de retour a un type. Vous pouvez définir ces types à l'aide de diagrammes de classes UML. Vous n'êtes pas obligé de représenter le détail de l'implémentation dans ces diagrammes. Par exemple, si vous décrivez des données transmises au format XML, vous pouvez utiliser une association pour représenter tout type de référence croisée entre les nœuds du document XML et utiliser des classes pour représenter les nœuds.  
  
 Utilisez des commentaires pour décrire les contraintes métier sur les associations et les attributs. Par exemple, si tous les articles sur la commande d'un client doivent provenir du même fournisseur, vous pouvez décrire ceci par référence aux associations entre les articles de la commande et les articles du catalogue de produits, et entre l'article du catalogue et son fournisseur.  
  
##  <a name="Patterns"></a> Modèles de conception  
 Un modèle de conception est un plan qui décrit comment concevoir un aspect particulier du logiciel, en particulier un aspect qui se reproduit dans différentes parties du système. En adoptant une approche uniforme dans tout le projet, vous pouvez réduire le coût de conception, garantir la cohérence dans l'interface utilisateur et réduire le coût de gestion et de modification du code.  
  
 Certains modèles de conception généraux tels qu'Observer sont bien connus et largement applicables. En outre, il existe des modèles qui sont applicables uniquement à votre projet. Par exemple, dans un système de ventes sur le web, il y aura plusieurs opérations dans le code où des modifications seront apportées à une commande de client. Pour vous assurer que l'état de la commande est affiché correctement à chaque étape, toutes ces opérations doivent suivre un protocole particulier pour mettre à jour la base de données.  
  
 Une partie du travail d'architecture logicielle consiste à déterminer quels modèles doivent être adoptés dans toute la conception. Il s'agit généralement d'une tâche continue, car de nouveaux modèles et des améliorations de modèles existants seront découverts à mesure que le projet progresse. Il est utile d'organiser le plan de développement pour que vous puissiez tester chacun de vos principaux modèles de conception à un stade précoce.  
  
 La plupart des modèles de conception peuvent être intégrés en partie dans le code d'infrastructure. Une partie du modèle peut être réduite à obliger le développeur à utiliser des classes ou des composants spécifiques, tels qu'une couche d'accès de base de données qui garantit la gestion correcte de la base de données.  
  
 Un modèle de conception est décrit dans un document et comprend généralement les parties suivantes :  
  
-   Nom.  
  
-   Description du contexte dans lequel il est applicable. Quels critères doivent inciter un développeur à envisager l'application de ce modèle ?  
  
-   Brève explication du problème qu'il résout.  
  
-   Modèle des principales parties et de leurs relations. Il peut s'agir de classes ou de composants et d'interfaces, avec des associations et des dépendances entre eux. Les éléments appartiennent généralement à deux catégories :  
  
    -   Éléments que le développeur doit dupliquer dans chaque partie du code où le modèle est utilisé. Vous pouvez utiliser des types de modèles pour les décrire. Pour plus d’informations, consultez [diagrammes de cas d’usage UML : référence](../modeling/uml-use-case-diagrams-reference.md).  
  
    -   Éléments décrivant les classes d'infrastructure que le développeur doit utiliser.  
  
-   Modèle des interactions entre les parties, à l'aide de diagrammes de séquence ou d'activités.  
  
-   Conventions d'attribution de noms.  
  
-   Description de la façon dont le modèle résout le problème.  
  
-   Description des variations que les développeurs peuvent être en mesure d'adopter.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier des modèles UML et des diagrammes](../modeling/edit-uml-models-and-diagrams.md)   
 [Visualiser le code](../modeling/visualize-code.md)   
 [Modéliser les besoins des utilisateurs](../modeling/model-user-requirements.md)   
 [Développer des tests à partir d’un modèle](../modeling/develop-tests-from-a-model.md)   
 [Utiliser des modèles dans votre processus de développement](../modeling/use-models-in-your-development-process.md)



