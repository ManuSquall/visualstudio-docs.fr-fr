---
title: 'Scénario : Modifier votre conception à l’aide de la visualisation et modélisation | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
ms.assetid: ccc80825-a4a0-44fa-a0bb-f95254785a3b
caps.latest.revision: 63
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 220666e6fe12e6a5ab3bbaf1238c19d761427cea
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303041"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scénario : modifier votre conception à l'aide de la visualisation et de la modélisation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Assurez-vous que votre système logiciel répond aux besoins des utilisateurs à l’aide des outils de visualisation et de modélisation dans Visual Studio. Utilisez des outils comme les diagrammes UML (Unified Modeling Language), les cartes de code, les diagrammes de couche et les diagrammes de classes pour effectuer les tâches ci-dessous :  
  
 Pour connaître les versions de Visual Studio qui prennent en charge chaque outil, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
-   Clarifier les besoins des utilisateurs et les processus d’entreprise.  
  
-   Visualiser et explorer le code existant.  
  
-   Décrire les modifications apportées à un système existant.  
  
-   Vérifier que le système satisfait à ses spécifications.  
  
-   Maintenir la cohérence du code avec la conception.  
  
 Cette procédure pas à pas :  
  
-   décrit ce que ces outils peuvent apporter à votre projet de logiciel ;  
  
-   montre comment utiliser ces outils, quelle que soit votre approche du développement, à l’aide d’un exemple de scénario.  
  
 Pour en savoir plus sur ces outils et les scénarios qu’ils prennent en charge, consultez :  
  
-   [Analyse et modélisation de l’architecture](../modeling/analyze-and-model-your-architecture.md)  
  
-   [Visualiser du code](../modeling/visualize-code.md)  
  
-   [Créer des modèles pour votre application](../modeling/create-models-for-your-app.md)  
  
##  <a name="ScenarioOverview"></a> Vue d’ensemble du scénario  
 Ce scénario décrit certaines étapes des cycles de vie du développement de logiciels dans deux entreprises fictives : Dinner Now et Lucerne Publishing. Dinner Now propose un service web de livraison de repas à Seattle. Les clients peuvent commander des repas et les payer sur le site web de Dinner Now. Les commandes sont alors envoyées au restaurant local chargé de les livrer. Lucerne Publishing, une société implantée à New York, exerce plusieurs activités liées ou non au web. Par exemple, elle gère un site web sur lequel ses clients peuvent publier leurs commentaires sur des restaurants.  
  
 Lucerne a récemment acquis Dinner Now et veut apporter les modifications suivantes :  
  
-   Intégrer le site web de Dinner Now en y ajoutant des fonctionnalités de publication d’avis sur les restaurants.  
  
-   Remplacer le système de paiement de Dinner Now par celui de Lucerne.  
  
-   Développer les services Dinner Now dans toute la région.  
  
 Dinner Now utilise SCRUM et eXtreme Programming, des outils qui offrent une couverture de test très élevée et comportent très peu de code non pris en charge. Dinner Now réduit les risques en créant des versions légères mais fonctionnelles d’un système, puis en ajoutant progressivement des fonctionnalités. Elle développe le code sur des itérations courtes et fréquentes. Cela lui permet d’intégrer les modifications en toute confiance, de refactoriser fréquemment le code et d’éviter un lourd travail de conception en amont.  
  
 Lucerne tient à jour une collection bien plus importante et complexe de systèmes,  certains d’entre eux datant de plus de 40 ans. La société fait preuve d’une grande prudence pour apporter des modifications en raison de la complexité et de la portée du code hérité. Elle suit un processus de développement plus rigoureux, préférant concevoir des solutions détaillées, et documenter la conception et les modifications effectuées pendant le développement.  
  
 Les deux équipes utilisent des diagrammes de modélisation dans Visual Studio pour développer des systèmes qui répondent mieux aux besoins des utilisateurs. Elles utilisent Team Foundation Server en parallèle d’autres outils pour planifier, organiser et gérer leur travail.  
  
 Pour plus d’informations sur Team Foundation Server, consultez :  
  
