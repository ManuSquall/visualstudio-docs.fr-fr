---
title: ID de composant et de charge de travail de Visual Studio Team Explorer 2017
titleSuffix: ''
description: Utilisez les ID de composant et de charge de travail de Visual Studio pour fournir des outils de test intégrés pour les testeurs généralistes
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.prod: visual-studio-dev15
ms.assetid: c6ef9a3b-d13d-49b4-9faa-51fa06b21e1f
ms.workload:
- multiple
ms.openlocfilehash: 694085412a674731934ac75d62bd2c904e3c7176
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860216"
---
# <a name="visual-studio-team-explorer-2017-component-directory"></a>Répertoire des composants Visual Studio Team Explorer 2017

Les tableaux de cette page répertorient les ID que vous pouvez utiliser pour installer Visual Studio à l’aide de la ligne de commande ou que vous pouvez spécifier en tant que dépendance dans un manifeste VSIX. Notez que nous ajouterons des composants supplémentaires lors de la publication de mises à jour de Visual Studio.

En outre, notez ce qui suit concernant la page :

* Chaque charge de travail possède sa propre section, suivie de l’ID de charge de travail et d’une table des composants disponibles pour cette charge.
* Par défaut, les composants **requis** sont installés lorsque vous installez la charge de travail.
* Si vous le souhaitez, vous pouvez également installer les composants **recommandés** et **facultatifs**.
* Nous avons également ajouté une section qui répertorie les composants supplémentaires qui ne sont affiliés à aucune charge de travail.

Lorsque vous définissez des dépendances dans votre manifeste VSIX, vous devez spécifier les ID de composant uniquement. Utilisez les tableaux de cette page pour déterminer les dépendances minimum des composants. Dans certains scénarios, cela peut vouloir dire que vous ne spécifiez qu’un composant à partir d’une charge de travail. Dans d’autres, cela peut vouloir dire que vous spécifiez plusieurs composants à partir d’une charge de travail unique ou plusieurs composants à partir de plusieurs charges de travail. Pour plus d’informations, consultez la page [Guide pratique pour migrer les projets d’extensibilité vers Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

Pour plus d’informations sur l’utilisation de ces ID, consultez la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017 RC](use-command-line-parameters-to-install-visual-studio.md). Pour obtenir la liste des ID de charge de travail et de composant triés des autres produits, consultez la page [ID de composant et de charge de travail de Visual Studio 2017](workload-and-component-ids.md).

## <a name="visual-studio-core-editor-included-with-visual-studio-team-explorer-2017"></a>Éditeur de base de Visual Studio (fourni avec Visual Studio Team Explorer 2017)

**ID :** Microsoft.VisualStudio.Workload.CoreEditor

**Description :** Utilisation de l’interpréteur de commandes de base Visual Studio, modification du code avec prise en charge de la syntaxe, contrôle de code source et gestion des éléments de travail.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Name | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Éditeur de base de Visual Studio | 15.8.27729.1 | Obligatoire
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Page de démarrage de Visual Studio pour les utilisateurs C++ | 15.0.27128.1 | Facultatif

## <a name="unaffiliated-components"></a>Composants non affiliés

Il s’agit de composants qui ne sont inclus dans aucune charge de travail, mais qui peuvent être sélectionnés de manière individuelle.

ID de composant | Name | Version
--- | --- | ---
N/A | N/A | N/A

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md)
* [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)
