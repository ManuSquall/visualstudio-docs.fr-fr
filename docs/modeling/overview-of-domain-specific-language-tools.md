---
title: Vue d'ensemble des outils de langage spécifique à un domaine
description: Découvrez comment les outils DSL vous permettent de concevoir un langage spécifique à un domaine, puis de générer tout ce que les utilisateurs doivent avoir pour créer des modèles basés sur la langue.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 004c9929b33878359fa23735189d60939953755a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390904"
---
# <a name="overview-of-domain-specific-language-tools"></a>Vue d'ensemble des outils de langage spécifique à un domaine
Les outils de langage d' Domain-Specific (outils DSL), qui sont hébergés dans Visual Studio, vous permettent de concevoir un langage spécifique à un domaine, puis de générer tout ce que les utilisateurs doivent avoir pour créer des modèles basés sur la langue.

 Les outils suivants se trouvent dans les Outils DSL :

- Un Assistant de projet qui utilise différents modèles de solution pour vous aider à commencer à développer votre langage spécifique à un domaine.

- Un concepteur graphique pour créer et modifier la définition de votre langage spécifique à un domaine.

- Un moteur de validation qui permet de s’assurer que la définition du langage spécifique à un domaine est correctement formée et qui affiche les erreurs et les avertissements en cas de problèmes.

- Un générateur de code qui prend une définition de langage spécifique à un domaine comme entrée et génère le code source comme sortie.

## <a name="the-dsl-tools-solution"></a>Solution des Outils DSL
 L’Assistant Concepteur Domain-Specific Language fournit les modèles de solution suivants :

- Flux de tâches

- Diagrammes de classes

- Langage minimal

- Modèles de composant

- WPF minimal

- Windows.Forms minimal

- Bibliothèque DSL

  Pour plus d’informations, consultez [Choix d'un modèle de solution de langage spécifique à un domaine](../modeling/choosing-a-domain-specific-language-solution-template.md).

  L’Assistant crée une solution Visual Studio qui contient les projets suivants :

- Dsl

   Le projet Dsl définit le langage spécifique à un domaine et ses outils d’édition et de traitement.

- **DslPackage**

   Le projet DslPackage détermine la façon dont les outils de langage s’intègrent à Visual Studio.

## <a name="the-dsl-tools-graphical-interface"></a>Interface graphique des Outils DSL
 Vous pouvez utiliser l’interface graphique des Outils DSL pour ajouter des éléments et des relations à votre langage spécifique à un domaine. Une fois que vous avez ajouté les éléments, vous pouvez définir leur apparence en les mappant à des formes, en personnalisant les couleurs et en ajoutant des éléments décoratifs. Vous pouvez également ajouter les éléments à la boîte à outils.

## <a name="validation-in-dsl-tools"></a>Validation dans les Outils DSL
 DSL offre un niveau de validation pour vous assurer que le modèle de domaine répond aux exigences de base pour générer du code. En règle générale, lorsque vous créez votre propre langage spécifique à un domaine, vous devez ajouter votre propre validation pour exprimer vos règles de logique métier. Pour plus d’informations sur la validation personnalisée, consultez [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md).

 Nous vous recommandons de valider souvent votre langage spécifique à un domaine quand vous le créez. Si votre langage spécifique à un domaine comporte des erreurs de validation, vous ne pouvez pas générer le code source. Le processus de génération de code source à partir des modèles est effectué en cliquant sur **Transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions. Chaque fois que vous modifiez la définition de langage, veillez également à **Transformer tous les modèles**. Pour plus d’informations, consultez [Comment : créer une solution de langage Domain-Specific](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Personnalisation des Outils DSL
 Vous pouvez fournir du code supplémentaire pour affiner le comportement du modèle et définir des contraintes sur votre langage. Si nécessaire, vous pouvez apporter des changements significatifs en modifiant les modèles de texte.

## <a name="distributing-your-dsl-solution"></a>Distribution de votre solution DSL
 Les outils DSL génèrent un package qui est hébergé dans Visual Studio. Le package présente une boîte à outils, un explorateur DSL et d’autres éléments d’interface utilisateur qui permettent aux utilisateurs de créer des modèles à l’aide de votre langage spécifique à un domaine.

 Quand vous générez et exécutez la solution d’outils DSL dans Visual Studio, une deuxième instance de Visual Studio vous indique comment votre langage spécifique à un domaine est l’utilisateur du langage. Après avoir vérifié que tout fonctionne correctement, vous pouvez distribuer le fichier `.vsix` que vous trouverez dans le dossier de génération du projet DslPackage. Ce fichier peut être utilisé pour installer le DSL comme une extension Visual Studio sur d’autres ordinateurs.  Pour plus d’informations, consultez [Déploiement de solutions de langage spécifique à un domaine](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Voir aussi

- [Instance expérimentale](../extensibility/the-experimental-instance.md)
- [Glossaire des Outils Domain-Specific Language](/previous-versions/bb126564(v=vs.100))