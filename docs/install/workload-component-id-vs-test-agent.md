---
title: "ID de composant et de charge de travail de Visual Studio Test Agent 2017 | Microsoft Docs"
description: "Utiliser les ID de composant et de charge de travail de Visual Studio pour exécuter des tests automatisés et de chargement à distance"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 03/07/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
ms.assetid: 55aea29b-1066-4e5a-aa99-fc87d4efb6d5
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 9e635a28d3338bcf518a0aec69c476280eedf6e2
ms.openlocfilehash: 06ed56b985123bf0af56377d271d5d33f6c37d0e
ms.lasthandoff: 03/27/2017

---

# <a name="visual-studio-test-agent-2017-component-directory"></a>Répertoire des composants Visual Studio Test Agent 2017

Les tables de cette page répertorient les ID que vous pouvez utiliser pour installer Visual Studio à l’aide de la ligne de commande. Notez que nous ajouterons des composants supplémentaires lors de la publication de mises à jour de Visual Studio.

En outre, notez ce qui suit concernant la page :

* Chaque charge de travail possède sa propre section, suivie de l’ID de charge de travail et d’une table des composants disponibles pour cette charge.
* Par défaut, les composants **requis** sont installés lorsque vous installez la charge de travail. Si vous le souhaitez, vous pouvez également installer les composants **recommandés** et **facultatifs**.
* Nous avons également ajouté une section qui répertorie les composants supplémentaires qui ne sont affiliés à aucune charge de travail.

Pour plus d’informations sur l’utilisation de ces ID, consultez la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017 RC](use-command-line-parameters-to-install-visual-studio.md). Pour obtenir la liste des ID de charge de travail et de composant triés des autres produits, consultez la page [Visual Studio 2017 Workload and Component IDs](workload-and-component-ids.md) (ID de composant et de charge de travail de Visual Studio 2017).

## <a name="test-agent"></a>Agent de test

**ID :** Microsoft.VisualStudio.Workload.TestAgent

**Description :** prend en charge l’exécution de tests automatisés et de tests de chargement à distance

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Type de dépendance
--- | --- | ---
Microsoft.VisualStudio.ComponentGroup.TestTools.TestAgent | Fonctionnalités principales de Test Agent | Obligatoire
## <a name="unaffiliated-components"></a>Composants non affiliés

Il s’agit de composants qui ne sont inclus dans aucune charge de travail, mais qui peuvent être sélectionnés de manière individuelle.

ID de composant | Nom
--- | ---
N/A | N/A

## <a name="see-also"></a>Voir aussi

* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)

