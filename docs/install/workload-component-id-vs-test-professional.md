---
title: "ID de composant et de charge de travail de Visual Studio Test Professional 2017 | Microsoft Docs"
description: "Utilisez les ID de composant et de charge de travail de Visual Studio pour fournir des outils de test intégrés pour les testeurs généralistes"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 10/09/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology: vs-ide-install
ms.assetid: 70c03438-8434-4921-ada0-c172519af431
ms.openlocfilehash: 82375aa5b08b3890aa2c615f9d44877ca7fb3a22
ms.sourcegitcommit: 2c7f48ad6073a81fa927568793633f26cc1f0b15
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="visual-studio-test-professional-2017-component-directory"></a>Répertoire des composants Visual Studio Test Professional 2017

Les tableaux de cette page répertorient les ID que vous pouvez utiliser pour installer Visual Studio à l’aide de la ligne de commande. Notez que nous ajouterons des composants supplémentaires lors de la publication de mises à jour de Visual Studio.

En outre, notez ce qui suit concernant cette page :

* Chaque charge de travail possède sa propre section, suivie de l’ID de charge de travail et d’un tableau des composants disponibles pour cette charge de travail.
* Par défaut, les composants **requis** sont installés lorsque vous installez la charge de travail. Si vous le souhaitez, vous pouvez également installer les composants **recommandés** et **facultatifs**.
* Nous avons également ajouté une section qui répertorie les composants supplémentaires qui ne sont affiliés à aucune charge de travail.

Pour plus d’informations sur l’utilisation de ces ID, consultez la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017 RC](use-command-line-parameters-to-install-visual-studio.md). Pour obtenir la liste des ID de charge de travail et de composant des autres produits, consultez la page [ID de composant et de charge de travail de Visual Studio 2017](workload-and-component-ids.md).

## <a name="test-professional"></a>Test Professional

**ID :** Microsoft.VisualStudio.Workload.TestProfessional

**Description :** Test Professional fournit des outils de test intégrés qui répondent aux besoins des testeurs généralistes tout au long du cycle de vie des tests.

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.0.26711.1 | Obligatoire
Microsoft.VisualStudio.Component.TestTools.MicrosoftTestManager | Microsoft Test Manager | 15.0.26606.0 | Obligatoire

## <a name="unaffiliated-components"></a>Composants non affiliés

Il s’agit de composants qui ne sont inclus dans aucune charge de travail, mais qui peuvent être sélectionnés de manière individuelle.

ID de composant | Nom | Version
--- | --- | ---
N/A | N/A | N/A

## <a name="get-support"></a>Obtenir de l’aide
Parfois, des problèmes peuvent se produire. Si votre installation de Visual Studio échoue, consultez la page [Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017](troubleshooting-installation-issues.md) pour obtenir des conseils de dépannage. Vous pouvez également nous signaler des problèmes au niveau d'un produit via l'outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) de l'IDE de Visual Studio, ou nous faire part de vos suggestions sur [UserVoice](https://visualstudio.uservoice.com/forums/121579). Vous pouvez suivre les problèmes au niveau d'un produit sur le site [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), et y poser des questions et obtenir des réponses. Vous pouvez également communiquer avec nous et d'autres développeurs Visual Studio en prenant part à notre [conversation Visual Studio dans la communauté Gitter ](https://gitter.im/Microsoft/VisualStudio) (nécessite un compte [GitHub](https://github.com/)).

## <a name="see-also"></a>Voir aussi

* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md)
* [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)
