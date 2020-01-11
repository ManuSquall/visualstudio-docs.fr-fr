---
title: Configuration requise pour l’utilisateur du modèle | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
- UML, modeling requirements
ms.assetid: 359900f8-6d69-493d-bfdf-2c9069c74a26
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d70a7c8b7dbf6015e992cfabb5204f3b307238a
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75844916"
---
# <a name="model-user-requirements"></a>Modéliser les besoins des utilisateurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio vous aide à comprendre, discuter et communiquer les besoins de vos utilisateurs en dessinant des diagrammes sur leurs activités et le rôle joué par votre système pour les aider à atteindre leurs objectifs. Un modèle d’impératifs est un ensemble de tels diagrammes, chacun étant axé sur un aspect différent des besoins des utilisateurs. Pour obtenir une démonstration vidéo, consultez : [Modeling the Business Domain (Modélisation du domaine d’entreprise)](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain).

 Pour connaître les versions de Visual Studio qui prennent en charge chaque type de modèle, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Un modèle d’impératifs vous aide à :

- Vous concentrer sur le comportement externe du système, indépendamment de sa conception interne

- Décrire les besoins des utilisateurs et des parties prenantes avec beaucoup moins d’ambiguïté qu’en langage naturel

- Définir un glossaire cohérent de termes qui peuvent être utilisés par les utilisateurs, les développeurs et les testeurs

- Réduire les oublis et les incohérences des impératifs

- Réduire la somme de travail nécessaire pour répondre aux changements d’impératifs

- Planifier l’ordre dans lequel les fonctionnalités seront développées

- Utiliser les modèles comme base pour les tests système et clarifier la relation entre les tests et les impératifs Quand les impératifs changent, cette relation vous aide à mettre à jour les tests correctement. Cela permet de s’assurer que le système répond aux nouveaux impératifs.

  Un modèle d’impératifs est le plus utile si vous l’utilisez pour focaliser les discussions avec les utilisateurs ou leurs représentants et si vous le revisitez au début de chaque itération. Il est inutile de le remplir de manière détaillée avant d’écrire le code. Une application partiellement fonctionnelle, même si elle est grandement simplifiée, constitue en général la base la plus stimulante pour toute discussion des impératifs avec les utilisateurs. Le modèle permet de résumer les résultats de ces discussions de façon efficace. Pour plus d’informations, consultez [utiliser des modèles dans votre processus de développement](../modeling/use-models-in-your-development-process.md).

> [!NOTE]
> Tout au long de ces rubriques, le terme « système » faire référence au système ou à l’application que vous développez. Il peut s’agir d’une grande collection de nombreux composants matériels et logiciels, d’une application unique ou d’un composant logiciel à l’intérieur d’un système plus grand. Dans tous les cas, le modèle d’impératifs décrit le comportement qui est visible de l’extérieur de votre système, par le biais d’une interface utilisateur ou d’une API.

## <a name="common-tasks"></a>Tâches courantes
 Vous pouvez créer plusieurs vues différentes des impératifs des utilisateurs.  Chaque vue fournit un type particulier d’informations.  Lors de la création de ces vues, il est préférable de passer fréquemment de l’une à l’autre. Vous pouvez commencer à partir de n’importe quelle vue.

