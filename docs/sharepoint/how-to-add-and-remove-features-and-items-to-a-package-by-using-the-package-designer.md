---
title: 'Concepteur de packages : Ajouter & supprimer des fonctionnalités et des éléments dans le package'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerDesign
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 86dde3abc86ff42d2e558626abdb5faee7e5c90e
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585600"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>Comment : ajouter et supprimer des fonctionnalités et des éléments dans un package à l’aide du concepteur de packages
  Lorsque vous créez une solution SharePoint, Visual Studio ajoute les fonctionnalités SharePoint par défaut au package dans la solution. Avant le déploiement final, vous pouvez ajouter et supprimer des fonctionnalités et des éléments de projet SharePoint pour modifier le package SharePoint.

 Vous pouvez également utiliser l’Explorateur de package pour ajouter et supprimer des éléments de projet SharePoint. Vous pouvez également afficher et modifier la hiérarchie des éléments de projet SharePoint et des fonctionnalités qui sont placées dans le package (. wsp). Pour plus d’informations, consultez [Comment : ajouter et supprimer des fonctionnalités et des éléments dans un package à l’aide de l’Explorateur](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)de package.

## <a name="add-features-to-a-sharepoint-package"></a>Ajouter des fonctionnalités à un package SharePoint
 Vous pouvez utiliser le concepteur de packages pour ajouter des fonctionnalités à un package SharePoint.

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>Pour ajouter des fonctionnalités SharePoint avec le concepteur de packages

1. Ouvrez le **Concepteur de packages**.

    Pour plus d’informations, consultez [Comment : personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Ajoutez une ou plusieurs fonctionnalités SharePoint en effectuant une ou plusieurs des étapes suivantes :

   1. Double-cliquez sur chaque élément dans les **éléments de la** liste de solutions que vous souhaitez ajouter.

   2. Choisissez un élément que vous souhaitez ajouter, puis cliquez sur le bouton **Ajouter** (>).

   3. Cliquez sur le bouton **Ajouter tout** (>>) pour ajouter tous les éléments à la fois.

      Par exemple, vous pouvez double-cliquer sur un élément dans les **éléments de la liste solution** pour l’ajouter aux **éléments de la liste des packages** .

      Les éléments et les fonctionnalités de projet SharePoint apparaissent dans les **éléments de la liste des packages** .

## <a name="remove-features-from-a-sharepoint-package"></a>Supprimer des fonctionnalités d’un package SharePoint
 Vous pouvez utiliser le concepteur de packages pour supprimer des fonctionnalités d’un package SharePoint.

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>Pour supprimer des fonctionnalités SharePoint à l’aide du concepteur de packages

1. Dans la liste **éléments dans le package** , choisissez l’élément que vous souhaitez supprimer, puis choisissez le bouton **supprimer** (<), ou cliquez sur le bouton **Supprimer tout** (<<) pour supprimer tous les éléments.

     Les éléments SharePoint apparaissent dans les **éléments de la liste de solutions** .

## <a name="see-also"></a>Voir aussi
- [Créer des packages de solution SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Comment : personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Comment : créer un package](/previous-versions/ee231585(v=vs.110))