---
title: Développer des tests à partir d'un modèle
description: Découvrez comment vous pouvez utiliser les spécifications et les modèles architecturaux pour mieux organiser les tests de votre système et de ses composants.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tests and requirements
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dadffd0a2950d55145b24d3172564eb572f98d70
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389148"
---
# <a name="develop-tests-from-a-model"></a>Développer des tests à partir d'un modèle
Vous pouvez utiliser les spécifications et les modèles architecturaux pour mieux organiser les tests de votre système et de ses composants. Cette pratique vous permet de vous assurer que vous testez les besoins importants des utilisateurs et des autres parties prenantes, et vous aide à mettre rapidement à jour les tests quand les besoins changent. Si vous utilisez [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], vous pouvez également tenir à jour des liens entre les modèles et les tests.

 Pour connaître les versions de Visual Studio qui prennent en charge ces fonctionnalités, consultez [prise en charge des versions pour les outils d’architecture et de modélisation](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

## <a name="system-and-subsystem-testing"></a>Tests système et de sous-systèmes
 Le *test du système,* également appelé *test d’acceptation*, consiste à tester si les besoins des utilisateurs sont satisfaits. Ces tests portent sur le comportement extérieurement visible du système, plutôt que sur sa conception interne.

 Les tests système sont extrêmement utiles lors de l'extension ou de la modification de conception d'un système. Ils vous évitent d'introduire des bogues quand vous modifiez le code.

 Lorsque vous planifiez une modification ou une extension d'un système, il est utile de commencer avec un ensemble de tests système qui s'exécutent sur le système existant. Ensuite, vous pouvez étendre ou adapter les tests pour tester les nouveaux impératifs, apporter les modifications au code et réexécuter l'ensemble complet de tests.

 Quand vous développez un nouveau système, vous pouvez commencer à créer des tests dès le début du développement. Définir des tests avant de développer chaque fonctionnalité vous permet de capturer les discussions d'impératifs d'une manière très spécifique.

 Les tests de sous-systèmes appliquent les mêmes principes aux composants majeurs d'un système. Chaque composant est testé indépendamment des autres composants. Les tests de sous-systèmes sont axés sur le comportement visible au niveau des interfaces utilisateur ou des API du composant.

## <a name="deriving-system-tests-from-a-requirements-model"></a>Dérivation de tests système à partir d'un modèle d'impératifs
 Vous pouvez créer et tenir à jour une relation entre des tests système et un modèle d'impératifs. Pour établir cette relation, vous devez écrire des tests qui correspondent aux principaux éléments du modèle d'impératifs. Visual Studio vous aide à tenir à jour cette relation en vous permettant de créer des liens entre les tests et les parties du modèle. Pour plus d’informations sur les modèles d’impératifs, consultez [Configuration requise](../modeling/model-user-requirements.md)pour les utilisateurs.

### <a name="write-tests-for-each-use-case"></a>Écrire des tests pour chaque cas d'usage
 Si vous utilisez [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], vous pouvez créer un groupe de tests pour chaque cas d'usage que vous avez défini dans votre modèle d'impératifs. Par exemple, si vous avez un cas d'usage Commander un repas, qui comprend Créer une commande et Ajouter un article à la commande, vous pouvez créer des tests à la fois pour le cas d'usage global et pour les cas d'usage plus détaillés.

 Les instructions suivantes peuvent être utiles :

- Chaque cas d'usage doit avoir plusieurs tests, pour les itinéraires principaux et pour les résultats exceptionnels.

- Quand vous décrivez un cas d'usage dans le modèle d'impératifs, il est plus important de définir sa post-condition, autrement dit l'objectif atteint, que de décrire en détail les procédures suivies par l'utilisateur pour atteindre l'objectif. Par exemple, la post-condition de Commander un repas pourrait être qu'un Restaurant a préparé un repas pour un Client et que le client a payé. La post-condition correspond aux critères que vos tests doivent vérifier.

- Basez des tests distincts sur les clauses distinctes de la post-condition. Par exemple, créez des tests distincts pour informer le restaurant de la commande et pour recevoir le paiement du client. Cette séparation offre les avantages suivants :

  - Les modifications de différents aspects des impératifs se produisent souvent indépendamment. En séparant les tests en différents aspects de cette manière, vous simplifiez la mise à jour des tests en cas de modification des impératifs.

  - Si le plan de développement implémente un aspect du cas d'usage avant un autre, vous pouvez activer les tests séparément à mesure que le développement progresse.

- Lors de la conception des tests, séparez le choix des données de test du code ou du script qui détermine si la post-condition a été remplie. Par exemple, voici un exemple de test d'une fonction arithmétique simple : entrer 4, vérifier que la sortie est 2. Au lieu de cela, concevez le script comme suit : choisir une entrée, multiplier le résultat par lui-même et vérifier que le résultat est l'entrée d'origine. Ce style vous permet de faire varier les entrées de test sans modifier le corps principal du test.

#### <a name="linking-tests-to-use-cases"></a>Liaison de tests à des cas d'usage
 Si vous utilisez [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] pour concevoir et exécuter vos tests, vous pouvez organiser vos tests sous les éléments de travail spécification, cas d’utilisation ou récit utilisateur. Vous pouvez lier ces éléments de travail à des cas d'usage dans votre modèle. Cela vous permet d'effectuer un suivi rapide des modifications d'impératifs lors des tests et vous aide à suivre la progression de chaque cas d'usage.

###### <a name="to-link-tests-to-a-use-case"></a>Pour lier des tests à un cas d'usage

1. Dans [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], créez un impératif et basez une suite de tests dessus.

    L'impératif que vous créez est un élément de travail dans [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Il peut s’agir d’un élément de travail récit utilisateur, spécification ou cas d’usage, selon le modèle de processus utilisé par votre projet avec Team Foundation. Pour plus d’informations, consultez [à propos des outils agile et gestion de projet agile](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true).

2. Liez l'élément de travail Spécification à un ou plusieurs cas d'usage dans votre modèle.

    Dans un diagramme de cas d’usage, cliquez avec le bouton droit sur un cas d’usage, puis cliquez sur **lier à l’élément de travail**.

3. Ajoutez à la suite de tests des cas de test qui vérifient les cas d'usage.

   En général, chaque élément de travail Récit utilisateur ou Spécification est lié à plusieurs cas d'usage dans votre modèle et chaque cas d'usage est lié à plusieurs spécifications ou récits utilisateur. Cela est dû au fait que chaque récit utilisateur ou spécification couvre un ensemble de tâches qui développent plusieurs cas d'usage. Par exemple, lors d'une itération précoce de votre projet, vous pourriez développer le récit utilisateur de base selon lequel un client peut sélectionner des articles dans un catalogue et se les faire livrer. Lors d'une itération ultérieure, le récit pourrait préciser que l'utilisateur paie à la fin de la commande et que le fournisseur reçoit la somme payée après avoir envoyé la marchandise.  Chaque récit ajoute une clause à la post-condition du cas d'usage Commander des biens.

   Vous pouvez créer des liens séparés entre les spécifications et les clauses de la post-condition en écrivant ces clauses dans des commentaires distincts dans le diagramme de cas d'usage. Vous pouvez lier chaque commentaire à un élément de travail Spécification et le lier au cas d'usage dans le diagramme.

### <a name="base-tests-on-the-requirements-types"></a>Tests de base sur les types de spécifications
 Les types (c'est-à-dire les classes, les interfaces et les énumérations) d'un modèle d'impératifs décrivent les concepts et les relations d'après la façon dont les utilisateurs pensent et communiquent leur activité professionnelle. Cela exclut les types axés exclusivement sur la conception interne du système.

 Vous devez concevoir vos tests par rapport à ces types d'impératifs. Cette pratique vous permet de vous assurer que lors de la discussion des changements d'impératifs il est facile d'associer ces changements aux modifications de tests nécessaires. Cela permet de discuter des tests et de leurs résultats prévus directement avec les utilisateurs finaux et les autres parties prenantes. Cela signifie que vous pouvez gérer les besoins des utilisateurs en dehors du processus de développement et évite de concevoir involontairement les tests autour de failles possibles dans la conception.

 Pour les tests manuels, cette pratique implique le respect du vocabulaire du modèle d'impératifs dans les scripts de tests. Pour les tests automatisés, cette pratique implique l'utilisation des diagrammes de classes d'impératifs comme base pour votre code de test et la création de fonctions d'accès et de mise à jour pour lier le modèle d'impératifs au code.

 Par exemple, un modèle d'impératifs peut inclure les types Menu, Élément de menu, Commande et des associations entre ces types. Ce modèle représente les informations stockées et traitées par le système de commande de repas, mais ne représente pas les complexités de son implémentation. Dans le système opérationnel, il peut y avoir plusieurs réalisations différentes de chaque type, dans des bases de données, dans des interfaces utilisateur et dans des API. Dans un système distribué, il peut exister plusieurs variantes de chaque instance stockées simultanément dans différentes parties du système.

 Pour tester un cas d'usage tel que Ajouter un article à la commande, une méthode de test peut inclure du code semblable au suivant :

```
Order order = ... ; // set up an order
// Store prior state:
int countBefore = order.MenuItems.Count;
// Perform use case:
MenuItem chosenItem = ...; // choose an item
AddItemToOrder (chosenItem, order);
// Verify part of postcondition:
int countAfter = order.MenuItems.Count;
Assert (countAfter == countBefore = 1);
```

 Notez que cette méthode de test utilise les classes du modèle d'impératifs. Les associations et les attributs sont réalisés en tant que propriétés .NET.

 Pour cela, les propriétés des classes doivent être définies en tant que fonctions ou accesseurs en lecture seule, qui accèdent au système pour récupérer des informations sur son état actuel. Les méthodes qui simulent des cas d'usage, telles que AddItemToOrder, doivent faire passer le système via son API ou une couche située en dessous de son interface utilisateur. Les constructeurs d'objets de test tels que Order et MenuItem doivent aussi piloter le système pour créer des éléments correspondants dans le système.

 Une grande partie des accesseurs et des programmes de mise à jour seront déjà disponibles via l'API normale de l'application, mais vous devrez peut-être écrire certaines fonctions supplémentaires pour activer les tests. Ces accesseurs et programmes de mise à jour supplémentaires sont parfois appelés « instrumentation de test ». Comme ils dépendent de la conception interne du système, il incombe aux développeurs du système de les fournir, tandis que les testeurs écrivent le code des tests conformément au modèle d'impératifs.

 Quand vous écrivez des tests automatisés, vous pouvez utiliser des tests génériques pour encapsuler les accesseurs et les programmes de mise à jour.

### <a name="tests-for-business-rules"></a>Tests de règles métier
 Certains impératifs ne sont directement liés à aucun cas d'usage. Par exemple, l'entreprise DinnerNow permet aux clients de choisir parmi de nombreux Menus, mais elle exige que dans chaque Commande, tous les Éléments choisis proviennent d'un même Menu. Cette règle métier peut être exprimée comme un invariant relatifs aux associations entre Commandes, Menus et Éléments dans le modèle de classes d'impératifs.

 Une règle invariante de ce genre régit non seulement tous les cas d'usage actuellement définis, mais aussi les autres cas d'usage qui seront définis ultérieurement. Ainsi, il est utile de l'écrire et de la tester séparément de tout cas d'usage.

## <a name="deriving-subsystem-tests-from-models"></a>Dérivation de tests de sous-systèmes à partir de modèles
 Dans la conception globale d'un grand système, vous pouvez identifier les composants ou les sous-systèmes. Ils représentent des parties qui peuvent être conçues séparément, qui se trouvent sur des ordinateurs différents ou qui sont des modules réutilisables pouvant être recombinés de plusieurs manières.

 Vous pouvez appliquer à chaque composant majeur les mêmes principes que ceux utilisés pour l'ensemble du système. Dans un grand projet, chaque composant peut avoir son propre modèle d'impératifs. Dans les projets plus petits, vous pouvez créer un modèle d'architecture ou une conception globale pour montrer les principaux composants et leurs interactions. Pour plus d’informations, consultez [modéliser l’architecture de votre application](../modeling/model-your-app-s-architecture.md).

 Dans les deux cas, vous pouvez établir une relation entre les éléments de modèle et les tests de sous-systèmes comme vous le feriez entre le modèle d'impératifs et les tests système.

### <a name="isolate-components-with-provided-and-required-interfaces"></a>Isoler des composants avec des interfaces fournies et requises
 Il est utile d'identifier toutes les dépendances d'un composant envers d'autres parties de votre système ou envers des services externes et de les représenter en tant qu'Interfaces requises. Cet exercice entraîne généralement une modification de la conception qui rend le composant bien plus découplé et aisément séparable du reste de votre conception.

 L'un des avantages de ce découplage est que vous pouvez tester le composant en remplaçant les services qu'il utilise habituellement par des objets fictifs. Il s'agit de composants qui sont configurés pour les besoins des tests. Un composant fictif fournit l'interface dont votre composant a besoin et répond aux requêtes avec des données simulées. Les composants fictifs font partie d'un atelier de test complet que vous pouvez connecter à toutes les interfaces du composant.

 L'un des avantages des tests fictifs est que vous pouvez développer votre composant pendant que les autres composants dont il utilisera les services sont en cours de développement.

## <a name="maintain-the-relationships-between-tests-and-model"></a>Gérer les relations entre les tests et le modèle
 Dans un projet classique qui effectue une itération toutes les deux ou trois semaines, un examen des impératifs a lieu au début de chaque itération. Durant cette réunion, vous discutez des fonctionnalités qui doivent être délivrées lors de l'itération suivante. Vous pouvez utiliser un modèle d'impératifs pour faciliter la discussion des concepts, des scénarios et des séquences d'actions qui seront développés. Les parties prenantes définissent des priorités, les développeurs réalisent des évaluations et les testeurs s'assurent que le comportement attendu de chaque fonctionnalité est capturé correctement.

 L'écriture de tests constitue le moyen le plus efficace de définir un impératif et permet également de bénéficier d'une vision claire de ce qui est exigé. Toutefois, alors que l'écriture de tests prend trop de temps au cours d'un atelier d'impératifs, la création de modèles peut être effectuée plus rapidement.

 Du point de vue des tests, un modèle d'impératifs peut être considéré comme un raccourci pour les tests. Ainsi, il est important de maintenir la relation entre les tests et le modèle tout au long du projet.

## <a name="attaching-test-cases-to-model-elements"></a><a name="Attaching"></a> Attacher des cas de test à des éléments de modèle
 Si votre projet utilise [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], vous pouvez lier des tests aux éléments de votre modèle. Cela vous permet d'identifier rapidement les tests affectés par une modification des impératifs et de suivre dans quelle mesure un impératif a été satisfait.

 Vous pouvez lier des tests à tous les types d'éléments. Voici quelques exemples :

- Lier un cas d'usage aux tests qui l'utilisent.

- Écrire les clauses d'une post-condition de cas d'usage, ou objectif, dans les commentaires associés au cas d'usage, puis lier des tests à chaque commentaire.

- Écrire des règles invariantes dans des commentaires dans les diagrammes de classes ou d'activités et les lier à des tests.

- Lier des tests à un diagramme d'activités ou à des activités spécifiques.

- Lier une suite de tests au composant ou au sous-système qu'elle teste.

#### <a name="to-link-tests-to-a-model-element-or-relationship"></a>Pour lier des tests à un élément de modèle ou à une relation

1. Dans [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], créez un impératif et basez une suite de tests dessus.

    L'impératif que vous créez est un élément de travail dans [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Il peut s’agir d’un élément de travail récit utilisateur, spécification ou cas d’usage, selon le modèle de processus utilisé par votre projet avec Team Foundation. Pour plus d’informations, consultez [à propos des outils agile et gestion de projet agile](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true).

2. Liez l'élément de travail Spécification à un ou plusieurs éléments dans votre modèle.

    Dans un diagramme de modélisation, cliquez avec le bouton droit sur un élément, un commentaire ou une relation, puis cliquez sur **lier à l’élément de travail**.

3. Ajoutez à la suite de tests des cas de test qui vérifient l'impératif exprimé dans l'élément de modèle.

## <a name="see-also"></a>Voir aussi

- [Créer des modèles pour votre application](../modeling/create-models-for-your-app.md)
- [Modéliser les besoins des utilisateurs](../modeling/model-user-requirements.md)
- [Modéliser l’architecture de votre application](../modeling/model-your-app-s-architecture.md)
- [Analyse et modélisation de l’architecture](../modeling/analyze-and-model-your-architecture.md)
