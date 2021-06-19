---
title: Générer et configurer votre application à partir de modèles
description: Découvrez ce que représente un modèle et comment vous pouvez générer ou configurer des parties de votre application à partir d’un modèle.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 68339159ed9926490f22a82cd30ce69f45ab6a30
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388865"
---
# <a name="generate-and-configure-your-app-from-models"></a>Générer et configurer votre application à partir de modèles
Vous pouvez générer ou configurer certaines parties de votre application à partir d'un modèle.

 Il représente les impératifs plus directement que le code. En dérivant le comportement de l'application directement à partir du modèle, vous pouvez répondre aux changements d'impératifs avec beaucoup plus de rapidité et de fiabilité que par la mise à jour du code. Bien qu'un travail initial soit nécessaire pour configurer la dérivation, cet investissement est rentable si vous prévoyez que les impératifs changeront ou si vous envisagez de créer plusieurs variantes du produit.

## <a name="generating-the-code-of-your-application-from-a-model"></a>Génération du code de votre application à partir d'un modèle
 Pour générer du code, le plus simple consiste à utiliser des modèles de texte. Vous pouvez générer du code dans la même solution Visual Studio que celle dans laquelle vous conservez le modèle. Pour plus d'informations, consultez les pages suivantes :

- [Génération de code durant la conception à l'aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

- [Génération de code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md)

  Cette méthode est facile à appliquer de façon incrémentielle. Commencez avec une application qui fonctionne uniquement pour un cas spécifique, puis choisissez-en certaines parties que vous souhaitez modifier par rapport au modèle. Renommez les fichiers sources de ces parties pour qu'elles deviennent des fichiers de modèle de texte (.tt). À ce stade, les fichiers .cs sources seront générés automatiquement à partir des fichiers de modèle. L'application fonctionnera donc comme auparavant.

  Vous pouvez ensuite prendre une partie du code et la remplacer par une expression de modèle de texte, qui lit le modèle et génère cette partie du fichier source. Au moins une valeur du modèle doit générer la source d'origine pour que vous puissiez à nouveau exécuter l'application et qu'elle fonctionne comme avant. Après avoir testé différentes valeurs de modèle, vous pouvez insérer des expressions de modèle dans une autre partie du code.

  Grâce à cette méthode incrémentielle, la génération de code est habituellement une approche peu risquée. Les performances des applications qui en résultent sont généralement presque aussi élevées que celles des versions écrites manuellement.

  Toutefois, si vous commencez avec une application existante, vous constaterez peut-être que de nombreuses opérations de refactorisation sont nécessaires pour séparer les différents comportements régis par le modèle, pour qu'ils puissent varier indépendamment. Nous vous recommandons d'évaluer cet aspect de l'application lors de l'estimation du coût de votre projet.

## <a name="configuring-your-application-from-a-model"></a>Configuration de votre application à partir d'un modèle
 Si vous souhaitez faire varier le comportement de votre application au moment de l'exécution, vous ne pouvez pas utiliser la génération de code, qui génère le code source avant que l'application soit compilée. Au lieu de cela, vous pouvez concevoir votre application pour lire le modèle et faire varier son comportement en conséquence. Pour plus d'informations, consultez les pages suivantes :

- [Comment : ouvrir un modèle depuis un fichier dans le code de programme](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  Vous pouvez aussi appliquer cette méthode de façon incrémentielle, mais davantage de travail est nécessaire au début. Vous devez écrire le code qui lit le modèle et configurer une infrastructure qui permet à ses valeurs d'être accessibles aux parties variables. Le fait de rendre les parties variables génériques est plus coûteux que la génération de code.

  Les performances d'une application générique sont généralement moins bonnes que celles de ses homologues spécifiques. Si les performances sont essentielles, votre plan de projet doit inclure une évaluation de ce risque.

## <a name="developing-a-derived-application"></a>Développement d'une application dérivée
 Voici quelques consignes générales qui pourront vous être utiles.

- **Démarrez spécifique, puis généralisez.** Écrivez tout d'abord une version spécifique de votre application. Cette version doit fonctionner dans un ensemble de conditions. Une fois satisfait de son bon fonctionnement, vous pouvez faire en sorte que certaines parties dérivent d'un modèle. Étendez progressivement les parties dérivées.

     Par exemple, concevez un site Web avec un ensemble spécifique de pages Web avant de concevoir une application Web qui présente des pages définies dans un modèle.

- **Modélisez les aspects variants.** Identifiez les aspects qui varieront, soit d'un déploiement à un autre, soit dans le temps à mesure que les impératifs changeront. Il s'agit des aspects qui doivent être dérivés d'un modèle.

     Par exemple, si l’ensemble de pages Web et les liens entre eux changent, mais que le style et le format des pages sont toujours identiques, le modèle doit décrire les liens, mais il n’est pas nécessaire de décrire le format des pages.

- **Des préoccupations distinctes.** Si les aspects variables peuvent être divisés en zones indépendantes, utilisez des modèles distincts pour chaque zone. Avec ModelBus, vous pouvez définir des opérations qui affectent à la fois les modèles et les contraintes entre eux.

     Par exemple, utilisez un modèle pour définir la navigation entre les pages Web et un autre modèle pour définir la disposition des pages.

- **Modélisez les impératifs, et non la solution.** Concevez le modèle afin qu’il décrive les besoins des utilisateurs. En revanche, ne concevez pas la notation en fonction des aspects variables de l'implémentation.

     Par exemple, le modèle de navigation Web doit représenter des pages Web et des liens hypertexte entre eux. Le modèle de navigation Web ne doit pas représenter des fragments de classes HTML ou de classes dans votre application.

- **Générer ou interpréter ?** Si les impératifs d'un déploiement particulier ne changeront que rarement, générez le code de programme à partir du modèle. Si les impératifs peuvent changer fréquemment ou coexister dans plusieurs variantes dans le même déploiement, écrivez l'application pour qu'elle puisse lire et interpréter un modèle.

     Par exemple, si vous utilisez votre modèle de site Web pour développer une série de sites Web différents et installés séparément, vous devez générer le code du site à partir du modèle. Mais si vous utilisez votre modèle pour contrôler un site qui change chaque jour, il est préférable d’écrire un serveur Web qui lit le modèle et présente le site en conséquence.

- **UML ou DSL ?** Vous pouvez créer votre notation de modélisation à l'aide de stéréotypes pour étendre UML. Définissez un diagramme DSL s'il n'existe aucun diagramme UML adapté. Évitez toutefois de compromettre la sémantique standard UML.

     Par exemple, un diagramme de classes UML est une collection de cases et de flèches ; avec cette notation, vous pouvez théoriquement définir n'importe quoi. Cependant, nous vous déconseillons d'utiliser le diagramme de classes, sauf quand vous décrivez réellement un ensemble de types. Par exemple, vous pouvez adapter des diagrammes de classes pour décrire différents types de pages Web.

## <a name="see-also"></a>Voir aussi

- [Génération de code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md)
- [Comment : ouvrir un modèle depuis un fichier dans le code de programme](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Génération de code durant la conception à l'aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