|Diagramme ou document|Ce qu’il décrit dans un modèle d’impératifs|Section|
|-------------------------|-----------------------------------------------|-------------|
|Diagramme de cas d'usage|Qui utilise le système et ce qu’ils font avec lui.|[Description de l’utilisation de votre système](#UseCases)|
|Diagramme de classes conceptuelles|Glossaire des types utilisés pour décrire les impératifs et des types visibles à l’interface du système.|[Définition des termes utilisés pour décrire les spécifications](#RequirementsClasses)|
|Diagramme d'activités|Flux de travail et d’informations entre les activités effectuées par les utilisateurs et le système ou ses composants.|[Présentation du workflow de travail entre les utilisateurs et votre système](#Workflow)|
|Diagramme de séquence|Séquence d’interactions entre les utilisateurs et le système ou ses composants. Autre vue du diagramme d’activités.|[Montrer les interactions entre les utilisateurs et votre système](#Sequences)|
|Autres documents ou éléments de travail|Critères de performances, de sécurité, de facilité d’utilisation et de fiabilité.|[Description des impératifs de qualité de service](#QoSRequirements)|
|Autres documents ou éléments de travail|Contraintes et règles non spécifiques à un cas d’usage particulier|[Affichage des règles métier](#BusinessRules)|

 Notez que la plupart des types de diagrammes peuvent être utilisés à d’autres fins. Pour obtenir une vue d’ensemble des types de diagrammes, consultez [créer des modèles pour votre application](../modeling/create-models-for-your-app.md). Pour obtenir des informations de base sur les diagrammes de dessin, consultez [modifier des modèles et des diagrammes UML](../modeling/edit-uml-models-and-diagrams.md).

## <a name="UseCases"></a>Description de l’utilisation de votre système
 Créez des diagrammes de cas d’usage pour décrire qui utilise le système et dans quel but. Un cas d’usage correspond à un objectif d’un utilisateur du système et à la procédure qu’il applique pour atteindre cet objectif.

 Par exemple, un système de vente de repas en ligne doit permettre aux clients de choisir des éléments dans un menu et aux restaurants proposant ce service de mettre à jour le menu. Vous pouvez résumer tout cela dans un diagramme de cas d’usage :

 ![Cas d’usage pour le client et le restaurant](../modeling/media/uml-reqmuc1.png "UML_ReqmUC1")

 Vous pouvez également montrer comment un cas d’usage est composé de plus petits cas. Par exemple, la commande d’un repas fait partie de l’achat d’un repas, qui comprend également le paiement et la livraison :

 ![Le système participe au paiement mais pas à la livraison.](../modeling/media/uml-reqmuc2.png "UML_ReqmUC2")

 Vous pouvez aussi montrer quels cas d’usage sont inclus dans la portée du système que vous développez. Par exemple, le système illustré ici ne participe pas au cas d’usage Livraison de repas. Cela aide à définir le contexte pour le travail de développement. (Dans un diagramme de cas d’usage, les conteneurs de sous-systèmes peuvent servir à représenter le système ou ses composants.)

 Il aide aussi votre équipe à discuter de ce qui sera inclus dans les versions successives. Vous pouvez par exemple décider si, dans la version initiale du système, le Paiement du repas s’effectue directement entre le restaurant et le client, au lieu de passer par le système. Dans ce cas, vous pouvez déplacer la partie « Paiement du repas » hors du rectangle « Système Dîner maintenant » pour la version initiale.

 Un diagramme de cas d’usage fournit uniquement un résumé des cas d’usage. Pour fournir des descriptions plus détaillées, vous pouvez lier les cas d’usage sur le diagramme à des documents distincts et à d’autres diagrammes. Pour savoir comment procéder, consultez [lier un cas d’usage à des documents et des diagrammes](../modeling/link-a-use-case-to-documents-and-diagrams.md).

 Le fait de dessiner un diagramme de cas d’usage aide votre équipe à :

- Se concentrer sur ce que les utilisateurs prévoient de faire avec le système, sans être distraits par les détails de l’implémentation

- Discuter de la portée de votre système ou de versions particulières du système

  Les rubriques suivantes fournissent des informations supplémentaires :

|Pour en savoir plus sur|Lecture|
|--------------------|----------|
|Informations plus détaillées sur la façon de créer des cas d’usage|[Diagrammes de cas d’usage UML : recommandations](../modeling/uml-use-case-diagrams-guidelines.md)|
|Éléments dans un diagramme de cas d’usage|[Informations de référence sur les diagrammes de cas d’usage UML](../modeling/uml-use-case-diagrams-reference.md)|
|Comment développer du code à partir de cas d’usage|[Modéliser l’architecture de votre application](../modeling/model-your-app-s-architecture.md)|

## <a name="RequirementsClasses"></a>Définition des termes utilisés pour décrire les spécifications
 Vous pouvez utiliser des diagrammes de classes UML pour vous aider à développer une terminologie cohérente des concepts métier utilisés aux fins suivantes :

- Par les utilisateurs eux-mêmes pour discuter de l’entreprise au sein de laquelle le système s’exécute.

- Pour décrire les besoins des utilisateurs, par exemple dans les descriptions des cas d’usage, des règles d’entreprise et des récits utilisateur.

- Les types d’informations échangées au niveau de l’API du système ou par le biais de l’interface utilisateur.

- Descriptions des tests système ou d’acceptation.

  Quand il est utilisé à cet effet, le contenu d’un diagramme de classes UML est appelé « diagramme de classes conceptuelles ». (Les termes *modèle de domaine* et *modèle de classe d’analyse*sont également utilisés.)

  Un diagramme de classes conceptuelles montre uniquement les classes nécessaires dans les descriptions des impératifs, sans montrer les détails de la conception interne du système. Le diagramme n’affiche aucun détail sur la conception interne du système. En règle générale, les classes conceptuelles ne montrent pas les opérations ou les interfaces.

  Par exemple, vous pourriez dessiner ces classes conceptuelles pour le système Dîner maintenant :

  ![Menu classes, ordre, élément de menu, ordre d’élément.](../modeling/media/uml-reqmcd1.png "UML_ReqMCD1")

  Un diagramme de classes conceptuelles fournit la terminologie employée dans le modèle d’impératifs. Par exemple, dans la description détaillée du cas d’usage Commander un repas, vous pourriez écrire :

  Le client choisit un *Menu* à partir duquel créer une *Commande*, puis il crée des *Éléments de commande* dans la *Commande* en sélectionnant des *Éléments de menu* dans le *Menu*.

  Notez que les termes utilisés dans cette description correspondent à des noms de classes dans le modèle. Le diagramme supprime les ambiguïtés des relations entre ces classes. Par exemple, il montre clairement que chaque Commande est associée à un seul Menu.

  Les malentendus quant aux besoins des utilisateurs sont souvent dus à des malentendus quant aux significations détaillées des termes. Par exemple, la plupart des restaurants comprennent les termes Menu et Commande de manière identique, mais la différence entre un élément d’une Commande et un élément d’un Menu est moins évidente. Lors de l’examen des impératifs avec les parties prenantes, il est important d’exposer ces différences. Le diagramme de classes est un outil utile pour vous aider à clarifier les termes et leurs relations.

  Le modèle de classes conceptuelles peut former le vocabulaire de base à partir duquel la logique métier de votre système peut être décrite. En revanche, les classes dans le logiciel sont généralement beaucoup plus complexes que le modèle conceptuel, car votre implémentation doit tenir compte de différents facteurs tels que les performances, la distribution ou la flexibilité. On trouve fréquemment plusieurs implémentations différentes d’une classe conceptuelle dans un système.

  Par exemple, les Commandes peuvent être représentées en XML, SQL, HTML et C# dans différentes parties du système et au niveau de différentes interfaces entre les parties. L’association entre une Commande et un Menu peut être représentée de nombreuses manières, par exemple par des références au sein du code C#, des relations dans une base de données ou des ID à références croisées en XML. En dépit de ces variations, le modèle conceptuel fournit des informations importantes qui sont vraies dans chaque partie du logiciel. Le diagramme de classes dans notre exemple indique que dans chaque implémentation il n’y aura qu’un seul Menu associé à chaque Commande.

  Le fait de dessiner un diagramme de classes d’impératifs aide votre équipe à :

- Définir et normaliser les termes de base employés dans les discussions des besoins des utilisateurs

- Clarifier les relations entre ces termes

  Les rubriques suivantes fournissent des informations supplémentaires :

|Pour en savoir plus sur|Lecture|
|--------------------|----------|
|Informations détaillées sur la recherche de classes d’impératifs|[Diagrammes de classes UML : recommandations](../modeling/uml-class-diagrams-guidelines.md)|
|Éléments d’un diagramme de classes conceptuelles|[Informations de référence sur les diagrammes de classes UML](../modeling/uml-class-diagrams-reference.md)|
|Comment développer du code à partir de classes conceptuelles|[Modéliser l’architecture de votre application](../modeling/model-your-app-s-architecture.md)|

 Dans un diagramme de classes conceptuelles, il est généralement inutile de placer des flèches sur les associations pour représenter la navigabilité. En effet, le diagramme ne représente pas une implémentation. Les associations représentent des relations entre des objets du monde réel. L’Extension [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] suivante applique par défaut des flèches non directionnelles : [Exemple : fonctionnalités de modélisation de domaine UML](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples).

## <a name="BusinessRules"></a> Showing Business Rules
 Une règle métier est un impératif qui n’est associé à aucun cas d’usage particulier et doit être respecté à l’échelle du système.

 De nombreuses règles métier sont des contraintes sur les relations entre les classes conceptuelles. Vous pouvez écrire ces *règles métier statiques* en tant que commentaires associés aux classes pertinentes sur un diagramme de classes conceptuelles. Par exemple :

 ![Règle dans le commentaire joint à la classe Order.](../modeling/media/uml-reqmcd2.png "UML_ReqmCD2")

 Les*règles métier dynamiques* contraignent les séquences d’événements autorisées. Par exemple, vous utilisez un diagramme de séquence ou d’activités pour montrer qu’un utilisateur doit se connecter avant d’effectuer d’autres opérations sur votre système.

 Toutefois, vous pouvez exprimer de nombreuses règles dynamiques plus efficacement et plus génériquement en les remplaçant par des règles statiques. Par exemple, vous pourriez ajouter un attribut booléen « Connecté » à une classe dans le modèle de classes conceptuelles. Vous ajouteriez « Connecté » comme post-condition du cas d’usage Connecté et vous l’ajouteriez comme précondition pour la plupart des autres cas d’usage. Cette approche vous permet d’éviter de définir toutes les combinaisons possibles de séquences d’événements. Elle offre aussi davantage de flexibilité quand vous devez ajouter de nouveaux cas d’usage au modèle.

 Notez qu’ici le choix porte sur la façon dont vous définissez les impératifs et que cette décision est indépendante de la façon dont vous implémentez les impératifs dans le code du programme.

 Les rubriques suivantes fournissent des informations supplémentaires :

|Pour en savoir plus sur|Lecture|
|--------------------|----------|
|Informations détaillées sur la recherche et l’enregistrement des règles métier statiques|[Diagrammes de classes UML : recommandations](../modeling/uml-class-diagrams-guidelines.md)|
|Éléments d’un diagramme de classes conceptuelles|[Informations de référence sur les diagrammes de classes UML](../modeling/uml-class-diagrams-reference.md)|
|Comment développer du code qui respecte des règles métier|[Modéliser l’architecture de votre application](../modeling/model-your-app-s-architecture.md)|

## <a name="QoSRequirements"></a> Describing Quality of Service Requirements
 Il existe plusieurs catégories d’impératifs de qualité de service. Il s'agit des dossiers suivants :

- Performances

- Sécurité

- Facilité d'utilisation

- Fiabilité

- Robustesse

  Vous pouvez inclure certains de ces impératifs dans les descriptions de cas d’usage particuliers. D’autres impératifs ne sont spécifiques à aucun cas d’usage et il est plus efficace de les rédiger dans un document distinct. Dans la mesure du possible, essayez d’adhérer à la terminologie définie par le modèle d’impératifs. Dans l’exemple suivant, notez que les principaux termes utilisés dans l’impératif sont les titres des acteurs, des cas d’usage et des classes des illustrations précédentes :

  Si un Restaurant supprime un Élément de menu pendant qu’un Client Commande un Repas, tout Élément de commande qui fait référence à cet Élément de menu est affiché en rouge.

  Les rubriques suivantes fournissent des informations supplémentaires :

|Pour en savoir plus sur|Lecture|
|--------------------|----------|
|Ajout de documents supplémentaires à des cas d’usage|[Lier un cas d’usage à des documents et diagrammes](../modeling/link-a-use-case-to-documents-and-diagrams.md)|
|Comment développer du code conforme aux impératifs de qualité de service|[Modéliser l’architecture de votre application](../modeling/model-your-app-s-architecture.md)|

## <a name="Workflow"></a>Présentation du workflow de travail entre les utilisateurs et votre système
 Vous pouvez utiliser un diagramme d’activités pour montrer le flux de travail entre différents cas d’usage. Il est souvent utile de commencer un modèle d’impératifs en dessinant un diagramme d’activités qui montre les principales tâches effectuées par les utilisateurs, à la fois dans et en dehors du système.

 Par exemple :

 ![Activité avec trois actions et une boucle.](../modeling/media/uc-reqmwfact.png "UC_ReqmWFAct")

 Vous pouvez dessiner des diagrammes de cas d’usage et des diagrammes d’activités pour montrer différentes vues des mêmes informations.  Le diagramme de cas d’usage convient mieux à l’affichage de l’imbrication de petites actions dans une activité plus grande, mais il ne montre pas le flux de travail. Par exemple :

 ![Cas d’usage pour les actions précédentes](../modeling/media/uml-reqmwfuc.png "UML_ReqmWFUC")

 Notez que vous pouvez aussi utiliser des diagrammes d’activités pour représenter les algorithmes de votre logiciel, mais quand vous utilisez les diagrammes pour le processus d’entreprise, vous vous concentrez sur les actions qui sont visibles en dehors du système.

 Les rubriques suivantes fournissent des informations supplémentaires :

|Pour en savoir plus sur|Lecture|
|--------------------|----------|
|Plus d’informations sur la façon de définir des flux de travail d’entreprise|[Diagrammes d’activités UML : conseils](../modeling/uml-activity-diagrams-guidelines.md)|
|Éléments sur un diagramme d’activités|[Informations de référence sur les diagrammes d’activités UML](../modeling/uml-activity-diagrams-reference.md)|
|Comment développer du code à partir de diagrammes d’activités|[Modéliser l’architecture de votre application](../modeling/model-your-app-s-architecture.md)|

## <a name="Sequences"></a>Montrer les interactions entre les utilisateurs et votre système
 Vous pouvez utiliser un diagramme de séquence pour montrer l’échange de messages entre votre système et des acteurs externes ou entre différentes parties de votre système. Vous obtenez ainsi une vue des étapes dans un cas d’usage qui montre très clairement la séquence d’interactions. Les diagrammes de séquence sont particulièrement utiles quand plusieurs parties interagissent dans un cas d’usage ou quand votre système a une API.

 Par exemple :

 ![Diagramme de séquence avec le système et les acteurs.](../modeling/media/uml-reqmseq.png "UML_ReqmSeq")

 Avec les diagrammes de séquence, il est facile de voir quels messages accèdent au système que vous construisez. Pour concevoir le système, vous pouvez remplacer la ligne de vie Système unique par une ligne de vie distincte pour chacun de ses composants, puis montrer les interactions entre eux en réponse à chaque message entrant.

 Les rubriques suivantes fournissent des informations supplémentaires :

|Pour en savoir plus sur|Lecture|
|--------------------|----------|
|Plus d’informations sur la façon de définir des interactions|[Diagrammes de séquence UML : recommandations](../modeling/uml-sequence-diagrams-guidelines.md)|
|Éléments d’un diagramme de séquence|[Informations de référence sur les diagrammes de séquence UML](../modeling/uml-sequence-diagrams-reference.md)|
|Comment développer du code à partir de diagrammes de séquence|[Modéliser l’architecture de votre application](../modeling/model-your-app-s-architecture.md)|

## <a name="using-a-model-to-reduce-inconsistencies"></a>Utilisation d’un modèle pour réduire les incohérences
 La création d’un modèle entraîne généralement une réduction significative des incohérences et des ambiguïtés quant aux impératifs des utilisateurs. Différentes parties prenantes ont fréquemment une vue différente du monde professionnel dans lequel le système fonctionne. Votre première tâche consiste donc à identifier et éliminer ces différences entre vos clients.

 Vous constaterez que de nombreuses questions relatives au domaine professionnel apparaîtront naturellement lors de la création d’un modèle. En posant ces questions à vos utilisateurs, vous réduirez la nécessité d’apporter des modifications à un stade ultérieur du projet. Voici quelques questions spécifiques que vous pouvez vous poser dans un premier temps, puis poser aux parties prenantes si la réponse n’est pas claire :

- Pour chaque classe du modèle d’impératifs, demandez « Quel cas d’usage crée des instances de cette classe ? ». Par exemple, dans un service en ligne de commande de repas, vous pouvez demander « Quel cas d’usage crée des instances de la classe Menu de restaurant ? ». Cela conduirait à une discussion sur les conditions dans lesquelles un nouveau restaurant s’inscrirait au service et proposerait son menu. Vous pouvez poser des questions similaires concernant ce qui crée ou modifie des attributs et des associations.

- Pour chaque cas d’usage dans le modèle d’impératifs, essayez de décrire le résultat (ou post-condition) de chaque cas d’usage en utilisant des mots fournis par les diagrammes de classes. Il est souvent utile de montrer l’effet d’un cas d’usage en dessinant des instances des classes avant et après une occurrence du cas d’usage. Par exemple, si la post-condition de cas d’usage indique « un élément de menu est ajouté à la commande du client », dessinez des instances des classes Commande et Élément de menu. Montrez les effets du cas d’usage, tel qu’un nouveau lien ou un nouvel objet, avec une couleur différente ou un nouveau dessin. Cela conduit fréquemment à des discussions concernant les informations qui sont nécessaires dans le modèle. Bien que les classes d’impératifs ne soient pas directement concernées par l’implémentation, elles décrivent les informations que votre système devra stocker et transmettre.

- Renseignez-vous sur les contraintes sur les attributs et les associations, en particulier celles impliquant plusieurs attributs ou associations.

- Demandez quelles sont les séquences valides et non valides de cas d’usage, et dessinez des diagrammes de séquence ou d’activités pour les illustrer.

  En examinant les relations entre les vues fournies par différents diagrammes, vous pouvez rapidement comprendre les principaux concepts avec lesquels vos utilisateurs travaillent et les aider à comprendre ce qu’ils ont besoin de la part du système. Vous identifierez aussi plus précisément les impératifs concernant lesquels les parties prenantes ont des doutes. Vous pouvez prévoir de développer ces fonctionnalités, au moins sous une forme simplifiée, à un stade précoce du projet, pour permettre aux utilisateurs d’expérimenter avec elles.

## <a name="see-also"></a>Voir aussi
 [Modifier des modèles et des diagrammes UML](../modeling/edit-uml-models-and-diagrams.md) [Développer des tests à partir d’un modèle](../modeling/develop-tests-from-a-model.md) [Utiliser des modèles dans votre processus de développement](../modeling/use-models-in-your-development-process.md) [Modéliser l’architecture de votre application](../modeling/model-your-app-s-architecture.md) [Exemple d'extension VS : Fonctionnalités de modélisation de domaine UML](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples) [ Exemple d'extension VS : Coloriser les éléments UML par stéréotype](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples) [Exemple d’extension VS : associer des éléments UML à des diagrammes, des fichiers et d’autres éléments exemple d’extension](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples) [Exemple d’extension VS : Aligner des formes dans un diagramme UML](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples) [ Vidéo : Modélisation du domaine professionnel](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain)
