---
title: ID de composant et de charge de travail de Visual Studio Test Controller 2017 | Microsoft Docs
description: "Utiliser les ID de composant et de charge de travail Visual Studio pour distribuer des tests automatisés sur plusieurs machines"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 05/10/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
ms.assetid: fbbda9c8-d2c6-474d-b52d-a95227d52fe7
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: a9b33db2ba10b9a1e4c85a8caf17345f21a057b2
ms.contentlocale: fr-fr
ms.lasthandoff: 05/13/2017

---

# <a name="visual-studio-test-controller-2017-component-directory"></a>Répertoire des composants Visual Studio Test Controller 2017

Les tableaux de cette page listent les ID que vous pouvez utiliser pour installer Visual Studio à l’aide de la ligne de commande. Notez que nous ajouterons des composants supplémentaires lors de la publication de mises à jour de Visual Studio.

En outre, notez ce qui suit concernant la page :

* Chaque charge de travail possède sa propre section, suivie de l’ID de charge de travail et d’une table des composants disponibles pour cette charge.
* Par défaut, les composants **requis** sont installés lorsque vous installez la charge de travail. Si vous le souhaitez, vous pouvez également installer les composants **recommandés** et **facultatifs**.
* Nous avons également ajouté une section qui répertorie les composants supplémentaires qui ne sont affiliés à aucune charge de travail.

Pour plus d’informations sur l’utilisation de ces ID, consultez la page [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017 RC](use-command-line-parameters-to-install-visual-studio.md). Pour obtenir la liste des ID de charge de travail et de composant triés des autres produits, consultez la page [ID de composant et de charge de travail de Visual Studio 2017](workload-and-component-ids.md).

## <a name="test-controller"></a>Test Controller

**ID :** Microsoft.VisualStudio.Workload.TestController

**Description :** Distribuer des tests automatisés sur plusieurs ordinateurs

### <a name="components-included-by-this-workload"></a>Composants inclus par cette charge de travail

ID de composant | Nom | Version | Type de dépendance
--- | --- | --- | ---
Microsoft.VisualStudio.ComponentGroup.TestTools.TestController | Fonctionnalités principales de Test Controller | 15.0.26208.0 | Obligatoire
## <a name="unaffiliated-components"></a>Composants non affiliés

Il s’agit de composants qui ne sont inclus dans aucune charge de travail, mais qui peuvent être sélectionnés de manière individuelle.

ID de composant | Nom | Version
--- | --- | ---
N/A | N/A | N/A

## <a name="see-also"></a>Voir aussi

* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md)
* [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)

