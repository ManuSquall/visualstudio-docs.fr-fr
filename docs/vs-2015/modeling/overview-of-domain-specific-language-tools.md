---
title: Vue d’ensemble des Outils Domain-Specific Language | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 56
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d38aed17d7fdaa694c8c5753705b28b0390dedfc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652144"
---
# <a name="overview-of-domain-specific-language-tools"></a>Vue d'ensemble des outils de langage spécifique à un domaine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les Outils Domain-Specific Language (DSL), qui sont hébergés dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous permettent de concevoir un langage spécifique à un domaine et de générer tout ce que les utilisateurs doivent avoir pour créer des modèles basés sur le langage.

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

  L’Assistant crée une solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] qui contient les projets suivants :

- Dsl

   Le projet Dsl définit le langage spécifique à un domaine et ses outils d’édition et de traitement.

- **DslPackage**

   Le projet DslPackage détermine comment les outils de langage s’intègrent à [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="the-dsl-tools-graphical-interface"></a>Interface graphique des Outils DSL
 Vous pouvez utiliser l’interface graphique des Outils DSL pour ajouter des éléments et des relations à votre langage spécifique à un domaine. Une fois que vous avez ajouté les éléments, vous pouvez définir leur apparence en les mappant à des formes, en personnalisant les couleurs et en ajoutant des éléments décoratifs. Vous pouvez également ajouter les éléments à la boîte à outils.

## <a name="validation-in-dsl-tools"></a>Validation dans les Outils DSL
 DSL offre un niveau de validation pour vous assurer que le modèle de domaine répond aux exigences de base pour générer du code. En règle générale, lorsque vous créez votre propre langage spécifique à un domaine, vous devez ajouter votre propre validation pour exprimer vos règles de logique métier. Pour plus d’informations sur la validation personnalisée, consultez [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md).

 Nous vous recommandons de valider souvent votre langage spécifique à un domaine quand vous le créez. Si votre langage spécifique à un domaine comporte des erreurs de validation, vous ne pouvez pas générer le code source. Le processus de génération de code source à partir des modèles est effectué en cliquant sur **Transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions. Chaque fois que vous modifiez la définition de langage, veillez également à **Transformer tous les modèles**. Pour plus d’informations, consultez [Comment : créer une solution de langage spécifique à un domaine](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Personnalisation des Outils DSL
 Vous pouvez fournir du code supplémentaire pour affiner le comportement du modèle et définir des contraintes sur votre langage. Si nécessaire, vous pouvez apporter des changements significatifs en modifiant les modèles de texte.

## <a name="distributing-your-dsl-solution"></a>Distribution de votre solution DSL
 Les Outils DSL génèrent un package qui est hébergé dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Le package présente une boîte à outils, un explorateur DSL et d’autres éléments d’interface utilisateur qui permettent aux utilisateurs de créer des modèles à l’aide de votre langage spécifique à un domaine.

 Quand vous générez et exécutez la solution Outils DSL dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], une deuxième instance de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vous montre comment votre langage spécifique à un domaine apparaît à l’utilisateur du langage. Après avoir vérifié que tout fonctionne correctement, vous pouvez distribuer le fichier `.vsix` que vous trouverez dans le dossier de génération du projet DslPackage. Vous pouvez utiliser ce fichier pour installer le langage DSL comme extension [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sur d’autres ordinateurs.  Pour plus d’informations, consultez [Déploiement de solutions de langage spécifique à un domaine](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Voir aussi
 [L’instance expérimentale](../extensibility/the-experimental-instance.md) [Outils Domain-specific language Glossaire](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
