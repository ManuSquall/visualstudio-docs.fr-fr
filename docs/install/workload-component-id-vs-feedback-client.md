---
title: ID de composant et de charge de travail de Visual Studio Feedback Client
titleSuffix: ''
description: Utiliser les ID de composant et de charge de travail Visual Studio pour fournir un feedback détaillé pour Azure DevOps Services ou Team Foundation Server
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: 7392a100-100c-458c-9394-828695109015
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
open_to_public_contributors: false
ms.openlocfilehash: f83b457582124658285e0769d1907a8643d44fda
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881761"
---
# <a name="visual-studio-feedback-client-component-directory"></a>Répertoire des composants Visual Studio Feedback Client

Les tableaux de cette page répertorient les ID que vous pouvez utiliser pour installer Visual Studio à l’aide de la ligne de commande ou que vous pouvez spécifier en tant que dépendance dans un manifeste VSIX. Notez que nous ajouterons des composants supplémentaires lors de la publication de mises à jour de Visual Studio.

En outre, notez ce qui suit concernant la page :

* Chaque charge de travail possède sa propre section, suivie de l’ID de charge de travail et d’une table des composants disponibles pour cette charge.
* Par défaut, les composants **requis** sont installés lorsque vous installez la charge de travail.
* Si vous le souhaitez, vous pouvez également installer les composants **recommandés** et **facultatifs**.
* Nous avons également ajouté une section qui répertorie les composants supplémentaires qui ne sont affiliés à aucune charge de travail.

Lorsque vous définissez des dépendances dans votre manifeste VSIX, vous devez spécifier les ID de composant uniquement. Utilisez les tableaux de cette page pour déterminer les dépendances minimum des composants. Dans certains scénarios, cela peut vouloir dire que vous ne spécifiez qu’un composant à partir d’une charge de travail. Dans d’autres, cela peut vouloir dire que vous spécifiez plusieurs composants à partir d’une charge de travail unique ou plusieurs composants à partir de plusieurs charges de travail. Pour plus d’informations, consultez la page [Guide pratique pour migrer les projets d’extensibilité vers Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

Pour plus d’informations sur l’utilisation de ces ID, consultez la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017 RC](use-command-line-parameters-to-install-visual-studio.md). Pour obtenir la liste des ID de charge de travail et de composant triés des autres produits, consultez la page [ID de composant et de charge de travail de Visual Studio 2017](workload-and-component-ids.md).

## <a name="feedback-client"></a>Feedback Client

**ID :** Microsoft.VisualStudio.Workload.FeedbackClient

**Description :** Feedback Client permet de fournir un feedback détaillé pour Azure DevOps Services ou Team Foundation Server.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Outil de Feedback Microsoft | 15.6.27406.0 | Obligatoire

## <a name="unaffiliated-components"></a>Composants non affiliés

Il s’agit de composants qui ne sont inclus dans aucune charge de travail, mais qui peuvent être sélectionnés de manière individuelle.

ID de composant | Nom | Version
--- | --- | ---
n/a | n/a | n/a

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md)
* [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)
