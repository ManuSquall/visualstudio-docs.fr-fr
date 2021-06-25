---
title: Automatisation pour la configuration et les objets SelectedItem | Microsoft Docs
description: Découvrez comment automatiser les processus de génération et d’élément sélectionné de Visual Studio à l’aide des objets Configuration et SelectedItem dans l’interopérabilité de l’interpréteur de commandes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1a95fc06c5d84a936cdb1ada3369f584381dfe7f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901628"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatisation pour la configuration et les objets SelectedItem

Vous pouvez automatiser les processus de génération et d’élément sélectionné dans Visual Studio.

## <a name="automation-for-builds"></a>Automation pour les builds

La génération ou la configuration dispose d’un modèle Automation qui est fourni quand vous implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Pour plus d’informations, consultez [Présentation des configurations de build](../../ide/understanding-build-configurations.md).

Si vous créez un VSPackage et souhaitez contrôler les options de configuration, vous devez utiliser le modèle Automation.

## <a name="automation-for-selecteditem"></a>Automatisation pour SelectedItem

Vous n’avez pas besoin de fournir une implémentation pour l' `SelectedItem` objet, car Visual Studio contient une implémentation standard. Toutefois, vous pouvez implémenter l' `SelectedItem` objet si vous préférez. Vous devez implémenter un objet qui contient l' `SelectedItem` interface et retourner une réponse à un appel à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> méthode avec la `VSITEMID` valeur [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Contribuer au modèle Automation](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Présentation des configurations de build](../../ide/understanding-build-configurations.md)