-   [Planification et suivi du travail](#PlanningTracking)  
  
-   [Test, validation et archivage du code mis à jour](#TestValidateCheckInCode)  
  
##  <a name="ModelingDiagramsTools"></a> Rôles de l’architecture et des diagrammes de modélisation dans le développement de logiciels  
 Le tableau suivant décrit les rôles que ces outils peuvent jouer pendant diverses étapes du cycle de développement logiciel :  
  
||**Modélisation des besoins des utilisateurs**|**Modélisation des processus d’entreprise**|**Architecture et conception du système**|**Visualisation et exploration du code**|**Vérification**|  
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|  
|Diagramme de cas d’usage (UML)|√|√|||√|  
|Diagramme d'activités (UML)|√|√|√||√|  
|Diagramme de classes (UML)|√|√|√||√|  
|Diagramme de composant (UML)|√|√|√||√|  
|Diagramme de séquence (UML)|√|√|√||√|  
|Diagramme de langage spécifique à un domaine (DSL)|√|√|√|||  
|Diagramme de couche, validation de couche|||√|√|√|  
|Carte de code|||√|√|√|  
|Concepteur de classes (basé sur le code)||||√||  
  
 Pour dessiner des diagrammes UML et des diagrammes de couche, vous devez créer un projet de modélisation dans le cadre d’une solution existante ou nouvelle. Ces diagrammes doivent être créés dans le projet de modélisation. Les éléments des diagrammes UML font partie d’un modèle commun et les diagrammes UML sont des vues de ce modèle. Les éléments des diagrammes de couche se trouvent dans le projet de modélisation, mais ils ne sont pas stockés dans le modèle commun. Les cartes de code et les diagrammes de classes .NET créés à partir du code sont externes au projet de modélisation.  
  
 Consultez :  
  
-   [Créer des projets et des diagrammes de modélisation UML](../modeling/create-uml-modeling-projects-and-diagrams.md)  
  
-   [Créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Mapper les dépendances à travers vos solutions](../modeling/map-dependencies-across-your-solutions.md)  
  
-   [Guide pratique pour ajouter des diagrammes de classes aux projets (Concepteur de classes)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
-   [SDK de modélisation pour Visual Studio - Langages spécifiques à un domaine](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  
  
 Pour afficher d’autres vues de l’architecture, vous pouvez réutiliser certains éléments du même modèle sur plusieurs ou différents diagrammes. Par exemple, faites glisser un composant vers un autre diagramme de composant ou vers un diagramme de séquence à utiliser en tant qu’acteur. Consultez [modèles et diagrammes UML modifier](../modeling/edit-uml-models-and-diagrams.md).  
  
 Les deux équipes utilisent également la validation de couche pour s’assurer que le code en cours de développement reste cohérent avec la conception.  
  
 Consultez :  
  
-   [Maintien de la cohérence du code avec la conception](#ValidatingCode)  
  
-   [Décrire l’Architecture logique : diagrammes de couche](#DescribeLayers)  
  
-   [Valider du code avec des diagrammes de couche](../modeling/validate-code-with-layer-diagrams.md)  
  
    > [!NOTE]
    >  Certaines versions de Visual Studio prennent en charge la validation de couche et les versions en lecture seule des cartes de code et des diagrammes UML à des fins de visualisation et de modélisation. Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Prise en charge des versions pour les outils d'architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
##  <a name="UnderstandingCommunicating"></a> Présentation et communication des informations sur le système  
 Il n’y a pas d’ordre impératif pour l’utilisation des diagrammes de modélisation Visual Studio. Vous pouvez donc les utiliser comme vous le voulez, en fonction de vos besoins ou de votre approche. En règle générale, les équipes revoient leurs modèles de façon répétée et fréquente au cours d’un projet. Chaque diagramme possède ses propres atouts pour vous aider à comprendre, décrire et communiquer différents aspects du système en cours de développement.  
  
 Les sociétés Dinner Now et Lucerne communiquent entre elles et avec les parties prenantes des projets en utilisant des diagrammes comme langage commun. Par exemple, Dinner Now utilise des diagrammes pour effectuer ces tâches :  
  
-   visualiser le code existant ;  
  
-   communiquer avec Lucerne sur les récits utilisateur nouveaux ou mis à jour ;  
  
-   identifier les modifications requises pour prendre en charge des récits utilisateur nouveaux ou mis à jour.  
  
 Lucerne utilise des diagrammes pour effectuer ces tâches :  
  
-   découvrir le processus d’entreprise de Dinner Now ;  
  
-   comprendre la conception du système ;  
  
-   communiquer avec Dinner Now sur les besoins nouveaux ou mis à jour des utilisateurs ;  
  
-   documenter les mises à jour du système.  
  
 Les diagrammes sont intégrés à Team Foundation Server pour que les équipes puissent planifier, gérer et suivre leur travail plus facilement. Par exemple, les équipes utilisent des modèles pour identifier des cas de test et des tâches de développement, et pour estimer leur travail. Lucerne lie les éléments de travail Team Foundation Server aux éléments de modèle, ce qui permet aux équipes de surveiller la progression du travail et de s’assurer que le système répond aux besoins des utilisateurs. Par exemple, la liaison de cas d’usage à des éléments de travail de cas de test permet de savoir que les cas d’usage sont remplis quand tous les tests sont réussis.  
  
 Avant que les équipes archivent leurs modifications, elles valident le code par rapport aux tests et à la conception en exécutant des builds qui incluent une validation de couche et des tests automatisés. Ainsi, le code mis à jour n’entre pas en conflit avec la conception et ne nuit pas aux fonctionnalités qui étaient opérationnelles auparavant.  
  
 Consultez :  
  
-   [Présentation du rôle du système dans le processus d’entreprise](#UnderstandingBPMandSystemDesign)  
  
-   [Décrire les besoins des utilisateurs nouveaux ou mis à jour](#DescribingURM)  
  
-   [Création de tests à partir de modèles](#CreatingTests)  
  
-   [Identification des modifications apportées au système existant](#DeterminingChanges)  
  
-   [Keeping code consistent with the design](#ValidatingCode)  
  
-   [Conseils généraux sur la création et l’utilisation de modèles](#GeneralTips)  
  
-   [Planification et suivi du travail](#PlanningTracking)  
  
-   [Test, validation et archivage du code mis à jour](#TestValidateCheckInCode)  
  
###  <a name="UnderstandingBPMandSystemDesign"></a> Présentation du rôle du système dans le processus d’entreprise  
 Lucerne veut en savoir plus sur le processus d’entreprise de Dinner Now. Elle crée les diagrammes suivants pour mieux comprendre le processus Dinner Now :  
  
|**Diagramme**|**Éléments décrits**|  
|-----------------|-------------------|  
|*Diagramme de cas d’usage (UML)*<br /><br /> Consultez :<br /><br /> -   [Diagrammes de cas d’usage UML : référence](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagrammes de cas d’usage UML : indications](../modeling/uml-use-case-diagrams-guidelines.md)|-Les activités qui prend en charge par le système Dinner Now<br />-Les personnes et les systèmes externes qui effectuent les activités<br />-Les principaux composants du système qui prennent en charge chaque activité<br />-Les parties du processus d’entreprise situés en dehors de l’étendue du système actuel, par exemple, livraison des repas|  
|*Diagramme d’activités (UML)*<br /><br /> Consultez :<br /><br /> -   [Diagrammes d’activités UML : référence](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagrammes d’activités UML : indications](../modeling/uml-activity-diagrams-guidelines.md)|Flux des étapes qui se produisent quand un client crée une commande|  
|*Diagramme de classes (UML)*<br /><br /> Consultez :<br /><br /> -   [Diagrammes de classes UML : référence](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagrammes de classes UML : indications](../modeling/uml-class-diagrams-guidelines.md)|Entités métier et termes utilisés dans la discussion, et relations entre ces entités. Par exemple, « commande » et « élément de menu » font partie du vocabulaire de ce scénario.|  
  
 Par exemple, Lucerne crée le diagramme de cas d’usage suivant pour présenter les tâches effectuées sur le site web de Dinner Now et les personnes qui les effectuent :  
  
 ![Diagramme de cas d’usage UML](../modeling/media/uml-usecase.png "UML_UseCase")  
  
 **Diagramme de cas d’usage UML**  
  
 Le diagramme d’activités suivant décrit le flux des étapes quand un client crée une commande sur le site web de Dinner Now. Dans cette version, des éléments de commentaire identifient les rôles et des lignes créent des *couloirs*, qui permettent d’organiser les étapes par rôle :  
  
 ![Diagramme d’activités UML](../modeling/media/uml-dinnernowprocess.png "UML_DinnerNowProcess")  
  
 **Diagramme d’activités UML**  
  
 Le diagramme de classes suivant décrit les entités qui participent au processus de commande :  
  
 ![Diagramme de classes UML](../modeling/media/uml-dinnerorders.png "UML_DinnerOrders")  
  
 **Diagramme de classes UML**  
  
###  <a name="DescribingURM"></a> Décrire les besoins des utilisateurs nouveaux ou mis à jour  
 Lucerne veut ajouter des fonctionnalités au système Dinner Now pour que les clients puissent lire les avis sur des restaurants et y contribuer. La société met à jour les diagrammes suivants pour pouvoir décrire ce nouveau besoin et en discuter avec Dinner Now :  
  
|**Diagramme**|**Éléments décrits**|  
|-----------------|-------------------|  
|*Diagramme de cas d’usage (UML)*<br /><br /> Consultez :<br /><br /> -   [Diagrammes de cas d’usage UML : référence](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagrammes de cas d’usage UML : indications](../modeling/uml-use-case-diagrams-guidelines.md)|Un nouveau cas d’usage pour « Donner un avis sur un restaurant »|  
|*Diagramme d’activités (UML)*<br /><br /> Consultez :<br /><br /> -   [Diagrammes d’activités UML : référence](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagrammes d’activités UML : indications](../modeling/uml-activity-diagrams-guidelines.md)|Étapes qui se produisent quand un client veut donner son avis sur un restaurant|  
|*Diagramme de classes (UML)*<br /><br /> Consultez :<br /><br /> -   [Diagrammes de classes UML : référence](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagrammes de classes UML : indications](../modeling/uml-class-diagrams-guidelines.md)|Données requises pour enregistrer un avis|  
  
 Par exemple, le diagramme de cas d’usage suivant inclut un nouveau cas d’usage « Donner un avis » pour représenter le nouveau besoin. Il est surligné en orange dans le diagramme pour en faciliter l’identification :  
  
 ![Diagramme de cas d’usage UML](../modeling/media/uml-writerev.png "UML_WriteRev")  
  
 **Diagramme de cas d’usage UML**  
  
 Le diagramme d’activités suivant inclut de nouveaux éléments en orange décrivant le flux des étapes du nouveau cas d’usage :  
  
 ![Diagramme d’activités UML](../modeling/media/uml-writereview.png "UML_WriteReview")  
  
 **Diagramme d’activités UML**  
  
 Le diagramme de classes suivant inclut une nouvelle classe Avis et décrit ses relations avec d’autres classes pour que les équipes puissent en discuter les détails. Notez qu’un client et qu’un restaurant peuvent comporter plusieurs avis :  
  
 ![Diagramme de classes UML](../modeling/media/uml-dinnerreviews.png "UML_DinnerReviews")  
  
 **Diagramme de classes UML**  
  
###  <a name="CreatingTests"></a> Création de Tests à partir de modèles  
 Les deux équipes conviennent qu’elles ont besoin d’un ensemble complet de tests pour le système et ses composants avant de procéder à toute modification. Lucerne dispose d’une équipe spécialisée qui effectue les tests au niveau du système et de chaque composant. Elle réutilise les tests créés par Dinner Now et les structure à l’aide de diagrammes UML :  
  
-   Chaque cas d’usage est représenté par un ou plusieurs tests. Les éléments inclus dans le diagramme de cas d’usage sont liés à des éléments de travail de cas de test dans Team Foundation Server.  
  
-   Chaque flux figurant dans un diagramme d’activités ou un diagramme de séquence au niveau du système est lié à au moins un test. L’équipe de test vérifie systématiquement qu’elle teste chaque tracé possible dans l’ensemble du diagramme d’activités.  
  
-   Les termes utilisés pour décrire les tests se basent sur ceux définis par les diagrammes de cas d’usage, de classes et d’activités.  
  
 Quand les besoins changent et que les diagrammes sont mis à jour pour refléter ces modifications, les tests sont mis à jour en conséquence. Un besoin est considéré comme rempli uniquement quand les tests réussissent. Quand c’est possible ou plus pratique, les tests sont définis et basés sur des diagrammes UML avant le début de l’implémentation.  
  
 Consultez :  
  
-   [Développer des tests à partir d’un modèle](../modeling/develop-tests-from-a-model.md)  
  
-   [Valider votre modèle UML](../modeling/validate-your-uml-model.md)  
  
###  <a name="DeterminingChanges"></a> Identifying Changes to the Existing System  
 Dinner Now doit estimer le coût de réalisation pour remplir le nouveau besoin. Ce coût dépend en partie des répercussions de cette modification sur les autres parties du système. Pour mieux déterminer ce coût, l’un des développeurs de Dinner Now crée ces cartes et diagrammes à partir du code existant :  
  
|**Carte ou diagramme**|**Éléments décrits**|  
|------------------------|---------------|  
|*Carte de code*<br /><br /> Consultez :<br /><br /> -   [Mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Parcourir et réorganiser des cartes de code](../modeling/browse-and-rearrange-code-maps.md)<br />-   [Personnaliser des cartes de code en modifiant les fichiers DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Dépendances et autres relations dans le code.<br /><br /> Par exemple, Dinner Now peut commencer par examiner les cartes de code des assemblys pour avoir une vue d’ensemble des assemblys et de leurs dépendances. La société peut explorer les cartes pour examiner les espaces de noms et les classes figurant dans ces assemblys.<br /><br /> Dinner Now peut également créer des cartes pour examiner certaines zones et d’autres types de relations dans le code. Elle utilise l’Explorateur de solutions pour rechercher et sélectionner les zones et les relations qui l’intéressent.|  
|*Diagramme de classes basé sur le code*<br /><br /> Consultez [How to: Add Class Diagrams to Projects (Class Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Classes existantes dans le code|  
  
 Par exemple, le développeur crée une carte de code. Il ajuste la portée pour se concentrer sur les zones concernées par le nouveau scénario. Ces zones sont sélectionnées et mises en surbrillance sur la carte :  
  
 ![Graphique de dépendance Namespace](../modeling/media/namespace-reviewsystem.png "Namespace_ReviewSystem")  
  
 **Carte de code des espaces de noms**  
  
 Le développeur développe les espaces de noms sélectionnés pour en voir les classes, les méthodes et les relations :  
  
 ![Graphique de dépendance d’espace de noms développé](../modeling/media/dep-reviewsystem.png "Dep_ReviewSystem")  
  
 **Carte de code des espaces de noms développée avec les liens entre les groupes**  
  
 Le développeur examine le code pour trouver les classes et méthodes affectées. Pour voir les effets de chaque modification apportée, régénérez les cartes de code après chaque modification. Consultez [visualiser le code](../modeling/visualize-code.md).  
  
 Pour décrire les modifications apportées à d’autres parties du système, notamment les composants ou les interactions, l’équipe peut dessiner ces éléments sur des tableaux blancs. Elle peut également dessiner les diagrammes suivants dans Visual Studio pour que les détails puissent être capturés, gérés et compris par les deux équipes :  
  
|**Diagrammes**|**Éléments décrits**|  
|------------------|-------------------|  
|*Diagramme d’activités (UML)*<br /><br /> Consultez :<br /><br /> -   [Diagrammes d’activités UML : référence](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagrammes d’activités UML : indications](../modeling/uml-activity-diagrams-guidelines.md)|Flux des étapes qui se produisent quand le système détecte qu’un client passe une nouvelle commande auprès d’un restaurant, l’invitant alors à donner son avis.|  
|*Diagramme de classes (UML)*<br /><br /> Consultez :<br /><br /> -   [Diagrammes de classes UML : référence](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagrammes de classes UML : indications](../modeling/uml-class-diagrams-guidelines.md)|Classes logiques et leurs relations. Par exemple, une nouvelle classe est ajoutée pour décrire un **Avis** et ses relations avec d’autres entités, telles que **Restaurant**, **Menu**et **Client**.<br /><br /> Pour associer des avis à un client, le système doit enregistrer des informations sur le client. Un diagramme de classes UML peut permettre de clarifier ces informations.|  
|*Diagramme de classes basé sur le code*<br /><br /> Consultez [How to: Add Class Diagrams to Projects (Class Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Classes existantes dans le code.|  
|*Diagramme de composant (UML)*<br /><br /> Consultez :<br /><br /> -   [Diagrammes de composants UML : référence](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagrammes de composants UML : indications](../modeling/uml-component-diagrams-guidelines.md)|Parties visibles du système, comme le site web de Dinner Now et ses interfaces. Ces interfaces définissent la manière dont les composants interagissent entre eux via les méthodes ou services qu’ils fournissent et consomment.|  
|*Diagramme de séquence (UML)*<br /><br /> Consultez :<br /><br /> -   [Diagrammes de séquence UML : référence](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagrammes de séquence UML : indications](../modeling/uml-sequence-diagrams-guidelines.md)|Séquence d’interactions entre les instances.|  
  
 Par exemple, le diagramme de composant suivant montre le nouveau composant, qui fait partie du composant Site web de Dinner Now. Le composant ReviewProcessing gère la fonctionnalité de création des avis et apparaît surligné en orange :  
  
 ![Diagramme de composant UML](../modeling/media/uml-internal.png "UML_Internal")  
  
 **Diagramme de composant UML**  
  
 Le diagramme de séquence suivant montre la séquence des interactions qui se produisent quand le composant Site web de Dinner Now vérifie si le client a déjà commandé auprès d’un restaurant auparavant. Le cas échéant, le client est invité à donner son avis, lequel est envoyé au restaurant et publié sur le site web :  
  
 ![Diagramme de séquence UML](../modeling/media/uml-revsystem.png "UML_RevSystem")  
  
 **Diagramme de séquence UML**  
  
###  <a name="ValidatingCode"></a> Maintien de la cohérence du code avec la conception  
 Dinner Now doit s’assurer que le code mis à jour demeure cohérent avec la conception. Pour cela, elle crée des diagrammes de couche qui décrivent les couches de fonctionnalité dans le système, spécifient les dépendances autorisées entre elles et associent des artefacts de solution à ces couches.  
  
|**Diagramme**|**Éléments décrits**|  
|-----------------|-------------------|  
|*Diagramme de couche*<br /><br /> Consultez :<br /><br /> -   [Créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagrammes de couche : référence](../modeling/layer-diagrams-reference.md)<br />-   [Diagrammes de couche : instructions](../modeling/layer-diagrams-guidelines.md)<br />-   [Valider du code avec des diagrammes de couche](../modeling/validate-code-with-layer-diagrams.md)|Architecture logique du code.<br /><br /> Un diagramme de couche organise et associe les artefacts dans une solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] avec des groupes abstraits appelés *couches*. Ces couches identifient les rôles, les tâches ou les fonctions que ces artefacts effectuent dans le système.<br /><br /> Les diagrammes de couche sont utiles pour décrire la conception prévue du système et valider le code en constante évolution par rapport à cette conception.<br /><br /> Pour créer des couches, faites glisser des éléments à partir de l’Explorateur de solutions, des cartes de code, de l’affichage de classes et de l’Explorateur d’objets. Pour dessiner de nouvelles couches, utilisez la boîte à outils ou cliquez avec le bouton droit sur la surface du diagramme.<br /><br /> Pour afficher les dépendances existantes, cliquez avec le bouton droit sur la surface du diagramme de couche, puis cliquez sur **Générer des dépendances**. Pour spécifier les dépendances prévues, dessinez de nouvelles dépendances.|  
  
 Par exemple, le diagramme de couche suivant décrit les dépendances entre les couches et le nombre d’artefacts associés à chaque couche :  
  
 ![Diagramme de couche du système de paiement intégré](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **Diagramme de couche**  
  
 Pour empêcher d’éventuels conflits avec la conception pendant le développement du code, les équipes utilisent la validation de couche sur les builds exécutées sur Team Foundation Build. Elles créent également une tâche MSBuild personnalisée pour exiger la validation de couche dans leurs opérations d’archivage. Elles utilisent des rapports de build pour collecter les erreurs de validation.  
  
 Consultez :  
  
-   [Définir votre processus de génération](http://msdn.microsoft.com/library/61593e10-d24b-492f-b19a-af4d85abea6b)  
  
-   [Utiliser un processus de génération d’archivage contrôlé pour la validation des modifications](http://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)  
  
-   [Personnaliser votre modèle de processus de génération](http://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
###  <a name="GeneralTips"></a> General Tips for Creating and Using Models  
  
-   La plupart des diagrammes sont constitués de nœuds connectés par des lignes. Pour chaque type de diagramme, la boîte à outils fournit différents types de nœuds et de lignes.  
  
     Pour ouvrir la boîte à outils, dans le menu **Affichage** , cliquez sur **Boîte à outils**.  
  
-   Pour créer un nœud, faites-le glisser de la boîte à outils vers le diagramme. Certains types de nœuds doivent être déplacés vers des nœuds existants. Par exemple, sur un diagramme de composant, un nouveau port doit être ajouté à un composant existant.  
  
-   Pour créer une ligne ou une connexion, cliquez sur l’outil approprié dans la boîte à outils, cliquez sur le nœud source, puis cliquez sur le nœud cible. Certaines lignes peuvent être créées uniquement entre certains types de nœuds. Quand vous déplacez le pointeur sur une source ou une cible possible, le pointeur indique si vous pouvez créer une connexion.  
  
-   Quand vous créez des éléments sur des diagrammes UML, vous les ajoutez également à un modèle commun. Les diagrammes UML d’un projet de modélisation sont des vues de ce modèle. Les éléments d’un diagramme de couche font partie du projet de modélisation, même s’ils ne sont pas stockés dans le modèle commun.  
  
     Pour voir le modèle, dans le menu **Architecture** , pointez sur  **Fenêtres**, puis cliquez sur **Explorateur de modèles UML**.  
  
-   Dans certains cas, vous pouvez faire glisser des éléments de l’ **Explorateur de modèles UML** vers un diagramme UML. Certains éléments au sein du même modèle peuvent être utilisés sur plusieurs ou différents diagrammes pour représenter d’autres vues de l’architecture. Par exemple, faites glisser un composant vers un autre diagramme de composant ou vers un diagramme de séquence à utiliser en tant qu’acteur.  
  
-   Visual Studio prend en charge UML 2.1.2. Cette vue d’ensemble décrit uniquement les principales fonctionnalités des diagrammes UML disponibles dans cette version, mais il existe de nombreux ouvrages traitant du langage UML et de son utilisation plus en détail.  
  
 Consultez [créer des modèles pour votre application](../modeling/create-models-for-your-app.md).  
  
###  <a name="PlanningTracking"></a> Planning and Tracking Work  
 Des diagrammes de modélisation Visual Studio sont intégrés à Team Foundation Server pour que vous puissiez planifier, gérer et suivre le travail plus facilement. Les deux équipes utilisent des modèles pour identifier des cas de test et des tâches de développement, et pour estimer leur travail. Lucerne crée des éléments de travail Team Foundation Server et les lie à des éléments de modèle,tels que des cas d’usage ou des composants. Ainsi, les équipes peuvent suivre leur progression et tracer le travail par rapport aux besoins des utilisateurs. Elles peuvent mieux contrôler le maintien de la cohérence des modifications avec ces besoins.  
  
 Au fur et à mesure que le travail avance, les équipes mettent à jour leurs éléments de travail pour prendre en compte le temps dévolu à leurs tâches. Elles surveillent et signalent également l’état de leur travail en utilisant les fonctionnalités Team Foundation Server suivantes :  
  
-   Des *rapports d’avancement* quotidiens qui indiquent si les équipes vont effectuer le travail planifié dans le temps imparti. Les équipes génèrent d’autres rapports similaires à partir de Team Foundation Server pour suivre la progression des bogues.  
  
-   Une *feuille de calcul d’itération* qui utilise Microsoft Excel pour aider les équipes à surveiller et équilibrer la charge de travail entre ses membres. Cette feuille de calcul est liée à Team Foundation Server et fournit le thème de discussion lors des réunions d’avancement régulières.  
  
-   Un *tableau de bord de développement* qui utilise Office Project pour tenir l’équipe informée sur les points importants du projet.  
  
 Consultez :  
  
-   [Effectuer le suivi d’un travail à l’aide de Visual Studio Team Services ou Team Foundation Server](http://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)  
  
-   [Lier des éléments de modèle et des éléments de travail](../modeling/link-model-elements-and-work-items.md)  
  
-   [Graphiques, tableaux de bord et rapports pour Visual Studio ALM](http://msdn.microsoft.com/library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)  
  
-   [Créer votre journal des travaux en souffrance et vos tâches à l'aide de Project](http://msdn.microsoft.com/library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)  
  
###  <a name="TestValidateCheckInCode"></a> Test, validation et archivage du code  
 À mesure que les équipes effectuent chaque tâche, elles vérifient leur code dans la gestion de version Team Foundation et reçoivent des rappels de Team Foundation Server, en cas d’oubli. Avant que Team Foundation Server n’accepte leurs archivages, les équipes exécutent des tests unitaires et la validation de couche pour vérifier le code par rapport à leur cas de test et à la conception. Elles utilisent Team Foundation Server pour exécuter régulièrement des builds, des tests unitaires automatisés et la validation de couche. Ainsi, elles vérifient que le code respecte les critères suivants :  
  
-   Il fonctionne.  
  
-   Il n’empêche pas du code opérationnel existant de fonctionner.  
  
-   Il n’entre pas en conflit avec la conception.  
  
 Dinner Now possède une grande collection de tests automatisés. Lucerne peut réutiliser ces tests, car ils sont presque tous encore applicables. Lucerne peut également s’appuyer sur ces tests et en ajouter de nouveaux pour couvrir les nouvelles fonctionnalités. Les deux sociétés utilisent également Visual Studio pour exécuter des tests manuels.  
  
 Pour s’assurer que le code est conforme à la conception, les équipes configurent leurs builds dans Team Foundation Build pour inclure la validation de couche. En cas de conflit, un rapport détaillé est généré.  
  
 Consultez :  
  
-   [Test de l’application](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)  
  
-   [Valider votre système pendant le développement](../modeling/validate-your-system-during-development.md)  
  
-   [Utiliser la gestion de version](http://go.microsoft.com/fwlink/?LinkID=525605)  
  
-   [Générer l’application](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
##  <a name="UpdatingSystem"></a> Updating the System Using Visualization and Modeling  
 Lucerne et Dinner Now doivent intégrer leurs systèmes de paiement. Les sections suivantes présentent les diagrammes de modélisation dans Visual Studio qui les aident à effectuer cette tâche :  
  
-   [Comprendre les besoins des utilisateurs : diagrammes de cas d’usage](#UnderstandUseCases)  
  
-   [Comprendre le processus d’entreprise : diagrammes d’activités](#UnderstandActivities)  
  
-   [Décrire la Structure du système : diagrammes de composants](#DescribeComponents)  
  
-   [Décrire les Interactions : diagrammes de séquence](#DescribeSequence)  
  
-   [Visualiser le code existant : cartes de code](#VisualizeCode)  
  
-   [Définir un glossaire des types : diagrammes de classes](#DefineClasses)  
  
-   [Décrire l’Architecture logique : diagrammes de couche](#DescribeLayers)  
  
 Consultez :  
  
-   [Créer des modèles pour votre application](../modeling/create-models-for-your-app.md)  
  
-   [Visualiser du code](../modeling/visualize-code.md)  
  
-   [Utiliser des modèles dans votre processus de développement](../modeling/use-models-in-your-development-process.md)  
  
-   [Modéliser les besoins des utilisateurs](../modeling/model-user-requirements.md)  
  
-   [Modéliser l’architecture de votre application](../modeling/model-your-app-s-architecture.md)  
  
###  <a name="UnderstandUseCases"></a> Comprendre les besoins des utilisateurs : diagrammes de cas d’usage  
 Les diagrammes de cas d’usage résument les activités prises en charge par un système et les personnes qui effectuent ces activités. Lucerne utilise un diagramme de cas d’usage pour mieux comprendre le système Dinner Now :  
  
-   Les clients créent des commandes.  
  
-   Les restaurants reçoivent les commandes.  
  
-   La passerelle de traitement du paiement externe, utilisée par le système de paiement de Dinner Now pour valider les paiements, est en dehors de la portée du site web.  
  
 Le diagramme illustre aussi la manière dont certains cas d’usage principaux se scindent en plusieurs cas d’usage plus petits. Lucerne veut utiliser son propre système de paiement. La société met en surbrillance le cas d’usage correspondant au traitement du paiement avec une autre couleur pour indiquer qu’il nécessite des modifications :  
  
 ![Mise en surbrillance de traiter le paiement dans un diagramme de cas d’utilisation](../modeling/media/uml-processpay.png "UML_ProcessPay")  
  
 **Mise en surbrillance de traiter le paiement dans le diagramme de cas d’utilisation**  
  
 Si le délai de développement est court, l’équipe peut envisager de permettre aux clients de payer directement les restaurants. Pour cela, elle devra remplacer le cas d’usage Traiter le paiement par un cas d’usage situé au-delà des limites du système Dinner Now. Elle devra ensuite lier le client directement au restaurant, en indiquant que Dinner Now se contentera de traiter les commandes :  
  
 ![Redéfinition sur le diagramme de cas d’usage payer le Restaurant](../modeling/media/uml-payrestaurant.png "UML_PayRestaurant")  
  
 **Redéfinition payer le Restaurant sur le diagramme de cas d’utilisation**  
  
 Consultez :  
  
-   [Informations de référence sur les diagrammes de cas d’usage UML](../modeling/uml-use-case-diagrams-reference.md)  
  
-   [Diagrammes de cas d’usage UML : recommandations](../modeling/uml-use-case-diagrams-guidelines.md)  
  
#### <a name="drawing-a-use-case-diagram"></a>Dessin d’un diagramme de cas d’usage  
 Un diagramme de cas d’usage comporte les principales fonctionnalités suivantes :  
  
-   Les*acteurs* représentent les rôles joués par les personnes, les organisations, les ordinateurs ou les systèmes logiciels. Par exemple, Client, Restaurant et Système de paiement de Dinner Now sont des acteurs.  
  
-   Les*cas d’usage* représentent les interactions entre les acteurs et le système en cours de développement.  Ils peuvent représenter tout niveau d’interaction depuis un clic de souris ou un message unique jusqu’à une transaction qui se déroule sur plusieurs jours.  
  
-   Les*associations* lient les acteurs aux cas d’usage.  
  
-   Un cas d’usage plus large peut *inclure* plusieurs cas d’usage plus petits (par exemple, Créer une commande inclut Sélectionner un restaurant). Vous pouvez *étendre* un cas d’usage, ce qui ajoute des objectifs et des étapes au cas d’usage étendu, pour indiquer qu’il se produit uniquement sous certaines conditions. Les cas d’usage peuvent également hériter les uns des autres.  
  
-   Un *sous-système* représente le système logiciel en cours de développement ou l’un de ses composants. Il s’agit d’une grande « boîte » qui contient des cas d’usage. Un diagramme de cas d’usage clarifie ce qui est à l’intérieur ou à l’extérieur des limites du sous-système. Pour indiquer que l’utilisateur doit remplir certains objectifs d’une autre manière, dessinez ces cas d’usage en dehors des limites du sous-système.  
  
-   Les*artefacts* lient des éléments d’un diagramme à d’autres diagrammes ou documents.  
  
 Consultez :  
  
-   [Informations de référence sur les diagrammes de cas d’usage UML](../modeling/uml-use-case-diagrams-reference.md)  
  
-   [Diagrammes de cas d’usage UML : recommandations](../modeling/uml-use-case-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-use-case-diagrams"></a>Résumé : atouts des diagrammes de cas d’usage  
 Les diagrammes de cas d’usage vous aident à visualiser :  
  
-   les activités qu’un système prend ou ne prend pas en charge ;  
  
-   les personnes et les systèmes externes qui effectuent ces activités ;  
  
-   les principaux composants du système qui prennent en charge chaque activité, que vous pouvez représenter sous forme de sous-systèmes imbriqués dans le système parent ;  
  
-   la manière dont un cas d’usage peut se scinder en cas d’usage plus petits ou en variantes.  
  
#### <a name="relationship-to-other-diagrams"></a>Relation aux autres diagrammes  
  
|**Diagramme**|**Éléments décrits**|  
|-----------------|-------------------|  
|Diagramme d'activités|Flux des étapes dans un cas d’usage et personnes qui exécutent ces étapes dans ce cas d’usage.<br /><br /> Les noms des cas d’usage reflètent souvent les étapes incluses dans un diagramme d’activités. Les diagrammes d’activités prennent en charge des éléments tels que les décisions, les fusions, les entrées et sorties, les flux simultanés, etc.<br /><br /> Consultez :<br /><br /> -   [Diagrammes d’activités UML : référence](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagrammes d’activités UML : indications](../modeling/uml-activity-diagrams-guidelines.md)|  
|Diagramme de séquence|Séquence d’interactions entre les participants dans un cas d’usage.<br /><br /> Consultez :<br /><br /> -   [Diagrammes de séquence UML : référence](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagrammes de séquence UML : indications](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Diagramme de classes (UML)|Entités ou types qui participent au cas d’usage.<br /><br /> Consultez :<br /><br /> -   [Diagrammes de classes UML : référence](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagrammes de classes UML : indications](../modeling/uml-class-diagrams-guidelines.md)|  
  
###  <a name="UnderstandActivities"></a> Comprendre le processus d’entreprise : diagrammes d’activités  
 Les diagrammes d’activités décrivent le flux des étapes dans un processus d’entreprise et offrent un moyen simple de communiquer le flux de travail. Un projet de développement peut comporter plusieurs diagrammes d’activités. En règle générale, une activité englobe toutes les actions issues d’une seule action externe, comme la commande d’un repas, la mise à jour d’un menu ou l’ajout d’un nouveau restaurant. Une activité peut également décrire les détails d’une action complexe.  
  
 Lucerne met à jour le diagramme d’activités suivant pour montrer que c’est elle qui traite le paiement et paie le restaurant. Elle remplace le système de paiement de Dinner Now par celui de Lucerne (mis en surbrillance ci-dessous) :  
  
 ![Système de paiement Lucerne sur le diagramme d’activités](../modeling/media/uml-lucerne.png "UML_Lucerne")  
  
 **En remplaçant le système Dinner Now paiement sur le diagramme d’activités**  
  
 Le diagramme mis à jour permet à Lucerne et Dinner Now de mieux visualiser l’endroit où le système de paiement de Lucerne s’intègre au processus d’entreprise. Dans cette version, les commentaires sont utilisés pour identifier les rôles qui effectuent les étapes. Des lignes sont utilisées pour créer des *couloirs*, qui permettent d’organiser les étapes par rôle.  
  
 Les équipes peuvent également envisager un autre scénario où c’est plutôt le client qui paye le restaurant après la livraison de la commande. Ainsi, des spécifications différentes seraient créées pour le système logiciel.  
  
 Avant, Dinner Now dessinait ces diagrammes sur un tableau blanc ou dans PowerPoint. Maintenant, elle utilise également Visual Studio pour dessiner ces diagrammes pour que les deux équipes puissent capturer, comprendre et gérer les détails.  
  
 Consultez :  
  
-   [Informations de référence sur les diagrammes d’activités UML](../modeling/uml-activity-diagrams-reference.md)  
  
-   [Diagrammes d’activités UML : conseils](../modeling/uml-activity-diagrams-guidelines.md)  
  
#### <a name="drawing-an-activity-diagram"></a>Dessin d’un diagramme d’activités  
 Un diagramme d’activités comporte les principales fonctionnalités suivantes :  
  
-   Un *nœud initial* qui indique la première action de l’activité.  
  
     Le diagramme doit toujours comporter un de ces nœuds.  
  
-   Des*actions* qui décrivent les étapes au cours desquelles l’utilisateur ou le logiciel effectuent une tâche.  
  
-   Des*flux de contrôle* qui montrent le flux entre les actions.  
  
-   Des*nœuds de décision* qui représentent les branches conditionnelles dans le flux.  
  
-   Des*nœuds de bifurcation* qui divisent les flux uniques en flux simultanés.  
  
-   Des*nœuds finaux de l’activité* qui montrent la fin de l’activité.  
  
     Ces nœuds sont facultatifs, mais il est préférable de les inclure dans le diagramme pour indiquer la fin de l’activité.  
  
 Consultez :  
  
-   [Informations de référence sur les diagrammes d’activités UML](../modeling/uml-activity-diagrams-reference.md)  
  
-   [Diagrammes d’activités UML : conseils](../modeling/uml-activity-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-activity-diagrams"></a>Résumé : atouts des diagrammes d’activités  
 Les diagrammes d’activités vous aident à visualiser et décrire le flux de contrôle et d’informations entre les actions d’une entreprise, d’un système ou d’un programme. Il s’agit d’un moyen simple et pratique de décrire le flux de travail pour communiquer avec d’autres personnes.  
  
#### <a name="relationship-to-other-diagrams"></a>Relation aux autres diagrammes  
  
|**Diagramme**|**Description**|  
|-----------------|---------------------|  
|Diagramme de cas d'usage|Résume les activités que chaque acteur effectue.<br /><br /> Consultez :<br /><br /> -   [Diagrammes de cas d’usage UML : référence](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagrammes de cas d’usage UML : indications](../modeling/uml-use-case-diagrams-guidelines.md)|  
|Diagramme de composant|Permet de visualiser le système comme une collection de parties réutilisables qui fournissent ou consomment un comportement via un ensemble bien défini d’interfaces.<br /><br /> Consultez :<br /><br /> -   [Diagrammes de composants UML : référence](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagrammes de composants UML : indications](../modeling/uml-component-diagrams-guidelines.md)|  
  
###  <a name="DescribeComponents"></a> Décrire la Structure du système : diagrammes de composants  
 Les diagrammes de composant décrivent un système sous la forme d’une collection de parties séparables qui fournissent ou consomment un comportement via un ensemble bien défini d’interfaces. L’échelle et la manière de connecter ces parties sont entièrement libres.  
  
 Pour aider Lucerne et Dinner Now à visualiser et décrire les composants du système et leurs interfaces, les diagrammes de composant suivants sont créés :  
  
 ![Composants externes dans le système de paiement](../modeling/media/uml-extdnpayment.png "UML_ExtDNPayment")  
  
 **Composants du système de paiement Dinner Now**  
  
 Ce diagramme montre les différents types de composants et leurs *dépendances*. Par exemple, le site web de Dinner Now et le système de paiement de Lucerne requièrent que la passerelle de traitement du paiement externe valide les paiements. Les flèches entre les composants représentent les dépendances indiquant quels composants nécessitent les fonctionnalités d’autres composants.  
  
 Pour utiliser le système de paiement de Lucerne, le site web de Dinner Now doit être mis à jour pour utiliser les interfaces PaymentApproval et PayableInsertion du système de paiement de Lucerne.  
  
 Le diagramme suivant montre une configuration spécifique des composants pour le site web de Dinner Now. Cette configuration indique que chaque instance du site web se compose de quatre *parties*:  
  
-   CustomerProcessing  
  
-   OrderProcessing  
  
-   ReviewProcessing  
  
-   PaymentProcessing  
  
 Ces parties sont des instances des types de composants spécifiés et sont connectées comme suit :  
  
 ![Composants à l’intérieur du site Web de Dinner Now](../modeling/media/uml-dinnernow.png "UML_DinnerNow")  
  
 **Site Web de composants à l’intérieur de la Dinner Now**  
  
 Le site web de Dinner Now délègue son comportement à ces parties, qui gèrent les fonctions du site web. Les flèches entre le composant parent et ses composants membres représentent les *délégations* qui indiquent quelles parties gèrent les messages que le parent reçoit ou envoie via ses interfaces.  
  
 Dans cette configuration, le composant PaymentProcessing traite les paiements des clients. Il doit donc être mis à jour pour s’intégrer au système de paiement de Lucerne. Dans d’autres scénarios, plusieurs instances d’un type de composant peuvent exister dans le même composant parent.  
  
 Consultez :  
  
-   [Informations de référence sur les diagrammes de composants UML](../modeling/uml-component-diagrams-reference.md)  
  
-   [Diagrammes de composants UML : recommandations](../modeling/uml-component-diagrams-guidelines.md)  
  
#### <a name="drawing-a-component-diagram"></a>Dessin d’un diagramme de composant  
 Un diagramme de composant comporte les principales fonctionnalités suivantes :  
  
-   Des*composants* qui représentent des parties séparables des fonctionnalités du système.  
  
-   Des*ports d’interface fournie* qui représentent des groupes de messages ou d’appels que les composants implémentent et qui servent à d’autres composants ou systèmes externes.  
  
-   Des*ports d’interface requise* qui représentent des groupes de messages ou d’appels que les composants envoient à d’autres composants ou systèmes externes. Ce type de port décrit les opérations qu’un composant attend au minimum des autres composants ou systèmes externes.  
  
-   Les*parties* sont membres de composants et sont généralement des instances d’autres composants. Une partie est un fragment de la conception interne du composant parent.  
  
-   Des*dépendances* qui indiquent que les composants nécessitent les fonctionnalités d’autres composants.  
  
-   Des*délégations* qui indiquent que des parties d’un composant gèrent les messages envoyés ou reçus par le composant parent.  
  
 Consultez :  
  
-   [Informations de référence sur les diagrammes de composants UML](../modeling/uml-component-diagrams-reference.md)  
  
-   [Diagrammes de composants UML : recommandations](../modeling/uml-component-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-component-diagrams"></a>Résumé : atouts des diagrammes de composant  
 Les diagrammes de composant vous aident à visualiser :  
  
-   le système sous la forme d’une collection de parties séparables, indépendamment de leur langage ou mode d’implémentation ;  
  
-   les composants avec des interfaces bien définies, ce qui facilite la compréhension et la mise à jour de la conception quand les besoins changent.  
  
#### <a name="relationship-to-other-diagrams"></a>Relation aux autres diagrammes  
  
|**Diagramme**|**Description**|  
|-----------------|---------------------|  
|Carte de code|Visualisez l'organisation et les relations dans le code existant.<br /><br /> Pour identifier les candidats pour des composants, créez une carte de code et regroupez les éléments selon leur fonction dans le système.<br /><br /> Consultez :<br /><br /> -   [Mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md)|  
|Diagramme de séquence|Permet de visualiser la séquence d’interactions entre les composants ou les parties à l’intérieur d’un composant.<br /><br /> Pour créer une ligne de vie dans un diagramme de séquence à partir d’un composant, cliquez avec le bouton droit sur le composant, puis cliquez sur **Créer la ligne de vie**.<br /><br /> Consultez :<br /><br /> -   [Diagrammes de séquence UML : référence](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagrammes de séquence UML : indications](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Diagramme de classes (UML)|Permet de définir les interfaces sur les ports fournis ou requis, ainsi que les classes qui implémentent la fonctionnalité des composants.<br /><br /> Consultez :<br /><br /> -   [Diagrammes de classes UML : référence](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagrammes de classes UML : indications](../modeling/uml-class-diagrams-guidelines.md)|  
|Diagramme de couche|Décrit l’architecture logique du système relative aux composants. Utilisez la validation de couche pour vous assurer que le code reste cohérent avec la conception.<br /><br /> Consultez :<br /><br /> -   [Créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagrammes de couche : référence](../modeling/layer-diagrams-reference.md)<br />-   [Diagrammes de couche : instructions](../modeling/layer-diagrams-guidelines.md)<br />-   [Valider du code avec des diagrammes de couche](../modeling/validate-code-with-layer-diagrams.md)|  
|Diagramme d'activités|Permet de visualiser le traitement interne que les composants effectuent en réponse aux messages entrants.<br /><br /> Consultez :<br /><br /> -   [Diagrammes d’activités UML : référence](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagrammes d’activités UML : indications](../modeling/uml-activity-diagrams-guidelines.md)|  
  
###  <a name="VisualizeCode"></a> Visualiser le code existant : cartes de code  
 Les cartes de code montrent l’organisation et les relations actuelles dans le code. Les éléments sont représentés par des *nœuds* dans la carte et les relations sont représentées par des *liens*. Les cartes de code peuvent vous aider à effectuer les types de tâches suivants :  
  
-   Explorer du code méconnu.  
  
-   Comprendre où et comment une modification suggérée peut affecter du code existant.  
  
-   Identifier des zones de complexité, des couches naturelles ou des modèles, ou d’autres zones à améliorer.  
  
 Par exemple, Dinner Now doit estimer le coût de la mise à jour du composant PaymentProcessing. Ce coût dépend en partie des répercussions de cette modification sur les autres parties du système. Pour mieux déterminer ce coût, l’un des développeurs de Dinner Now génère des cartes de code à partir du code existant et ajuste la portée pour se concentrer sur les zones éventuellement concernées par la modification.  
  
 La carte suivante montre les dépendances entre la classe PaymentProcessing et d’autres parties du système Dinner Now, qui sont mises en surbrillance :  
  
 ![Graphique de dépendance pour le système de paiement de Dinner Now](../modeling/media/dep-dnpayment.png "Dep_DNPayment")  
  
 **Carte de code du système de paiement de Dinner Now**  
  
 Le développeur explore la carte en développant la classe PaymentProcessing et en sélectionnant ses membres pour voir les zones éventuellement affectées :  
  
 ![Méthodes dans PaymentProcessing et dépendances](../modeling/media/depgraph-expandeddn.png "DepGraph_ExpandedDN")  
  
 **Méthodes dans la classe PaymentProcessing et leurs dépendances**  
  
 L’équipe génère la carte suivante pour le système de paiement de Lucerne pour inspecter ses classes, méthodes et dépendances. Elle constate que le système Lucerne risque aussi de devoir être modifié pour interagir avec les autres parties de Dinner Now :  
  
 ![Graphique de dépendance pour le système de paiement de Lucerne](../modeling/media/depgraph-lucernepay.png "DepGraph_LucernePay")  
  
 **Carte de code pour le système de paiement de Lucerne**  
  
 Les deux équipes travaillent ensemble pour déterminer les modifications requises pour intégrer les deux systèmes. Elles décident de refactoriser une partie du code pour faciliter sa mise à jour. La classe PaymentApprover est déplacée vers l’espace de noms DinnerNow.Business et nécessite quelques méthodes nouvelles. Les classes Dinner Now qui gèrent les transactions ont leur propre espace de noms. Les équipes créent et utilisent des éléments de travail pour planifier, organiser et suivre leur travail. Elles lient les éléments de travail à des éléments de modèle quand cela s’avère utile.  
  
 Après avoir réorganisé le code, les équipes génèrent une nouvelle carte de code pour voir la structure et les relations mises à jour :  
  
 ![Graphique de dépendance avec code réorganisé](../modeling/media/depgraph-integrated.png "DepGraph_Integrated")  
  
 **Carte de code après la réorganisation du code**  
  
 Cette carte montre que la classe PaymentApprover se trouve maintenant dans l’espace de noms DinnerNow.Business et qu’elle comporte de nouvelles méthodes. Les classes de transaction Dinner Now ont maintenant leur propre espace de noms PaymentSystem, ce qui facilitera l’utilisation ultérieure de ce code.  
  
#### <a name="creating-a-code-map"></a>Création d’une carte de code  
  
-   Pour obtenir un aperçu rapide du code source, générez une carte de code en procédant comme suit :  
  
     Dans le menu **Architecture** , cliquez sur **Générer une carte du code pour la solution**.  
  
     Pour obtenir un aperçu rapide du code compilé, créez une carte de code vide, puis faites glisser des fichiers d’assembly ou des fichiers binaires vers la surface de la carte.  
  
-   Pour explorer du code spécifique ou des éléments de solution, utilisez l’Explorateur de solutions pour sélectionner les éléments et les relations que vous voulez visualiser. Vous pouvez ensuite générer une nouvelle carte ou ajouter les éléments sélectionnés à une carte existante. Consultez [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).  
  
-   Pour explorer la carte plus facilement, réorganisez la disposition pour qu’elle corresponde aux types de tâches à effectuer.  
  
     Par exemple, pour visualiser les couches dans le code, sélectionnez une disposition en arborescence. Consultez [Parcourir et réorganiser des cartes de code](../modeling/browse-and-rearrange-code-maps.md).  
  
#### <a name="summary-strengths-of-code-maps"></a>Résumé : atouts des cartes de code  
 Les cartes de code vous aident à :  
  
-   comprendre l’organisation et les relations du code existant ;  
  
-   identifier les zones qui peuvent être affectées par une modification proposée ;  
  
-   identifier des zones de complexité, des modèles, des couches ou d’autres zones à améliorer pour rendre le code plus facile à tenir à jour, modifier et réutiliser.  
  
#### <a name="relationship-to-other-diagrams"></a>Relation aux autres diagrammes  
  
|**Diagramme**|**Éléments décrits**|  
|-----------------|-------------------|  
|Diagramme de couche|L’architecture logique du système. Utilisez la validation de couche pour vous assurer que le code reste cohérent avec la conception.<br /><br /> Pour mieux identifier les couches existantes ou les couches prévues, créez une carte de code et regroupez les éléments connexes. Pour créer un diagramme de couche, consultez :<br /><br /> -   [Créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagrammes de couche : instructions](../modeling/layer-diagrams-guidelines.md)|  
|Diagramme de composant|Les composants, leurs interfaces et leurs relations.<br /><br /> Pour mieux identifier les composants, créez une carte de code et regroupez les éléments selon leur fonction dans le système.<br /><br /> Consultez :<br /><br /> -   [Diagrammes de composants UML : référence](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagrammes de composants UML : indications](../modeling/uml-component-diagrams-guidelines.md)|  
|Diagramme de classes (UML)|Les classes, leurs attributs et opérations, ainsi que leur relations.<br /><br /> Pour mieux identifier ces éléments, créez un diagramme de classes UML qui les représente.<br /><br /> Consultez :<br /><br /> -   [Diagrammes de classes UML : référence](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagrammes de classes UML : indications](../modeling/uml-class-diagrams-guidelines.md)|  
|Diagramme de classes (basé sur le code)|Classes existantes dans le code d’un projet spécifique.<br /><br /> Pour visualiser et modifier une classe existante dans le code, utilisez le Concepteur de classes.<br /><br /> Consultez [How to: Add Class Diagrams to Projects (Class Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|  
  
###  <a name="DescribeSequence"></a> Décrire les Interactions : diagrammes de séquence  
 Les diagrammes de séquence décrivent une série d’interactions entre les parties d’un système. Les parties peuvent être de n’importe quelle échelle. Par exemple, il peut s’agir d’objets individuels dans un programme ou de grands sous-systèmes ou acteurs externes. Les interactions peuvent être de n’importe quelle échelle et de n’importe quel type. Par exemple, les interactions peuvent être à l’échelle de messages individuels ou de transactions étendues, et correspondre à des appels de fonction ou à des messages de service web.  
  
 Pour permettre à Lucerne et Dinner Now de décrire et d’étudier les étapes du cas d’usage Traiter le paiement, les sociétés créent le diagramme de séquence suivant à partir du diagramme de composant. Les lignes de vie représentent le composant Site web de Dinner Now et ses parties. Les messages qui apparaissent entre les lignes de vie suivent les connexions sur les diagrammes de composant :  
  
 ![Cas d’usage de diagramme de séquence pour traiter le paiement](../modeling/media/umlsequence-processpayment.png "UMLSequence_ProcessPayment")  
  
 **Cas d’usage de diagramme de séquence pour le traiter le paiement**  
  
 Le diagramme de séquence montre que, quand le client crée une commande, le site web de Dinner Now appelle ProcessOrder sur une instance du composant OrderProcessing. Ensuite, OrderProcessing appelle ProcessPayment sur PaymentProcessing. Ce processus se poursuit jusqu’à ce que la passerelle de traitement du paiement externe valide le paiement. C’est uniquement à ce moment que le contrôle est renvoyé au site web de Dinner Now.  
  
 Lucerne doit estimer le coût de la mise à jour de son système de paiement pour pouvoir l’intégrer au système Dinner Now. Pour mieux déterminer ce coût, la société peut également créer des cartes de code pour visualiser le code affecté.  
  
 Consultez :  
  
-   [Informations de référence sur les diagrammes de séquence UML](../modeling/uml-sequence-diagrams-reference.md)  
  
-   [Diagrammes de séquence UML : recommandations](../modeling/uml-sequence-diagrams-guidelines.md)  
  
-   [Mapper les dépendances à travers vos solutions](../modeling/map-dependencies-across-your-solutions.md)  
  
#### <a name="drawing-a-sequence-diagram"></a>Dessin d’un diagramme de séquence  
 Un diagramme de séquence comporte les principales fonctionnalités suivantes :  
  
-   Les *lignes de vie* verticales représentent les acteurs ou les instances des objets logiciels.  
  
     Pour ajouter un symbole d’acteur, qui indique qu’un participant est en dehors du système en cours de développement, cliquez sur la ligne de vie. Dans la fenêtre **Propriétés** , affectez à **Acteur** la valeur **True**. Si la fenêtre **Propriétés** n’est pas ouverte, appuyez sur **F4**.  
  
-   Les *messages* horizontaux représentent des appels de méthode, des messages de service web ou d’autres communications. Les*occurrences d’exécution* sont des rectangles grisés verticaux qui apparaissent sur les lignes de vie et qui représentent les périodes pendant lesquelles les objets de destination traitent les appels.  
  
-   Pendant un *synchrone* message, l’objet expéditeur attend du contrôle <\<retourner >> comme dans un appel de fonction normal. Pendant un message *asynchrone* , l’expéditeur peut continuer immédiatement.  
  
-   Utilisez <\<créer >> messages pour indiquer la construction d’objets par d’autres objets. Cela doit être le premier message envoyé à l’objet.  
  
 Consultez :  
  
-   [Informations de référence sur les diagrammes de séquence UML](../modeling/uml-sequence-diagrams-reference.md)  
  
-   [Diagrammes de séquence UML : recommandations](../modeling/uml-sequence-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-sequence-diagrams"></a>Résumé : atouts des diagrammes de séquence  
 Les diagrammes de séquence vous aident à visualiser :  
  
-   le flux de contrôle qui effectue le transfert entre les acteurs ou les objets pendant l’exécution d’un cas d’usage ;  
  
-   l’implémentation d’un appel de méthode ou d’un message.  
  
#### <a name="relationship-to-other-diagrams"></a>Relation aux autres diagrammes  
  
|**Diagramme**|**Description**|  
|-----------------|---------------------|  
|Diagramme de classes (UML)|Permet de définir les classes que les lignes de vie représentent, et les paramètres et valeurs de retour qui sont utilisés dans les messages envoyés entre les lignes de vie.<br /><br /> Pour créer une classe à partir d’une ligne de vie, cliquez avec le bouton droit sur la ligne de vie, puis cliquez sur **Créer la classe** ou **Créer l’interface**. Pour créer une ligne de vie à partir d’un type sur un diagramme de classes, cliquez avec le bouton droit sur le type, puis cliquez sur **Créer la ligne de vie**.<br /><br /> Consultez :<br /><br /> -   [Diagrammes de classes UML : référence](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagrammes de classes UML : indications](../modeling/uml-class-diagrams-guidelines.md)|  
|Diagramme de composant|Décrit les composants que les lignes de vie représentent, et les interfaces qui fournissent et consomment le comportement représenté par les messages.<br /><br /> Pour créer une ligne de vie à partir d’un diagramme de composant, cliquez avec le bouton droit sur le composant, puis cliquez sur **Créer la ligne de vie**.<br /><br /> Consultez :<br /><br /> -   [Diagrammes de composants UML : référence](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagrammes de composants UML : indications](../modeling/uml-component-diagrams-guidelines.md)|  
|Diagramme de cas d'usage|Résume les interactions entre les utilisateurs et les composants dans un diagramme de séquence sous forme de cas d’usage, lequel représente l’objectif d’un utilisateur.<br /><br /> Consultez :<br /><br /> -   [Diagrammes de cas d’usage UML : référence](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagrammes de cas d’usage UML : indications](../modeling/uml-use-case-diagrams-guidelines.md)|  
  
###  <a name="DefineClasses"></a> Définir un glossaire des types : diagrammes de classes  
 Les diagrammes de classes définissent les entités, les termes ou les concepts qui participent au système, et leurs relations. Par exemple, vous pouvez utiliser ces diagrammes pendant le développement pour décrire les attributs et les opérations de chaque classe, indépendamment de leur langage ou mode d’implémentation.  
  
 Pour permettre à Lucerne de décrire et d’étudier les entités qui participent au cas d’usage Traiter le paiement, le diagramme suivant est dessiné :  
  
 ![Entités traiter le paiement sur le diagramme de classes](../modeling/media/uml-payentities.png "UML_PayEntities")  
  
 **Entités Traiter le paiement dans un diagramme de classes**  
  
 Ce diagramme montre qu’un client peut effectuer plusieurs commandes et utiliser différents modes de paiement pour les commandes. BankAccount et CreditCard héritent de Payment.  
  
 Pendant le développement, Lucerne utilise le diagramme de classes suivant pour décrire et étudier les détails de chaque classe :  
  
 ![Traiter les détails de l’entité paiement sur un diagramme de classes](../modeling/media/uml-payment.png "UML_Payment")  
  
 **Détails de l’entité Traiter le paiement dans le diagramme de classes**  
  
 Consultez :  
  
-   [Informations de référence sur les diagrammes de classes UML](../modeling/uml-class-diagrams-reference.md)  
  
-   [Diagrammes de classes UML : recommandations](../modeling/uml-class-diagrams-guidelines.md)  
  
#### <a name="drawing-a-class-diagram"></a>Dessin d’un diagramme de classes  
 Un diagramme de classes comporte les principales fonctionnalités suivantes :  
  
-   Des types, tels que des classes, des interfaces et des énumérations :  
  
    -   Une *classe* est la définition d’objets qui partagent des caractéristiques structurelles ou comportementales spécifiques.  
  
    -   Une *interface* définit une partie du comportement extérieurement visible d’un objet.  
  
    -   Une *énumération* est un classifieur qui contient une liste de valeurs littérales.  
  
-   Les*attributs* sont des valeurs d’un type donné qui décrivent chaque instance d’un *classifieur*. Un classifieur est un nom générique attribué aux types, aux composants, aux cas d’usage et même aux acteurs.  
  
-   Les*opérations* sont des méthodes ou des fonctions que les instances d’un classifieur peuvent exécuter.  
  
-   Une *association* indique une sorte de relation entre deux classifieurs.  
  
    -   Une *agrégation* est une association qui indique une propriété partagée entre des classifieurs.  
  
    -   Une *composition* est une association qui indique une relation ensemble à partie entre des classifieurs.  
  
     Pour afficher les agrégations ou les compositions, définissez la propriété **Aggregation** sur une association. La valeur**Shared** et la valeur **Composite** affichent les agrégations et les compositions, respectivement.  
  
-   Une *dépendance* indique que la modification de la définition d’un classifieur peut modifier la définition d’un autre classifieur.  
  
-   Une *généralisation* indique qu’un classifieur spécifique hérite une partie de sa définition d’un classifieur général. Une *réalisation* indique qu’une classe implémente les opérations et attributs fournis par une interface.  
  
     Pour créer ces relations, utilisez l’outil **Héritage** . Sinon, une réalisation peut être représentée sous forme d’interface *lollipop*.  
  
-   Les*packages* sont des groupes de classifieurs, d’associations, de lignes de vie, de composants et d’autres packages. Les relations d’*importation* indiquent qu’un package inclut toutes les définitions d’un autre package.  
  
 Pour commencer l’exploration et l’examen des classes existantes, vous pouvez utiliser le Concepteur de classes pour créer des diagrammes de classes à partir du code.  
  
 Consultez :  
  
-   [Informations de référence sur les diagrammes de classes UML](../modeling/uml-class-diagrams-reference.md)  
  
-   [Diagrammes de classes UML : recommandations](../modeling/uml-class-diagrams-guidelines.md)  
  
-   [Guide pratique pour ajouter des diagrammes de classes aux projets (Concepteur de classes)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
#### <a name="summary-strengths-of-class-diagrams"></a>Résumé : atouts des diagrammes de classes  
 Les diagrammes de classes vous permettent de définir :  
  
-   Un glossaire commun des termes à utiliser pour étudier les besoins des utilisateurs et les entités qui participent au système. Consultez [modéliser les besoins des utilisateurs](../modeling/model-user-requirements.md).  
  
-   Les types qui sont utilisés par des parties du système, notamment les composants, indépendamment de leur implémentation. Consultez [modéliser l’architecture de votre application](../modeling/model-your-app-s-architecture.md).  
  
-   Les relations, telles que les dépendances, entre les types. Par exemple, vous pouvez montrer qu’un type peut être associé à plusieurs instances d’un autre type.  
  
#### <a name="relationship-to-other-diagrams"></a>Relation aux autres diagrammes  
  
|**Diagramme**|**Description**|  
|-----------------|---------------------|  
|Diagramme de cas d'usage|Définit les types qui sont utilisés pour décrire les objectifs et les étapes des cas d’usage.<br /><br /> Consultez :<br /><br /> -   [Diagrammes de cas d’usage UML : référence](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagrammes de cas d’usage UML : indications](../modeling/uml-use-case-diagrams-guidelines.md)|  
|Diagramme d'activités|Définit les types de données qui transitent via des nœuds d’objet, des broches d’entrée, des broches de sortie et des nœuds de paramètre d’activité.<br /><br /> Consultez :<br /><br /> -   [Diagrammes d’activités UML : référence](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagrammes d’activités UML : indications](../modeling/uml-activity-diagrams-guidelines.md)|  
|Diagramme de composant|Décrit les composants, leurs interfaces et leurs relations. Une classe peut également décrire un composant complet.<br /><br /> Consultez :<br /><br /> -   [Diagrammes de composants UML : référence](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagrammes de composants UML : indications](../modeling/uml-component-diagrams-guidelines.md)|  
|Diagramme de couche|Définit l’architecture logique du système relative aux classes.<br /><br /> Utilisez la validation de couche pour vous assurer que le code reste cohérent avec la conception.<br /><br /> Consultez :<br /><br /> -   [Créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagrammes de couche : référence](../modeling/layer-diagrams-reference.md)<br />-   [Diagrammes de couche : instructions](../modeling/layer-diagrams-guidelines.md)<br />-   [Valider du code avec des diagrammes de couche](../modeling/validate-code-with-layer-diagrams.md)|  
|Diagramme de séquence|Définit les types de lignes de vie et les opérations, les paramètres et les valeurs de retour de tous les messages qu’une ligne de vie peut recevoir.<br /><br /> Pour créer une ligne de vie à partir d’un type sur un diagramme de classes, cliquez avec le bouton droit sur le type, puis cliquez sur **Créer la ligne de vie**.<br /><br /> Consultez :<br /><br /> -   [Diagrammes de séquence UML : référence](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagrammes de séquence UML : indications](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Carte de code|Permet de visualiser l’organisation et les relations dans le code existant.<br /><br /> Pour identifier les classes, leurs relations et leurs méthodes, créez une carte de code qui montre ces éléments.<br /><br /> Consultez :<br /><br /> -   [Mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md)|  
  
###  <a name="DescribeLayers"></a> Décrire l’Architecture logique : diagrammes de couche  
 Les diagrammes de couche décrivent l’architecture logique d’un système en organisant les artefacts de votre solution en groupes abstraits ou *couches*. Les artefacts peuvent correspondre à beaucoup de choses, notamment des espaces de noms, des projets, des classes, des méthodes, etc. Les couches représentent et décrivent les rôles ou les tâches que les artefacts exécutent dans le système. Vous pouvez également inclure la validation de couche dans votre build et des opérations d’archivage pour vous assurer que le code reste cohérent avec sa conception.  
  
 Pour que le code reste cohérent avec la conception, Dinner Now et Lucerne utilisent le diagramme de couche suivant pour valider le code à mesure qu’il évolue :  
  
 ![Diagramme de couche du système de paiement intégré](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **Diagramme de couche de Dinner Now intégré à Lucerne**  
  
 Les couches de ce diagramme sont liées aux artefacts de solution Dinner Now et Lucerne correspondants. Par exemple, la couche Business est liée à l’espace de noms DinnerNow.Business et à ses membres, qui incluent maintenant la classe PaymentApprover. La couche Resource Access est liée à l’espace de noms DinnerNow.Data. Les flèches, ou *dépendances*, indiquent que seule la couche Business peut utiliser la fonctionnalité dans la couche Resource Access. Quand les équipes mettent à jour leur code, une validation de couche est exécutée régulièrement pour détecter les conflits dès qu’ils se produisent et permettre aux équipes de les résoudre rapidement.  
  
 Les équipes travaillent ensemble pour intégrer et tester progressivement les deux systèmes. Elles vérifient d’abord que PaymentApprover et le reste du système Dinner Now fonctionnent correctement ensemble avant de s’occuper du code PaymentProcessing.  
  
 La carte de code suivante montre les nouveaux appels entre Dinner Now et PaymentApprover :  
  
 ![Graphique de dépendance mis à jour avec système intégré](../modeling/media/depgraph-intsystem.png "DepGraph_IntSystem")  
  
 **Carte de code avec les appels de méthode mis à jour**  
  
 Après avoir vérifié que le système fonctionne comme prévu, Dinner Now commente le code PaymentProcessing. Les rapports de validation de couche sont satisfaisants et la carte de code obtenue indique qu’il n’existe plus aucune dépendance PaymentProcessing :  
  
 ![Graphique de dépendance sans PaymentProcessing](../modeling/media/depgraph-nomore.png "DepGraph_NoMore")  
  
 **Carte de code sans PaymentProcessing**  
  
#### <a name="drawing-a-layer-diagram"></a>Dessin d’un diagramme de couche  
 Un diagramme de couche comporte les principales fonctionnalités suivantes :  
  
-   Des*couches* décrivent des groupes logiques d’artefacts.  
  
-   Un *lien* est une association entre une couche et un artefact.  
  
     Pour créer des couches à partir d’artefacts, faites glisser des éléments depuis l’Explorateur de solutions, des cartes de code, de l’affichage de classes ou de l’Explorateur d’objets. Pour dessiner de nouvelles couches et les lier aux artefacts, utilisez la boîte à outils, ou cliquez avec le bouton droit sur la surface du diagramme pour créer les couches, puis faites glisser des éléments vers ces couches.  
  
     Le nombre indiqué sur une couche représente le nombre d’artefacts liés à cette couche. Ces artefacts peuvent correspondre à des espaces de noms, des projets, des classes, des méthodes, etc. Quand vous analysez le nombre d’artefacts sur une couche, tenez compte des points suivants :  
  
    -   Si une couche est liée à un artefact contenant d'autres artefacts, mais n'est pas directement liée à ces autres artefacts, le nombre représentera uniquement les artefacts auxquels elle est directement liée. Toutefois, les autres artefacts sont inclus dans l'analyse pendant la validation de couche.  
  
         Par exemple, si une couche est liée à un espace de noms unique, le nombre d'artefacts liés est égal à 1, même si l'espace de noms contient des classes. Si la couche a également des liens vers chaque classe de l'espace de noms, le nombre comprendra les classes liées.  
  
    -   Si une couche contient d'autres couches liées à des artefacts, la couche du conteneur est également liée à ces artefacts, même si le nombre indiqué sur la couche du conteneur ne comprend pas ces artefacts.  
  
     Pour voir les artefacts liés à une couche, cliquez avec le bouton droit sur la couche, puis cliquez sur **Afficher les liens** pour ouvrir l’ **Explorateur de couches**.  
  
-   Une *dépendance* indique qu’une couche peut utiliser la fonctionnalité d’une autre couche, mais pas l’inverse. Une *dépendance bidirectionnelle* indique qu’une couche peut utiliser la fonctionnalité d’une autre couche, et vice versa.  
  
     Pour afficher les dépendances existantes sur le diagramme de couche, cliquez avec le bouton droit sur la surface du diagramme, puis cliquez sur **Générer des dépendances**. Pour décrire les dépendances prévues, dessinez-en de nouvelles.  
  
 Consultez :  
  
-   [Créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Informations de référence sur les diagrammes de couche](../modeling/layer-diagrams-reference.md)  
  
-   [Diagrammes de couche : recommandations](../modeling/layer-diagrams-guidelines.md)  
  
-   [Valider du code avec des diagrammes de couche](../modeling/validate-code-with-layer-diagrams.md)  
  
#### <a name="summary-strengths-of-layer-diagrams"></a>Résumé : atouts des diagrammes de couche  
 Les diagrammes de couche vous aident à :  
  
-   décrire l'architecture logique d'un système selon les fonctionnalités de ses artefacts ;  
  
-   vérifier que le code en cours de développement est conforme à la conception spécifiée.  
  
#### <a name="relationship-to-other-diagrams"></a>Relation aux autres diagrammes  
  
|**Diagramme**|**Description**|  
|-----------------|---------------------|  
|Carte de code|Permet de visualiser l’organisation et les relations dans le code existant.<br /><br /> Pour créer des couches, générez une carte de code, puis regroupez les éléments sur la carte en tant que couches potentielles. Faites glisser les groupes de la carte vers le diagramme de couche.<br /><br /> Consultez :<br /><br /> -   [Mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Parcourir et réorganiser des cartes de code](../modeling/browse-and-rearrange-code-maps.md)|  
|Diagramme de composant|Décrit les composants, leurs interfaces et leurs relations.<br /><br /> Pour visualiser les couches, créez un diagramme de composant qui décrit les fonctionnalités des différents composants du système.<br /><br /> Consultez :<br /><br /> -   [Diagrammes de composants UML : référence](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagrammes de composants UML : indications](../modeling/uml-component-diagrams-guidelines.md)|  
  
## <a name="external-resources"></a>Ressources externes  
  
|**Catégorie**|**Links**|  
|------------------|---------------|  
|**Forums**|-   [Outils de visualisation et de modélisation Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling (outils DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
  
## <a name="see-also"></a>Voir aussi  
 [Visualiser le code](../modeling/visualize-code.md)   
 [Créer des modèles pour votre application](../modeling/create-models-for-your-app.md)   
 [Utiliser des modèles dans votre processus de développement](../modeling/use-models-in-your-development-process.md)   
 [Utiliser des modèles dans le développement Agile](http://msdn.microsoft.com/en-us/592ac27c-3d3e-454a-9c38-b76658ed137f)   
 [Valider votre système pendant le développement](../modeling/validate-your-system-during-development.md)   
 [Étendre des diagrammes et des modèles UML](../modeling/extend-uml-models-and-diagrams.md)



