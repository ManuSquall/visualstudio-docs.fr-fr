---
title: 'Diagrammes de cas d’usage UML : Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: b1ae8ed0-d00b-4f9b-8e23-733e09e81e9b
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fc5dbc6b483313d169a80dc66550dce80a147c96
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823833"
---
# <a name="uml-use-case-diagrams-guidelines"></a>Diagrammes de cas d’usage UML : Recommandations
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, vous pouvez dessiner un *utiliser le diagramme de cas* pour synthétiser les personnes qui utilisent votre application ou système, et qu’ils peuvent faire avec. Pour créer un diagramme de cas d’usage UML, sur le **Architecture** menu, cliquez sur **nouveau UML ou diagramme de couche**.  
  
 Pour une démonstration vidéo, consultez [Organizing Features into cas d’usage](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases/).  
  
 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Prise en charge des versions pour les outils d'architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 À l'aide d'un diagramme de cas d'usage, vous pouvez discuter et communiquer :  
  
- les scénarios dans lesquels votre système ou application interagit avec des personnes, des organisations ou des systèmes externes ;  
  
- les objectifs qu'il aide ces acteurs à atteindre ;  
  
- la portée de votre système.  
  
  Un diagramme de cas d'usage ne montre pas les détails des cas d'usage : il résume uniquement certaines des relations entre les cas d'usage, les acteurs et les systèmes. En particulier, le diagramme n'indique pas l'ordre dans lequel les étapes sont effectuées pour atteindre les objectifs de chaque cas d'usage. Vous pouvez décrire ces détails dans d'autres diagrammes et documents, que vous pouvez lier à chaque cas d'usage. Pour plus d’informations, consultez [description des cas d’usage en détail](#Details) dans cette rubrique.  
  
  Les descriptions que vous fournissez pour les cas d'usage utiliseront plusieurs termes liés au domaine dans lequel le système fonctionne, telles que Vente, Menu, Client et ainsi de suite. Il est important de définir clairement ces termes et leurs relations, ce que vous pouvez faire à l'aide d'un diagramme de classes UML. Pour plus d'informations, consultez [Diagrammes de classes UML : Les instructions](../modeling/uml-class-diagrams-guidelines.md).  
  
  Les cas d'usage traitent uniquement des exigences fonctionnelles d'un système. Les autres exigences telles que les règles métier, les impératifs de qualité de service et les contraintes d'implémentation doivent être représentées séparément. Vous devez également décrire les détails internes et d'architecture séparément. Pour plus d’informations sur la façon de définir les besoins des utilisateurs, consultez [modéliser les besoins des utilisateurs](../modeling/model-user-requirements.md).  
  
  Les exemples utilisés dans cette rubrique concernent un site web sur lequel les clients peuvent commander des repas à des restaurants locaux.  
  
  ![Éléments dans un diagramme de cas d’usage](../modeling/media/uml-ucovactor.png "UML_UCOvActor")  
  
- Un *acteur* (1) est une classe de personne, organisation, appareil ou composants logiciels externes qui interagit avec votre système. Exemples d’acteurs sont **client**, **Restaurant**, **capteur de température**, **agent d’autorisation de carte de crédit.**  
  
- Un *cas d’usage* (2) représente les actions qui sont effectuées par un ou plusieurs acteurs dans le cadre d’un objectif particulier. Cas d’utilisation **commander un repas**, **Menu de mise à jour**, **traiter le paiement**.  
  
   Dans un diagramme de cas d'usage, les cas d'usage sont associés (3) aux acteurs qui les exécutent.  
  
- Votre *système (4)* est ce que vous développez. Il peut s'agir d'un petit composant logiciel (dont les acteurs sont uniquement d'autres composants logiciels), d'une application complète ou d'une grande suite distribuée d'applications déployée sur de nombreux ordinateurs et périphériques. Exemples de sous-systèmes sont **site Web de commande de repas**, **entreprise de livraison de repas**, **site Web Version 2**.  
  
   Un diagramme de cas d'usage peut montrer les cas d'usage qui sont pris en charge par votre système ou ses sous-systèmes.  
  
## <a name="BasicSteps"></a> Étapes de base pour dessiner des diagrammes de cas d’utilisation  
  
> [!NOTE]
> Les étapes détaillées pour créer un des diagrammes de modélisation sont décrites dans [modèles et diagrammes UML modifier](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-new-use-case-diagram"></a>Pour créer un diagramme de cas d'usage  
  
1. Sur le **Architecture** menu, cliquez sur **nouveau UML ou diagramme de couche**.  
  
2. Sous **modèles**, cliquez sur **diagramme de cas UMLUse**.  
  
3. Nommez le diagramme.  
  
4. Dans **ajouter au projet de modélisation**, sélectionnez un projet de modélisation existant dans votre solution, ou **créer un nouveau projet de modélisation**, puis cliquez sur **OK**.  
  
#### <a name="to-draw-a-use-case-diagram"></a>Pour dessiner un diagramme de cas d'usage  
  
1. Faites glisser **sous-système** des limites à partir de la boîte à outils vers le diagramme pour représenter l’intégralité de votre système ou ses principaux composants.  
  
    - Vous pouvez dessiner un diagramme de cas d'usage sans limites de système si vous ne souhaitez pas décrire les cas d'usage qui sont pris en charge par votre système ou ses composants.  
  
    - Faites glisser le coin d'un système pour l'agrandir, si nécessaire.  
  
    - Renommez-le comme il se doit.  
  
2. Faites glisser **acteurs** à partir de la boîte à outils vers le diagramme (en les plaçant en dehors de toute limite système).  
  
    - Les acteurs représentent des classes d'utilisateurs, d'organisations et de systèmes externes qui interagissent avec votre système.  
  
    - Renommez-les. Par exemple :  **Agence de carte de crédit du client, Restaurant.**  
  
3. Faites glisser **cas d’usage** à partir de la boîte à outils vers les systèmes appropriés.  
  
    - Les cas d'usage représentent les activités que les acteurs exécutent avec l'aide de votre système.  
  
    - Renommez-les à l'aide de titres que les acteurs eux-mêmes comprendront. N'utilisez pas de titres associés à votre code. Par exemple :  **Commander un repas, payer un repas, livrer le repas**.  
  
    - Commencer avec les transactions majeures telles que **commander un repas**, laissant jusqu'à occuper des interactions mineures telles que **sélectionner un élément de Menu**.  
  
    - Placez chaque cas d'usage dans le système ou le sous-système majeur qui le prend en charge (en ignorant toute façade ou tout composant impliqué uniquement dans la connexion à l'utilisateur).  
  
    - Vous pouvez dessiner un cas d'usage en dehors de la limite système pour montrer qu'il n'est pas pris en charge par votre système, par exemple dans une version particulière.  
  
4. Cliquez sur **Association** dans la boîte à outils, sur un cas d’usage et sur un acteur qui est inclus dans le cas d’usage. Liez chaque acteur à ses cas d'usage de cette manière.  
  
5. Cas de structure de l’utilisation avec le **Include**, **étendre** et **généralisation** relations. Pour créer chacun de ces liens, cliquez sur l'outil, sur le cas d'usage source, puis sur la cible. Consultez la section suivante intitulée [structuration de cas d’utilisation](#Structuring).  
  
6. Décrivez les cas d'usage plus en détail. Consultez la section suivante intitulée [description des cas d’usage en détail](#Details).  
  
7. Dessinez des diagrammes distincts pour vous concentrer sur différents sous-systèmes ou groupes de cas d'usage connexes. Tous les diagrammes dans un projet de modélisation sont des vues du même modèle.  
  
## <a name="Actors"></a> Dessin d’acteurs et cas d’utilisation  
 L'objectif principal d'un diagramme de cas d'usage est d'illustrer qui interagit avec votre système et les principaux objectifs qu'ils atteignent grâce à lui.  
  
- Créer **acteurs** pour représenter des classes de personnes, organisations, autres systèmes, logiciels ou périphériques qui interagissent avec votre système ou sous-système.  
  
  - Pour savoir comment dessiner des acteurs et autres éléments, consultez [modèles et diagrammes UML modifier](../modeling/edit-uml-models-and-diagrams.md).  

  - Pour chaque ensemble d'objectifs distinct, identifiez les acteurs par type ou par rôle, même si les personnes physiques ou les entités sont les mêmes. Par exemple, Restaurant et Client sont des acteurs distincts, même si un employé de restaurant peut parfois être un client.  
  
- Créer **cas d’usage** pour chacun des objectifs que chaque acteur cherche à atteindre avec le système.  
  
  - Nommez et décrivez les cas d'usage à l'aide de mots compréhensibles par l'acteur, plutôt qu'à l'aide de termes d'implémentation.  
  
- Utilisez **Associations** pour lier les acteurs aux cas d’usage.  
  
### <a name="inheritance-between-actors"></a>Héritage entre les acteurs  
 ![Diagramme de cas d’usage montrant l’héritage](../modeling/media/uml-ucguideinherit.png "UML_UCGuideInherit")  
  
 Vous pouvez dessiner un **généralisation** lien entre les acteurs. L'acteur spécialisé, tel que Client de club dans notre exemple, hérite des cas d'usage de l'acteur généralisé, tel que Client. La flèche doit pointer vers l'acteur le plus général, tel que Client. Quand vous créez le lien, pointez d'abord vers l'acteur le plus spécialisé.  
  
 L'acteur spécialisé peut avoir ses propres scénarios d'usage supplémentaires qui ne sont pas accessibles aux autres acteurs.  
  
> [!CAUTION]
> Vous ne devez pas créer de boucles de relations de généralisation qui font qu'un acteur se généralise lui-même. Les boucles peuvent générer des erreurs.  
  
### <a name="alternative-actor-icons"></a>Autres icônes d'acteurs  
 Vous pouvez utiliser des icônes personnalisées pour représenter un acteur, plutôt que le dessin minimaliste standard. Vous pouvez par exemple choisir une icône de périphérique, de restaurant, de banque et ainsi de suite.  
  
##### <a name="to-change-the-appearance-of-an-actor"></a>Pour modifier l'apparence d'un acteur  
  
1. Avec le bouton droit de l’acteur, puis cliquez sur **propriétés**.  
  
     La fenêtre **Propriétés** s'affiche.  
  
2. Définir le **chemin d’accès de l’Image** propriété à l’emplacement d’un fichier image.  
  
    - Vous pouvez utiliser plusieurs formats d'image, notamment .bmp, .gif et .jpg.  
  
    - Utilisez un fichier inclus dans le contrôle de code source de la solution ou du projet, pour qu'il soit toujours disponible en cas de déplacement ou de copie de la solution.  
  
3. Pour répliquer cette apparence dans d'autres diagrammes de cas d'usage, copiez l'acteur et collez-le dans un autre diagramme.  
  
    - Le changement d'image s'applique uniquement à la vue dans un diagramme particulier. Il ne s'applique pas à l'élément de modèle sous-jacent. Si vous faites glisser l'acteur depuis l'Explorateur de modèles UML vers un autre diagramme, il apparaît sous forme de dessin minimaliste standard.  
  
### <a name="multiplicities-between-actors-and-use-cases"></a>Multiplicités entre acteurs et cas d'usage  
 L’association entre un acteur et un cas d’usage peut afficher une *multiplicité* à chaque extrémité.  
  
 ![Utiliser des cas un-à-un avec acteur](../modeling/media/uml-ucguidemulti1.png "UML_UCGuideMulti1")  
  
> [!NOTE]
> Les multiplicités d’une association dans un diagramme de cas d’usage sont masquées si elles sont toutes deux **1**.  
  
 Par défaut, chaque multiplicité est **1**. Dans une stricte interprétation du modèle, une multiplicité de 1 signifie par exemple qu'un seul client est impliqué dans la commande de chaque repas et que chaque client ne commande qu'un seul repas à la fois.  
  
 Vous pouvez modifier ces multiplicités.  
  
 Par exemple :  
  
 ![Cas d’usage montrant la multiplicité plusieurs à plusieurs](../modeling/media/uml-ucguidemulti2.png "UML_UCGuideMulti2")  
  
- Pour indiquer que plusieurs acteurs de la même classe peuvent prendre part à une occurrence unique d’un cas d’usage, définissez la multiplicité à la fin de l’acteur de l’association à **1..\*** .  
  
   Dans l'illustration, un ou plusieurs restaurants peuvent participer à l'exécution de la même commande de repas.  
  
- Pour montrer que chaque acteur peut participer simultanément à plusieurs occurrences d’un cas d’usage, définissez la multiplicité à l’extrémité cas d’usage de l’association à **\*** .  
  
   Dans l'illustration, chaque restaurant peut satisfaire plusieurs commandes à la fois.  
  
##### <a name="to-set-multiplicities-on-an-association"></a>Pour définir les multiplicités sur une association  
  
1. Avec le bouton droit de l’association, puis cliquez sur **propriétés**.  
  
2. Développez le **premier rôle** ou **deuxième rôle**.  
  
    *Rôle* signifie que l’élément à une extrémité de l’association.  
  
3. Définissez la propriété Multiplicité en choisissant dans la liste :  
  
   - **1** pour indiquer qu’exactement une instance de ce rôle participe à chaque lien.  
  
   - **1..\***  à l’état une ou plusieurs instances de ce rôle participent de chaque lien.  
  
   - **valeur 0.. 1** pour indiquer que la participation est facultative.  
  
   - **\*** pour indiquer que zéro ou plusieurs instances de ce rôle participent au lien.  
  
> [!NOTE]
> De nombreuses équipes ne placent pas les informations de multiplicité sur les diagrammes de cas d'usage et laissent les multiplicités définies sur la valeur par défaut (1). Au lieu de cela, elles fournissent ces informations dans des descriptions séparées des cas d'usage. Dans ce cas, toutes les multiplicités dans les diagrammes de cas d'usage seront masquées.  
  
### <a name="using-an-actor-or-use-case-on-multiple-diagrams"></a>Utilisation d'un acteur ou d'un cas d'usage dans plusieurs diagrammes  
 Vous pouvez afficher les mêmes acteurs et cas d'usage dans plusieurs diagrammes. Par exemple :  
  
- Vous pouvez décrire dans différents diagrammes les différents cas d'usage dans lesquels un acteur est impliqué.  
  
- Vous pouvez utiliser un diagramme pour montrer les acteurs et les sous-systèmes auxquels un cas d'usage est associé et utiliser un autre diagramme pour montrer comment le cas d'usage est structuré en plusieurs cas d'usage inclus et étendus.  
  
##### <a name="to-show-the-same-actor-or-use-case-on-different-diagrams"></a>Pour afficher le même acteur ou cas d'usage dans différents diagrammes  
  
1. Créez l'acteur ou le cas d'usage dans un diagramme.  
  
2. Créez un autre diagramme de cas d'usage.  
  
3. Faites glisser un acteur ou cas d’usage **l’Explorateur de modèles** vers le nouveau diagramme.  
  
    > [!NOTE]
    > Si vous placez sur le nouveau diagramme un acteur et un cas d'usage qui sont déjà associés, leur association apparaît automatiquement sur le nouveau diagramme.  
  
## <a name="Details"></a> Description des cas d’usage en détail  
 Un cas d'usage représente :  
  
- Un objectif d’un acteur en utilisant le système, tel que **acheter un repas**; et  
  
- Un ou plusieurs *scénarios*, autrement dit, les séquences d’étapes effectuées dans le cadre de la poursuite de l’objectif, par exemple : {**commander un repas, payer, livrer**}. En plus des scénarios de réussite, il peut exister plusieurs exceptions ou scénarios d’échec, tel que **carte de crédit refusée**.  
  
  Vous pouvez décrire un cas d'usage selon différents niveaux de détail. Lors des phases initiales de conception, le seul nom sur le diagramme de cas d'usage suffit.  Ultérieurement, vous pouvez rédiger des descriptions plus détaillées des scénarios.  
  
  Dans Visual Studio Ultimate, vous pouvez décrire un cas d'usage de plusieurs façons, qui peuvent être utilisées séparément ou ensemble :  
  
- Liez le cas d'usage à un ou plusieurs diagrammes dans le projet.  
  
  - Un diagramme d'activités aide à expliquer un processus plus complexe où il existe des boucles, des branches et des threads parallèles. Il peut également illustrer le flux de données entre différentes parties du processus. Pour plus d’informations, consultez [diagrammes d’activités UML : Les instructions](../modeling/uml-activity-diagrams-guidelines.md).  
  
  - Un diagramme de séquence aide à expliquer une série complexe d'interactions entre différents acteurs. Vous pouvez également l'utiliser pour montrer ce qui se passe dans le système en réponse à chaque cas d'usage. Pour plus d’informations, consultez [diagrammes de séquence UML : Les instructions](../modeling/uml-sequence-diagrams-guidelines.md).  
  
- Liez le cas d'usage à une page, une section ou un paragraphe OneNote qui décrit le cas d'usage en détail.  
  
- Liez le cas d'usage à un document Word, dans lequel vous utilisez du texte, des captures d'écran, et ainsi de suite, pour décrire les scénarios du cas d'usage. Pour plus d’informations, consultez [modéliser les besoins de l’utilisateur](../modeling/model-user-requirements.md).  
  
#### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Pour lier un cas d'usage à un diagramme ou à un fichier dans la même solution  
  
1. Dessinez un diagramme (tel qu'un diagramme de séquence ou un diagramme d'activités) pour illustrer un scénario du cas d'usage.  
  
2. Revenez au diagramme de cas d'usage.  
  
3. Faites glisser le diagramme ou le fichier de l'Explorateur de solutions vers une partie vide du diagramme de cas d'usage.  
  
4. Se connecter à partir de l’artefact à utilisation cas en utilisant un **dépendance**.  
  
#### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Pour créer un lien vers un fichier de solution tel qu'un document Word ou une présentation PowerPoint  
  
1. Rédigez un document qui utilise du texte, des captures d'écran, et ainsi de suite, pour décrire le scénario du cas d'usage.  
  
2. Ajoutez le document à la solution.  
  
    1. Déplacez le document Word dans le même dossier Windows que la solution.  
  
    2. Dans l’Explorateur de solutions, cliquez sur la solution, pointez sur **ajouter**, puis cliquez sur **élément existant**.  
  
    3. Accédez au document Word et cliquez sur **ajouter**.  
  
         Le document Word s'affiche dans un dossier de solution dans l'Explorateur de solutions.  
  
3. Faites glisser le document Word de l'Explorateur de solutions vers une partie vide du diagramme de cas d'usage.  
  
     Un nouvel artefact s'affiche.  
  
4. Se connecter à partir de l’artefact à utilisation cas en utilisant un **dépendance**.  
  
#### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Pour créer un lien vers un élément OneNote, une page web ou un document partagé  
  
1. Obtenez l'URL de l'élément partagé. Il peut s’agir, par exemple, un début de chemin d’accès de fichier réseau '\\\\», ou une page web ou URL Sharepoint commençant par « http:// » ou un lien vers une section OneNote, page ou un paragraphe de début « onenote : ».  
  
2. Dans la boîte à outils, cliquez sur **artefact** puis cliquez sur dans le diagramme de cas d’usage.  
  
3. Une fois le nouvel artefact sélectionné, tapez ou collez l’URL dans le **Hyperlink** propriété.  
  
> [!NOTE]
> Vous pouvez double-cliquer sur un artefact pour ouvrir le diagramme ou le document auquel il est lié.  
  
### <a name="linking-use-cases-to-work-items"></a>Lier des cas d'usage à des éléments de travail  
 Si votre projet utilise [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] et vous avez [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], vous pouvez lier chaque cas d’usage à un élément de travail dans [!INCLUDE[esprfound](../includes/esprfound-md.md)]. Pour savoir comment créer ces liens, consultez [lier des éléments de modèle et des éléments de travail](../modeling/link-model-elements-and-work-items.md).  
  
 Cela vous permet d'effectuer les opérations suivantes :  
  
- Décrire le cas d'usage dans l'élément de travail lié. En particulier, si votre projet utilise le modèle de processus formel Visual Studio, vous pouvez établir un lien à un élément de travail de cas d'usage. Ce type d'élément de travail fournit des champs permettant de décrire les objectifs et les scénarios du cas d'usage.  
  
- Lier des cas de test au cas d'usage pour pouvoir obtenir des rapports et savoir dans quelle mesure le code en cours de développement implémente le cas d'usage.  
  
- Lier des tâches au cas d'usage pour pouvoir suivre la progression du travail de développement.  
  
## <a name="Structuring"></a> Structuration des cas d’usage  
 Vous devez tenter de décrire le comportement de votre système avec seulement quelques cas d'usage principaux. Chaque grand cas d'usage définit un objectif majeur qu'un acteur doit atteindre, comme l'achat d'un produit ou, du point de vue du fournisseur, la fourniture de produits pour la vente.  
  
 Une fois ces objectifs clairement établis, vous pouvez définir plus en détail comment chaque objectif est atteint et quelles sont les variantes des objectifs de base.  
  
 Évitez de décomposer les cas d'usage de manière trop détaillée. Les cas d'usage concernent l'expérience des utilisateurs de votre système, plutôt que ses mécanismes internes. De plus, il est souvent plus productif de créer des versions préliminaires opérationnelles du code que de passer du temps à structurer les cas d'usage dans les moindres détails.  
  
 Vous pouvez résumer dans un diagramme de cas d'usage les relations entre les cas d'usage principaux et plus détaillés. Ces opérations sont décrites dans les sections suivantes :  
  
- [Affichage des détails d’un cas d’usage avec Include](#Include)  
  
- [Partage d’objectifs avec généralisation](#Inheritance)  
  
- [Séparation des variantes de cas avec étendre](#Extend)  
  
### <a name="Include"></a> Affichage des détails d’un cas d’usage avec Include  
 Utiliser un **Include** relation pour afficher ce cas d’usage décrit certains détails d’un autre. Dans l’illustration, **commander un repas** inclut **payer**, **Menu choisissez**, et **choisir un élément de Menu**. Chacun des cas d'usage inclus et plus détaillé est une étape que l'acteur peut devoir effectuer pour atteindre l'objectif global du cas d'usage d'inclusion. La flèche doit pointer vers le cas d'usage inclus et plus détaillé.  
  
> [!CAUTION]
> Vous ne devez pas créer de boucles de relations d'inclusion qui font en sorte qu'un cas d'usage s'inclut lui-même. Les boucles peuvent générer des erreurs.  
  
 Vous pouvez partager des cas d'usage inclus. Dans l’exemple, le **commander un repas** et **s’abonner aux révisions** incluent tous deux des cas d’usage **payer**.  
  
 ![Cas d’usage décomposés avec :](../modeling/media/uml-ucguideinclude.png "UML_UCGuideInclude")  
  
 L'objectif et les scénarios d'un cas d'usage inclus doivent être indépendamment significatifs, pour pouvoir être inclus dans les cas d'usage conçus ultérieurement.  
  
 La séparation des cas d'usage en parties d'inclusion et parties incluses est utile pour atteindre les objectifs suivants :  
  
- structurer vos descriptions de cas d'usage dans différents niveaux de détail ;  
  
- éviter de répéter des scénarios partagés dans différents cas d'usage.  
  
#### <a name="Steps"></a> Définition de l’ordre des étapes détaillées  
 Le diagramme de cas d'usage ne dit rien sur l'ordre dans lequel les étapes plus détaillées doivent être exécutées, ni si chacune d'elles est toujours nécessaire.  
  
 Pour clarifier l’ordre des étapes, vous pouvez utiliser un **artefact** pour attacher un document distinct, avec notamment cas d’usage. Dans l'exemple suivant, un diagramme d'activités est attaché au cas d'usage Commander un repas. Vous pouvez également utiliser un document texte qui contient une liste d'étapes ou une séquence de captures d'écran. Pour plus d’informations, consultez [description des cas d’usage en détail](#Details).  
  
 Notez les conventions d'affectation de noms suivantes quand vous utilisez un diagramme d'activités :  
  
- Le nom de l'activité complète est le même que celui du cas d'usage d'inclusion.  
  
- Les noms des actions dans le diagramme d'activités sont les mêmes que ceux des cas d'usage inclus.  
  
  Pour plus d’informations, consultez [diagrammes d’activités UML : Les instructions](../modeling/uml-activity-diagrams-guidelines.md).  
  
  ![Utilisez les étapes du cas indiqués dans le diagramme d’activités lié](../modeling/media/uml-ucguidesteps.png "UML_UCGuideSteps")  
  
### <a name="Inheritance"></a> Partage d’objectifs avec généralisation  
 Utilisez une relation Généralisation pour montrer qu’un *spécialisé* cas d’usage est une manière particulière d’atteindre les objectifs exprimés par un autre *général* cas d’usage. La flèche ouverte doit pointer vers le cas d'usage plus général.  
  
 ![Utiliser des scénarios montrant la relation de généralisation](../modeling/media/uml-ucguidegeneral.png "UML_UCGuideGeneral")  
  
 Par exemple, **payer** généralise **payer par carte de crédit** et **payer en espèces**.  
  
> [!CAUTION]
> Vous ne devez pas créer de boucles de relations de généralisation qui font qu'un acteur se généralise lui-même. Les boucles peuvent générer des erreurs.  
  
 Les cas d'usage spécialisés peuvent vous aider à montrer les différentes manières grâce auxquelles votre système peut atteindre le même objectif.  
  
 Les cas d'usage spécialisés sont considérés comme héritant des objectifs et des acteurs du cas d'usage général. Le cas d'usage général n'est pas obligé d'avoir ses propres scénarios ; ses spécialisations décrivent différentes façons d'atteindre les objectifs.  
  
##### <a name="to-refactor-common-goals-from-two-or-more-use-cases"></a>Pour refactoriser des objectifs communs à partir de plusieurs cas d'usage  
  
1. Créez et nommez le nouveau cas d'usage général.  
  
2. Créer un **généralisation** relation avec la grande flèche pointant vers le nouveau cas d’usage général.  
  
    1. Cliquez sur **généralisation** dans la boîte à outils.  
  
    2. Cliquez sur un cas d’usage spécialisé (**payer par carte de crédit** dans l’exemple).  
  
    3. Cliquez sur le cas d’usage général (**payer** dans l’exemple).  
  
3. Si vous avez décrit les objectifs des cas d'usage spécialisés, déplacez les parties communes vers la description du cas d'usage général.  
  
4. Les acteurs partagés par les cas d'usage spécialisés peuvent être déplacés vers le cas d'usage général.  
  
### <a name="Extend"></a> Séparation de variantes de cas avec étendre  
 Utilisez un lien Étendre pour montrer qu'un cas d'usage peut ajouter des fonctionnalités à un autre cas d'usage dans certaines circonstances. La flèche doit pointer vers le cas d'usage principal étendu.  
  
 ![Extension d’un autre cas d’usage](../modeling/media/uml-ucguideextend.png "UML_UCGuideExtend")  
  
> [!CAUTION]
> Vous ne devez pas créer de boucles de relations d'extension qui font qu'un acteur se généralise lui-même. Les boucles peuvent générer des erreurs.  
  
 Par exemple, le **connexion** cas d’utilisation d’un site Web classique peut inclure **inscrire un nouvel utilisateur** - mais uniquement lorsque l’utilisateur ne possède pas un compte.  
  
##### <a name="to-separate-a-use-case-into-main-and-extending-parts"></a>Pour séparer un cas d'usage en parties principales et d'extension  
  
1. Créez et nommez le nouveau cas d'usage d'extension.  
  
2. Créer un **étendre** relation avec la flèche pointant vers le cas d’usage étendu.  
  
   1. Cliquez sur **étendre** dans la boîte à outils.  
  
   2. Cliquez sur le cas d’utilisation d’extension (**inscrire un nouvel utilisateur** dans l’exemple).  
  
   3. Cliquez sur le cas d’usage étendu (**connexion** dans l’exemple).  
  
       > [!NOTE]
       > Évitez de créer une boucle de relations Étendre dans le diagramme. Un cas d'usage ne doit pas être une extension de lui-même.  
  
3. Si vous avez déjà créé des scénarios pour le cas d'usage étendu, déplacez les étapes pertinentes dans le scénario de l'extension.  
  
4. La description de l’extension (**inscrire un nouvel utilisateur** dans l’exemple) doit inclure les détails de l’emplacement dans les scénarios de cas d’usage principal cela se produit et dans quelles circonstances. Cela équivaut un peu à modifier la description du cas principal.  
  
   Le cas d'usage d'extension représente des étapes de scénario qui feraient autrement partie des scénarios du cas d'usage principal. Le scénario et l'objectif de l'extension seront toujours lus dans le contexte du cas d'usage principal. Il n'est donc pas nécessaire qu'ils soient utiles indépendamment.  
  
   La séparation des extensions peut être utile pour décrire les situations suivantes :  
  
- Il existe des acteurs supplémentaires impliqués uniquement dans le cas d'usage d'extension. Par exemple, un administrateur doit approuver l'inscription d'un client sur le site web.  
  
- Un sous-système distinct gérera le cas d'usage d'extension.  
  
- Cette extension sera disponible uniquement dans des versions spécifiques du système. Vous pouvez afficher chaque version en tant que sous-système distinct dans le diagramme de cas d'usage.  
  
## <a name="Subsystems"></a> À l’aide des limites de sous-systèmes  
 Utilisez une limite de sous-système pour montrer les cas d'usage qui sont dans la portée de votre système.  
  
#### <a name="to-draw-a-subsystem-boundary"></a>Pour dessiner une limite de sous-système  
  
1. Dans la boîte à outils, cliquez sur **sous-système**, puis cliquez sur le diagramme.  
  
    Un sous-système apparaît sur le diagramme.  
  
2. Faites glisser les coins du sous-système pour ajuster sa taille.  
  
3. Faites glisser des cas d'usage existants dans ou hors du sous-système pour ajuster son contenu.  
  
   \- ou -  
  
   Pour créer un nouveau cas d’usage directement dans un sous-système, cliquez sur **cas d’usage** dans la boîte à outils, puis cliquez sur à l’intérieur du sous-système.  
  
> [!NOTE]
> Le **sujets** propriété d’un cas d’usage indique le sous-système dans lequel il est contenu.  
  
### <a name="use-cases-outside-the-system-scope"></a>Cas d'usage en dehors de la portée du système  
 Il est souvent utile d'inclure dans le diagramme les cas d'usage qui font partie de l'entreprise mais qui ne sont pas gérés par le système que vous développez. Cela aide les développeurs à comprendre le contexte de leur travail. Par exemple, Livrer le repas peut être affiché comme un cas d'usage impliquant les acteurs Restaurant et Client, mais en dehors de la responsabilité du Site web Commande de repas.  
  
### <a name="multiple-subsystems"></a>Sous-systèmes multiples  
 Vous pouvez créer plusieurs limites de sous-systèmes pour illustrer comment différents cas d'usage sont gérés par différents composants du système. Par exemple, **ajouter une évaluation de Restaurant** peut être traité sur un autre site Web. N'oubliez pas qu'un diagramme de cas d'usage doit traiter de ce qui est visible par l'utilisateur. Si vous souhaitez décrire la division interne du travail dans le système, utilisez plutôt un diagramme de composant.  
  
### <a name="system-versions"></a>Versions du système  
 Vous pouvez utiliser différentes limites de sous-systèmes pour illustrer différentes versions du système. Par exemple, le cas d'usage Payer peut être inclus dans le site web de Version 2, mais pas dans la Version 1. Cela implique que le système aide les clients à passer leurs commandes. Toutefois, ils doivent payer le restaurant directement.  
  
 Utilisez **dépendance** relations pour lier des sous-systèmes représentant différentes versions ou variantes.  
  
 ![Les sous-systèmes affichent différentes versions d’un système](../modeling/media/uml-ucguidesystem.png "UML_UCGuideSystem")  
  
## <a name="see-also"></a>Voir aussi  
 [Modéliser les besoins des utilisateurs](../modeling/model-user-requirements.md)   
 [Diagrammes de séquence UML : Instructions](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Modifier des modèles UML et des diagrammes](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagrammes de cas d’usage UML : Référence](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagrammes de classes UML : Référence](../modeling/uml-class-diagrams-reference.md)   
 [Diagrammes de composants UML : Référence](../modeling/uml-component-diagrams-reference.md)   
 [Diagrammes d’activités UML : Instructions](../modeling/uml-activity-diagrams-guidelines.md)   
 [Vidéo : Organisation des fonctions en cas d’utilisation](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases/)
